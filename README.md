# 모이라 (Moira)

모임의 일정 조율, 콘텐츠 투표, 정산을 한곳에서 처리하는 서비스입니다.

---

## 📌 프로젝트 소개

모임을 하려면 날짜를 맞추고 무엇을 할지 정해야 하고, 끝난 뒤에는 쓴 돈을 다시 나눠야 합니다. 모이라에서는 이 과정을 모임 하나 안에서 끝낼 수 있습니다.

- 일정 조율: 일정 후보마다 선호도를 받아 정합니다
- 콘텐츠 투표: 모임원이 함께 무엇을 할지 고릅니다
- 정산: 지출마다 참여한 사람끼리 나눠 한 번에 정산합니다
- 초대 링크로 모임에 참여합니다
- 투표가 끝나거나 정산이 완료되면 알림을 보냅니다

---
## 👥 팀 구성

| 담당 | GitHub |
| --- | --- |
| 모임·초대 | [sowon11](https://github.com/sowon11) |
| 회원·인증 | [jinni1](https://github.com/jinni1) |
| 일정 투표 | [jihoo414-tech](https://github.com/jihoo414-tech) |
| 콘텐츠 투표·알림 | [jjjonghyeon](https://github.com/jjjonghyeon) |
| 비용·정산 | [minj00-kim](https://github.com/minj00-kim) |

---
## 🛠 Tech Stack

### Backend

| | Technology |
| --- | --- |
| Language | Java 25 |
| Framework | Spring Boot 4.1.1 |
| ORM | Spring Data JPA |
| Security | Spring Security, JWT (JJWT 0.13.0) |
| Database | MySQL |
| DB Migration | Flyway |
| API Docs | SpringDoc OpenAPI / Swagger |
| Build | Gradle |

### Frontend

| | Technology |
| --- | --- |
| Framework | Next.js 16 |
| UI | React 19 |
| Language | TypeScript |
| Styling | Tailwind CSS 4 |
| Deployment | Vercel |

### Infra & Collaboration

| | Technology |
| --- | --- |
| Backend Deployment | Railway |
| Database | MySQL |
| Local DB | Docker Compose |

---
## Getting Started
### Backend
#### 1. 환경변수 설정

`backend/.env.example`을 복사해 `backend/.env`를 만듭니다.

```bash
cd backend
cp .env.example .env
```

`.env`에서 MySQL 접속 정보와 `JWT_ACCESS_SECRET`, `JWT_REFRESH_SECRET`을 설정합니다. 두 JWT 시크릿은 서로 다른 랜덤 값으로, 각각 UTF-8 기준 최소 32바이트로 설정합니다.

```env
SPRING_PROFILES_ACTIVE=local
MYSQLHOST=localhost
MYSQLPORT=3306
MYSQLDATABASE=team02
MYSQLUSER=team02_user
MYSQLPASSWORD=your_password
MYSQL_ROOT_PASSWORD=your_root_password
JWT_ACCESS_SECRET=your_jwt_access_secret
JWT_REFRESH_SECRET=your_jwt_refresh_secret
```

#### 2. 실행 프로필 설정
프로필을 지정하지 않으면 기본으로 `local` 프로필이 적용됩니다. 운영 환경에서는 배포 환경변수에 `SPRING_PROFILES_ACTIVE=prod`를 추가합니다.

```env
SPRING_PROFILES_ACTIVE=prod
```

#### 3. DB 스키마 관리 (Flyway)
DB 테이블은 처음 실행할 때 Flyway가 빈 DB에 자동으로 생성합니다. 스키마를 변경할 때는 `backend/src/main/resources/db/migration`에 새 버전의 SQL 파일을 추가합니다. 

#### 4. MySQL 실행

```bash
docker compose up -d
```

#### 5. 애플리케이션 실행

```bash
./gradlew bootRun
```

서버 실행 후 API 문서는 [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)에서 확인할 수 있습니다.



### Frontend

#### 1. 의존성 설치

```bash
cd frontend
npm install
```

#### 2. 환경변수 설정

로컬 프론트 환경변수는 `frontend/.env.local`에 둡니다. 

```env
# frontend/.env.local
BACKEND_URL=http://localhost:8080
```

#### 3. 개발 서버 실행

```bash
npm run dev
```

브라우저에서 [http://localhost:3000](http://localhost:3000)을 엽니다.


---
