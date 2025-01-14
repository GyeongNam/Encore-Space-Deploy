
# Encore Space


<p align="center">
  <img src="/docs/img/README.png"/>
<br>
한화시스템 BEYOND SW캠프 교육생들의 커뮤니티
</p>


## 목차

🛸 [프로젝트 개요](#-프로젝트-개요)  
👾 [팀원 소개](#-팀원-소개)  
📟 [협업 방법](#-협업-방법)  
📄 [개발 문서](#-개발-문서)  
⚙️ [기술 스택](#-기술-스택)  
📢 [주요 서비스](#-주요-서비스)
* ✅ [회원가입 및 로그인 서비스](#-회원가입-및-로그인-서비스)
* ✅ [게시판 서비스](#-게시판-서비스)

🌏 [CI/CD](#-cicd)  
🌐 [Service Test](#-service-test)



<br>

# 🛸 프로젝트 개요

1. 소개
* 교육생들 소통하는 창구를 만들어 공부 내용을 적어 관리할 뿐 아니라 수료생들끼리 수업 내용과 다른 유용한 정보들을 한 곳에 모아 보다 효과적으로 공유할 수 있는 서비스입니다.
* 기수, 프로젝트마다 그룹을 생성하고 내용을 공유할 수 있는 게시판 기능과 원할한 소통을 위한 메세지 기능이 있습니다.

#### GitHub Link

* [Back-End](https://github.com/GyeongNam/Encore-Space-Back)
* [Front-End](https://github.com/GyeongNam/Encore-Space-Front)
* [CI/CD](https://github.com/GyeongNam/Encore-Space-Deploy)

<br>

# 👾 팀원 소개

<div align="center">

|                                                                         박세종                                                                          | 신재석 | 조경남 | 한희준 |
|:----------------------------------------------------------------------------------------------------------------------------------------------------:|:----------:|:-----------------------:|:----------:|
| <img src="https://avatars.githubusercontent.com/u/123573918?v=4" height="150" width="150"> <br> [@lifedesigner88](https://github.com/lifedesigner88) | <img src="https://avatars.githubusercontent.com/u/27791880?v=4" height="150" width="150"> <br>[@MrKeeplearning](https://github.com/MrKeeplearning)| <img src="https://avatars.githubusercontent.com/u/63902992?v=4" height="150" width="150"> <br> [@GyeongNam](https://github.com/GyeongNam) | <img src="https://avatars.githubusercontent.com/u/139551676?v=4" height="150" width="150"> <br> [@lemony1122](https://github.com/lemony1122) |

</div>



<br>

# 📟 협업 방법

**이 프로젝트는 Jira와 GitHub Flow를 사용하여 협업했습니다.**

### Jira
- Jira를 사용하여 작업을 관리합니다.
- 작업은 **Backlog**에서 **To Do** → **In Progress** → **Code Review** → **Done**으로 진행됩니다.


<details>
  <summary> Jira 타임라인</summary>
  <div>
    <img src="/docs/jira1.png" alt="jira1" />
  </div>
</details>

### Branch rule (GitHub Flow)
- `main` 브랜치는 항상 배포 가능한 상태여야 합니다.
- 작업은 `main`에서 새로운 브랜치를 생성하여 진행합니다.
- 작업이 완료되면 Pull Request(PR)을 생성하여 코드 리뷰 후 `main`에 병합합니다.
- `main`에 병합된 후 배포가 자동으로 이루어집니다.
- 커밋 규칙

  | **타입**     | **설명**                                     |
  |-------------|--------------------------------------------|
  | `feat`      | 새로운 기능 추가                             |
  | `fix`       | 버그 수정                                   |
  | `docs`      | 문서 수정                                   |
  | `style`     | 코드 스타일 변경(포맷, 세미콜론 추가 등)     |
  | `refactor`  | 코드 리팩토링                               |
  | `test`      | 테스트 추가 또는 수정                       |
  | `chore`     | 그 외 잡다한 작업 (빌드, 설정 파일 수정 등) |

<br>

# 📄 개발 문서


<details>
  <summary>요구사항명세서</summary>
  <div>
    <img src="/docs/요구사항명세서.png" alt="요구사항명세서" />
  </div>
</details>

<details>
  <summary>ERD</summary>
  <div>
    <img src="/docs/ERD.png" alt="ERD" />
  </div>
</details>

<details>
  <summary>Swagger</summary>
  <div>
    <img src="/docs/swagger/img_5.png" alt="Swagger" />
    <img src="/docs/swagger/img_6.png" alt="Swagger" />
    <img src="/docs/swagger/img_7.png" alt="Swagger" />
    <img src="/docs/swagger/img_8.png" alt="Swagger" />
    <img src="/docs/swagger/img_9.png" alt="Swagger" />
    <img src="/docs/swagger/img_10.png" alt="Swagger" />
  </div>
</details>


<br>

# ⚙️ 기술 스택


### Back-End

![Java 17](https://img.shields.io/badge/Java_17-007396?style=for-the-badge&logo=java&logoColor=white)
![spring boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white)

### Front-End
![HTML](https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)
![Quasar](https://img.shields.io/badge/Quasar-1976D2?style=for-the-badge&logo=quasar&logoColor=white)

### DB
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)

### Infra
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)<br>
<img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white" alt="AWS">
<img src="https://img.shields.io/badge/AWS_EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white" alt="AWS EC2">
<img src="https://img.shields.io/badge/AWS_S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white" alt="AWS S3">
<img src="https://img.shields.io/badge/AWS_RDS-527FFF?style=for-the-badge&logo=amazonrds&logoColor=white" alt="AWS RDS">
<img src="https://img.shields.io/badge/AWS_CloudFront-FF8C00?style=for-the-badge&logo=amazoncloudwatch&logoColor=white" alt="AWS CloudFront">
<img src="https://img.shields.io/badge/AWS_IAM-FF9900?style=for-the-badge&logo=amazoniam&logoColor=white" alt="AWS IAM">
<img src="https://img.shields.io/badge/AWS_Route_53-006FBB?style=for-the-badge&logo=amazonroute53&logoColor=white" alt="AWS Route 53">

###  CI/CD
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

### Tools
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ_IDEA-000000?style=for-the-badge&logo=intellij-idea&logoColor=white)
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-007ACC.svg?&style=for-the-badge&logo=Visual%20Studio%20Code&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-6DB33F?style=for-the-badge&logo=swagger&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Jira](https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white)

<br>

# 📢 주요 서비스

## ✅ 회원가입 및 로그인 서비스


<p align="center">
  <img src="/docs/img/loginFlow.png"/>
</p>

<br/>

---

<br/>

### 기반 기술 설명

#### JWT

- JSON 웹 토큰(JSON Web Token, JWT, "jot”)은 선택적 서명 및 선택적 암호화를 사용하여 데이터를 만들기 위한 인터넷 표준으로, 페이로드는 몇몇 클레임(claim) 표명(assert)을 처리하는 JSON을 보관하고 있다. 토큰은 비공개 시크릿 키 또는 공개/비공개 키를 사용하여 서명된다

<p align="center">
  <img src="/docs/img/jwt.png"/>
</p>

#### Oauth2

- 어플리케이션이 리소스 소유자에게 리소스에 대한 접근 권한을 허용하고, 요청 결과로 전달받은 토큰을 이용해 애플리케이션이 해당 리소스에 접근하는 프로토콜

#### Redis

- 레디스는 Remote Dictionary Server의 약자로서, "키-값" 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터베이스 관리 시스템으로 인메모리를 사용한다.

#### SMTP

- Simple Mail Transfer Protocol의 약자로, 이메일 전송에 사용되는 네트워크 프로토콜

#### Spring Security

- Spring 기반의 애플리케이션의 보안(인증과 권한, 인가 등)을 담당하는 스프링 하위 프레임워크이다. Spring Security는 '인증'과 '권한'에 대한 부분을 Filter 흐름에 따라 처리하고 있다

<p align="center">
  <img src="/docs/img/SpringSecurity.png"/>
</p>

---

### Session vs JWT

웹 애플리케이션에서 사용자를 인증하고 권한을 부여하는 방법에는 크게 **Session 기반 인증**과 **JWT(JSON Web Token) 기반 인증**이 있습니다.

- **Session 기반 인증**
  - 서버에서 세션 데이터를 관리하며, 클라이언트는 세션 ID를 쿠키로 보관.
  - 서버가 상태를 유지해야 하므로 부하가 클 수 있음.
  - 주로 전통적인 웹 애플리케이션에서 사용.


- **JWT 기반 인증**
  - 클라이언트가 JWT를 보관하고 요청마다 토큰을 서버로 전송.
  - 서버는 상태를 유지하지 않아도 되므로 확장성이 높음.
  - RESTful API나 SPA(Single Page Application)에서 주로 사용.


- 데이터 요청 상황에 따른 로그인 방식 비교

<div style="align: center; font-size: 10px;">

| 데이터 요청 상황        | 로그인 방식                                    | 서버 부하       | 네트워크 부하  | 보안         | 성능     |
|------------------|-----------------------------------------------|----------------|---------------|-------------|---------|
| **데이터 요청이 많을 때** | **세션 기반 인증**                             | 매우 높음       | 높음          | 높음        | 중간    |
|                  | **엑세스 토큰만 사용**                         | 중간~높음       | 중간          | 중간        | 우수    |
|                  | **엑세스 토큰 + 리프레시 토큰**                | 높음            | 중간~높음     | 우수        | 중간    |
|                  | **엑세스 토큰 + 리프레시 토큰(서버 저장)**     | 중간~높음       | 중간~높음     | 우수        | 중간    |
|                  | **엑세스 토큰 + 리프레시 토큰(IP 기반 서버 저장)** | 중간~높음       | 중간~높음     | 최우수      | 중간    |
| **데이터 요청이 적을 때** | **세션 기반 인증**                             | 중간~높음       | 높음          | 높음        | 중간    |
|                  | **엑세스 토큰만 사용**                         | 낮음~중간       | 중간          | 중간        | 우수    |
|                  | **엑세스 토큰 + 리프레시 토큰**                | 중간            | 중간~높음     | 우수        | 중간    |
|                  | **엑세스 토큰 + 리프레시 토큰(서버 저장)**     | 낮음~중간       | 중간~높음     | 우수        | 중간    |
|                  | **엑세스 토큰 + 리프레시 토큰(IP 기반 서버 저장)** | 낮음~중간       | 중간~높음     | 최우수      | 중간    |

</div>

 **로그인 기능에서 가장 중요한 부분은 보안이라고 생각되었고 엑세스 토큰 + 리프레시 토큰(IP 기반 서버 저장)를 선택하게 되었습니다.**

<br>


## ✅ 게시판 서비스


### 게시글 작성

<p align="center">
    <img src="/docs/img/포스팅.png"/>
</p>


- 회원이고 로그인 된 상태인 사용자만 게시글 작성 가능
- 회원이고 로그인 된 상태인 사용자만 게시글 작성 가능
- 어떤 공간(개인스페이스, 팀 스페이스 등)에 작성하는지에 따라 작성 권한 제한
- 다중 이미지 파일 업로드 가능(게시글 이미지 삽입)
- 글을 공개가 기본값으로 작성, 비공개 선택 가능

---

### 게시글 수정

- 작성자 외에는 게시글 수정 불가능
- 제목, 본문 수정 가능
- 첨부파일 추가 가능
- 공개, 비공개 여부 수정 가능

---

### 게시글 삭제

- 작성자 외 관리자(MANAGER, TEACHER)도 삭제 가능
- 실제 DB에서는 삭제 안하고 delYN으로 관리
  - `delYN=”Y”`인 게시글은 서버에 안 보냄
- 게시글이 `delYN=”Y”` 인 경우 게시글에 달린 모든 댓글, 대댓글의 `delYN=”Y”`으로 변경, 관련 게시글 좋아요 정보 삭제

---

### 게시글 상세 조회

<p align="center">
    <img src="/docs/img/포스팅완료.png"/>
</p>

- 게시글 제목, 본문 외에 등록시간, 수정 시간, 공개 상태, 게시글 좋아요 수, 게시글에 달린 댓글과 대댓글, 댓글에 관련된 좋아요 수 정보 조회 가능
- 댓글의 경우 수정 가능하며 이 또한 작성자만 수정 가능
- 삭제된 댓글은 “삭제된 댓글입니다” 표시, 대댓글에는 영향 주지 않음
- 삭제된 댓글 또한 delYN으로 관리되어 실제 DB에서는 삭제되지 않음

---

### 게시글 목록 조회

<p align="center">
    <img src="/docs/img/게시글목록조회.png"/>
</p>

- 썸네일이 있는 경우 썸네일 사진으로, 아니면 기본값으로 썸네일 게시
- 썸네일과 제목으로 게시

---

### 파일 관리

- 파일 저장 : UUID를 이용해 파일명 중복 가능성 제거
- 파일 다운로드

---

### 좋아요 기능

<p align="center">
    <img src="/docs/img/하트.png"/>
</p>

- 게시글, 댓글, 대댓글에 좋아요 추가, 취소 가능
- 중복 좋아요 불가능


<br>

# 🌏 CI/CD

### 백엔드 배포 (Docker + EC2 + Redis + MariaDB 등)

<div style="align: center; font-size: 10px;">

| 단계 | 설명 |
| --- | --- |
| 1. **레포지토리 체크아웃** | `actions/checkout@v2`를 사용하여 GitHub 레포지토리에서 최신 `main` 브랜치 코드를 체크아웃. |
| 2. **Docker Hub 로그인** | `docker/login-action@v1`을 사용하여 Docker Hub에 로그인. |
| 3. **Docker 이미지 빌드 및 푸시** | `docker/build-push-action@v2`을 사용하여 Docker 이미지를 빌드하고, Docker Hub에 업로드. |
| 4. **EC2에 Redis 설치 및 실행** | 첫 번째 EC2 인스턴스에 Redis가 없다면, 설치 후 실행. Docker로 Redis 컨테이너를 생성. |
| 5. **EC2에 Docker 로그인 및 애플리케이션 실행** | 두 번째 EC2에 Docker 로그인 후, Docker Hub에서 이미지를 풀하고 컨테이너를 실행. 환경 변수 설정 (DB, S3, OAuth 등). |
| 6. **추가 EC2에 Redis 설치 및 실행** | 두 번째 EC2 인스턴스에 Redis를 설치하고 실행. |
| 7. **EC2에 Docker 로그인 및 애플리케이션 실행** | 두 번째 EC2에서 Docker 이미지를 풀어 애플리케이션을 실행. 동일한 환경 변수 설정. |

</div>

### 프론트엔드 배포 (AWS S3 + CloudFront)

<div style="align: center; font-size: 10px;">

| 단계 | 설명 |
| --- | --- |
| 1. **레포지토리 체크아웃** | `actions/checkout@v2`을 사용하여 GitHub 레포지토리에서 최신 `main` 브랜치 코드를 체크아웃. |
| 2. **Node.js 설정** | `actions/setup-node@v2`을 사용하여 Node.js 버전 `20`을 설정. |
| 3. **npm 의존성 설치** | `npm install`을 사용하여 `./Space_Frontend` 디렉토리 내의 의존성을 설치. |
| 4. **프론트엔드 빌드** | `npm run build`를 실행하여 `./Space_Frontend`의 빌드 파일을 생성. |
| 5. **AWS CLI 설정** | `aws-actions/configure-aws-credentials@v2`을 사용하여 AWS S3에 접근할 수 있도록 인증. |
| 6. **S3로 배포** | `aws s3 sync ./Space_Frontend/dist/spa s3://spaceencore.shop` 명령어로 S3에 빌드 파일을 동기화하여 배포. |

</div>


### 배포 프로세스
<p align="center">
    <img src="/docs/cicd.png"/>
</p>

<br>


# 🌐 Service Test


![img_1.png](/docs/ServiceTest/img/img_1.png)

## 로그인 테스트
![img_2.png](/docs/ServiceTest/img/img_2.png)

## 로그인이 완료 후 MYPAGE 확인

![img_4.png](/docs/ServiceTest/img/img_4.png)
![img_5.png](/docs/ServiceTest/img/img_5.png)



## 글 작성을 위한 POSTING 이동
#### 글을 작성하기위해서는 스페이스를 생성해야 합니다.


![img_7.png](/docs/ServiceTest/img/img_7.png)



## 게시글을 작성하기 위한 스페이스 생성(MY SPACE 로 이동)
#### GO TO CEREATE 클릭

![img_6.png](/docs/ServiceTest/img/img_6.png)


## 개인스페이스이므로 본인을 선택하고 생성
![img_13.png](/docs/ServiceTest/img/img_13.png)


## 개인 스페이스 입력하고 제출
![img_14.png](/docs/ServiceTest/img/img_14.png)


## MY 스페이스로 이동하여 생성된 스페이스 확인
#### 스페이스를 클릭하면 참여중인 맴버 조회 가능.
![img_16.png](/docs/ServiceTest/img/img_16.png)




## 팀 스페이스로 생성을 위해 TEAM 스페이스로 이동
#### 함께하고 싶은 팀원을 클릭하고 팀 생성
![img_17.png](/docs/ServiceTest/img/img_17.png)



## 팀스페이스를 입력하고 생성
![img_18.png](/docs/ServiceTest/img/img_18.png)

## 팀 스페이스 이동 후 스페이스 조회
#### 팀 생성자는 CAPTAIN , 초대된 사람은 CREW 로 ROLE 이 생김
![img_19.png](/docs/ServiceTest/img/img_19.png)


## 같은 방식으로 그룹 스페이스 생성
![img_20.png](/docs/ServiceTest/img/img_20.png)


## 포스팅으로 이동시 생성한 스페이스가 조회됨
![img_21.png](/docs/ServiceTest/img/img_21.png)

## 작성할 스페이스를 클릭 후 텍스트로만 글 작성 (이미지 첨부시 작성이 안됨)
![img_22.png](/docs/ServiceTest/img/img_22.png)

## 메인 페이지로 리다이렉팅 되고 아래로 내려보면 글이 있음
![img_23.png](/docs/ServiceTest/img/img_23.png)

## 게시글 클릭하면 게시글 상세보기 나옴
![img_24.png](/docs/ServiceTest/img/img_24.png)


## 게시글에 댓글 작성가능
![img_25.png](/docs/ServiceTest/img/img_25.png)


## LIKE(좋아요)를 누르면 우측상단 HEART가 1 증가함 (1번만 가능)
![img_26.png](/docs/ServiceTest/img/img_26.png)


## CANCLE(싫어요)를 누르면 우측 상단의 HEART가 0이됨
#### 댓글에 댓글, LIKE, CANCLE 은 작동하지 않음.
![img_27.png](/docs/ServiceTest/img/img_27.png)


### 댓글은 여러개 작성 가능
![img_28.png](/docs/ServiceTest/img/img_28.png)


## 마이 스페이스로가서 스페이스 클릭하면 작성한 글 조회 가능
![img_29.png](/docs/ServiceTest/img/img_29.png)


## MESSAGES 메뉴로 이동
![img_31.png](/docs/ServiceTest/img/img_31.png)


## 가운데쯤 메시지 모양의 버튼 클릭하면 채팅방 생성됨.
![img_33.png](/docs/ServiceTest/img/img_33.png)


## (F5) 새로고침을 누르면 채팅방이 보입니다.
![img_34.png](/docs/ServiceTest/img/img_34.png)


## 메시지 발송은 배포후 웹소켓 문제로 작동하지 않음
![img_35.png](/docs/ServiceTest/img/img_35.png)

### 마지막으로 로그아웃하고 종료
![img.png](/docs/ServiceTest/img/img_36.png)

