# Encore Space 배포

## 1. 최초 계획

### 블루/그린 배포

<p align="center">
    <img src="/Document/img/bluegreen.png"/>
</p>

### 블루 그린 배포를 선택한 이유

- Blue: 구버전, Green: 신버전
- 운영 환경에서 구버전과 동일하게 신버전의 인스턴스를 구성한 후, 로드밸런서를 통해 신버전으로 모든 트래픽을 전환하는 배포 방식.
- 구버전과 동일한 운영 환경으로 신버전의 인스턴스를 구성하기 때문에 실제 서비스 환경에서 신버전을 미리 테스트할 수 있는 장점
- 블루 그린 배포를 선택한 이유
  - 새로운 버전의 서비스를 배포하고 이를 프로덕션으로 전환하는 동안 서비스 중단 시간이 없다는 주요 장점이 있어 채팅과 같이 계속적인 가용성이 중요한 서비스에 대해 매우 유용함.
  - 또한, 신규 서비스에 문제가 발생하면 곧바로 이전 버전의 환경으로 전환할 수 있다는 장점이 있다.

### 전체 아키텍처 구성 설명

<p align="center">
  <img src="/Document/img/img.png"/>
</p>

### Frontend 동작 방식

- S3와 Cloudfront를 사용
- AWS 콘솔에서 S3업로드, 엣지 로케이션의 캐시 무효화, 요청에 대한 리다이렉션 처리 등의 작업을 간편하게 진행할 수 있는 장점이 있어 사용함.
- 사용자가 encorespace.shop으로 요청을 보내면 ACM에서 인증서를 검증한다.
- Route53에서 www인지, server인지 검증
- www인 경우 cloudfront로 라우팅해서 S3의 데이터에 접근하고 사용자에게 화면을 보여주게 된다.
- 반면, server인 경우 로드밸런서로 요청을 보내고 요청에 따른 적절한 반환값을 받게 된다.

### Frontend 배포 방식

```yaml
name: Deploy to AWS S3

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    # git action에서 우분투 최신 버전으로 설치
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: setup node.js
        uses: actions/setup-node@v2
        with:
          node-version: '20'

      - name: npm install
        working-directory: ./Space_Frontend
        run: npm install

      - name: npm build
        working-directory: ./Space_Frontend
        run: npm run build

      # github action 내에서 aws cli 설치
      - name: setup aws cli
        uses: aws-actions/configure-aws-credentials@v2
        # S3FullAccess에 대한 권한이 있는 IAM 사용자 로그인
        with:
          aws-access-key-id: ${{ secrets.AWS_S3_ACCESS_KEY }}
          aws-secret-access-key: ${{ secrets.AWS_S3_SECRET_KEY }}
          aws-region: "ap-northeast-2"

      # 빌드된 파일을 S3로 배포
      - name: deploy to s3
        run: |
      # Quasar 이기 때문에 dist 밑에 spa 폴더로 이동
      # copy는 delete 없이 덮어쓰기만 하지만 sync를 사용해서 변경이 있는 부분만 수정하게 됨.
          aws s3 sync ./Space_Frontend/dist/spa s3://spaceencore.shop
```

### Backend 방식

<p align="center">
    <img src="/Document/img/ecr.png"/>
</p>

Github Action, ECR, S3, CodeDeploy를 활용한 블루/그린 배포 방식

1. Github에 코드를 push하면 Github Action 동작
2. ECR에 Docker 이미지를 푸쉬
3. S3에 CodeDeploy 스크립트를 업로드
4. CodeDeploy를 실행해서 EC2에 배포하는 방식

- ECR에는 Spring Boot docker image를 push
- S3에는 CodeDeploy에 필요한 스크립트를 압축해 업로드
- CodeDeploy에서는 S3의 스크립트를 실행해 EC2 배포를 진행
- 스크립트에는 ECR로부터 docker image를 pull 받고 컨테이너를 실행하는 명령이 들어있음

<br/>

---

<br/>

# 2. 현재 상태

<p align="center">
    <img src="/Document/img/current_architecture.png"/>
</p>

### Dockerfile

```dockerfile
FROM openjdk:17-jdk-slim as builder
WORKDIR app
COPY gradlew .
COPY gradle gradle
COPY build.gradle .
COPY settings.gradle .
COPY src src

# Build
RUN chmod +x ./gradlew
RUN ./gradlew bootJar

# Stage 2: Running the Application
FROM openjdk:17-jdk-slim
WORKDIR app

COPY --from=builder /app/build/libs/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
```

### Github workflow

```yaml
name: CI/CD

on:
  push:
    branches:
      - main  # or any other branch name

env:
  IMAGE_NAME: space_backend

jobs:
  build-and-push-image:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

# GitAction에서 DockerHub로 로그인
      - name: Log in to Docker Hub
        uses: docker/login-action@v1
        with:
          username: ${{ secrets.DOCKER_HUB_USERNAME }}
          password: ${{ secrets.DOCKER_HUB_PASSWORD }}

# Dockerfile을 기반으로 이미지를 생성해서 도커 허브에 업로드
      - name: Build and push Docker image
        uses: docker/build-push-action@v2
        with:
          context: ./Space_Backend
          push: true
          tags: ${{ secrets.DOCKER_HUB_USERNAME }}/${{ env.IMAGE_NAME }}:latest

# *********************************** EC2 first ***********************************

# 첫번째 EC2 접속해서 script실행(docker, redis 설치)
      - name: pull and run Redis if not exist
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.EC2_HOST1 }}
          username: ${{ secrets.EC2_USERNAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: |
            sudo apt-get update
            sudo apt-get install -y docker.io
            if ! sudo docker ps | grep some-redis; then 
              sudo docker pull redis
              sudo docker network create my-network
              sudo docker run --name some-redis --network my-network -p 6379:6379 -d redis
            fi

# EC2 로그인 및 도커 로그인
      - name: ec2 ssh login and docker run
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.EC2_HOST1 }}
          username: ${{ secrets.EC2_USERNAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: |
            if ! type docker > /dev/null ; then
              curl -s https://get.docker.com -o get-docker.sh
              sudo sh get-docker.sh
            fi
            sudo docker login --username ${{ secrets.DOCKER_HUB_USERNAME }} --password ${{ secrets.DOCKER_HUB_PASSWORD }}
            sudo docker pull ${{ secrets.DOCKER_HUB_USERNAME }}/${{ env.IMAGE_NAME }}:latest
            sudo docker rm -f ${{ env.IMAGE_NAME }} || true
            sudo docker image prune -f

# 도커를 실행하는 시점에서 DB정보, 이메일 인증, 구글과 깃헙 OAuth, 이미지용 S3 저장소에 키를 설정
            sudo docker run -d --name ${{ env.IMAGE_NAME }} --network my-network -p 8080:8080 \
            -e SPRING_DATASOURCE_URL=jdbc:mariadb://${{ secrets.DB_HOST }}:3306/encorespace \
            -e SPRING_DATASOURCE_USERNAME=${{ secrets.DB_USERNAME }} \
            -e SPRING_DATASOURCE_PASSWORD=${{ secrets.DB_PASSWORD }} \
            -e SPRING_MAIL_PASSWORD=${{ secrets.MAIL_KEY }} \
            -e SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_GOOGLE_CLIENT_SECRET=${{ secrets.GOOGLE_KEY }} \
            -e SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_GITHUB_CLIENT_SECRET=${{ secrets.OAUTH_GITHUB_KEY }} \
            -e CLOUD_AWS_CREDENTIALS_ACCESS_KEY=${{ secrets.AWS_S3_ACCESS_KEY }} \
            -e CLOUD_AWS_CREDENTIALS_SECRET_KEY=${{ secrets.AWS_S3_SECRET_KEY }} ${{ secrets.DOCKER_HUB_USERNAME }}/${{ env.IMAGE_NAME }}:latest
            

# *********************************** EC2 second ***********************************


      - name: pull and run Redis if not exist
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.EC2_HOST2 }}
          username: ${{ secrets.EC2_USERNAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: |
            sudo apt-get update
            sudo apt-get install -y docker.io
            if ! sudo docker ps | grep some-redis; then 
              sudo docker pull redis
              sudo docker network create my-network
              sudo docker run --name some-redis --network my-network -p 6379:6379 -d redis
            fi

      - name: ec2 ssh login and docker run
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.EC2_HOST2 }}
          username: ${{ secrets.EC2_USERNAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: |
            if ! type docker > /dev/null ; then
              curl -s https://get.docker.com -o get-docker.sh
              sudo sh get-docker.sh
            fi
            sudo docker login --username ${{ secrets.DOCKER_HUB_USER NAME }} --password ${{ secrets.DOCKER_HUB_PASSWORD }}
            sudo docker pull ${{secrets.DOCKER_HUB_USERNAME }}/${{ env.IMAGE_NAME }}:latest
            sudo docker rm -f ${{ env.IMAGE_NAME }} || true
            sudo docker image prune -f

            sudo docker run -d --name ${{ env.IMAGE_NAME }} --network my-network -p 8080:8080 \
            -e SPRING_DATASOURCE_URL=jdbc:mariadb://${{ secrets.DB_HOST }}:3306/encorespace \
            -e SPRING_DATASOURCE_USERNAME=${{ secrets.DB_USERNAME }} \
            -e SPRING_DATASOURCE_PASSWORD=${{ secrets.DB_PASSWORD }} \
            -e SPRING_MAIL_PASSWORD=${{ secrets.MAIL_KEY }} \
            -e SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_GOOGLE_CLIENT_SECRET=${{ secrets.GOOGLE_KEY }} \
            -e SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_GITHUB_CLIENT_SECRET=${{ secrets.OAUTH_GITHUB_KEY }} \
            -e CLOUD_AWS_CREDENTIALS_ACCESS_KEY=${{ secrets.AWS_S3_ACCESS_KEY }} \
            -e CLOUD_AWS_CREDENTIALS_SECRET_KEY=${{ secrets.AWS_S3_SECRET_KEY }} ${{ secrets.DOCKER_HUB_USERNAME }}/${{ env.IMAGE_NAME }}:latest
```

<br/>

---

<br/>

## 3. 시연 링크

[spaceencore.shop](spaceencore.shop)
