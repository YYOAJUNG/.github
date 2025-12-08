# BudgetOps

<div align="center">

**멀티 클라우드 비용 최적화 플랫폼**

학생 개발자를 위한 AI 기반 클라우드 비용 관리 및 최적화 솔루션

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Backend](https://img.shields.io/badge/backend-Spring%20Boot%203.2-green.svg)](budgetops-be/)
[![Frontend](https://img.shields.io/badge/frontend-Next.js%2014-black.svg)](budgetops-fe/)
[![AI](https://img.shields.io/badge/AI-Claude%20%26%20Gemini-purple.svg)](budgetops-ai/)


</div>

---

## 목차

- [소개](#-소개)
- [주요 기능](#-주요-기능)
- [프로젝트 구조](#-프로젝트-구조)
- [기술 스택](#-기술-스택)
- [빠른 시작](#-빠른-시작)
- [아키텍처](#-아키텍처)
- [문서](#-문서)
- [기여](#-기여)
- [라이센스](#-라이센스)

---

## 소개

**BudgetOps**는 AWS, GCP, Azure, NCP 등 여러 클라우드 서비스 제공업체(CSP)의 리소스를 통합 관리하고, **AI 기반 비용 분석 및 최적화 추천**을 제공하여 클라우드 사용 비용을 효과적으로 절감하는 플랫폼입니다.

### 타겟 사용자
- 제한된 예산으로 클라우드를 활용하는 학생 개발자
- 여러 클라우드 플랫폼을 동시에 사용하는 개발 팀
- 클라우드 비용 최적화가 필요한 스타트업

### 핵심 가치
- **통합 관리**: 여러 클라우드 플랫폼을 하나의 대시보드에서 관리
- **AI 추천**: 실제 사용 패턴을 분석하여 최적의 비용 절감 방안 제시
- **자동화**: 비업무 시간 자동 중지, 라이프사이클 관리 등 자동화 기능
- **직관적 UI**: 복잡한 클라우드 관리를 쉽고 간편하게

---

## 주요 기능

### 1. 멀티 클라우드 통합 관리
- **지원 플랫폼**: AWS, GCP, Azure, NCP
- **리소스 관리**: EC2, Compute Engine, Virtual Machine, Server 통합 조회
- **실시간 모니터링**: CPU, 메모리, 네트워크 메트릭 시각화
- **생명주기 관리**: 인스턴스 시작/중지/재시작/삭제

### 2. 비용 분석 및 시각화
- **실시간 비용 추적**: CSP별, 서비스별, 기간별 비용 분석
- **대시보드**: 직관적인 차트와 그래프로 비용 현황 파악
- **프리티어 모니터링**: 무료 한도 사용률 추적
- **예산 관리**: 월별 예산 설정 및 알림

### 3. AI 기반 비용 최적화 (UCAS)
**Universal Cost Action Simulator**를 통한 4가지 최적화 액션:

#### 비업무 시간 자동 중지
- 평일/주말 스케줄 설정
- 유휴 시간 비용 절감
- 연간 최대 40-60% 절감

#### 장기 약정 할인
- Reserved Instance 시뮬레이션
- Savings Plan 분석
- 1년/3년 약정 비교

#### 스토리지 라이프사이클
- 저빈도 데이터 식별
- Cold Storage 전환
- 50-68% 스토리지 비용 절감

#### 인스턴스 다운사이징
- CPU/메모리 사용률 분석
- 적정 인스턴스 타입 추천
- 30-50% 비용 절감 가능

### 4. Top 3 추천 시스템
- 실제 리소스 데이터 기반 분석
- 우선순위별 최적화 액션 추천
- 연간 예상 절감액 계산
- 리스크 점수 및 신뢰도 표시

### 5. AI 어시스턴트
- **Claude API** 기반 비용 최적화 상담
- 자연어 질문/답변
- 컨텍스트 기반 대화
- 실시간 최적화 가이드

### 6. 알림 시스템
- 임계치 기반 알림
- Slack 연동
- 이메일 알림
- 실시간 알림 센터

### 7. 구독 및 결제
- 아임포트(PortOne) 연동
- 토큰 기반 사용량 관리
- 빌링키 자동 결제
- 요금제 관리

### 8. 보안 및 인증
- OAuth 2.0 소셜 로그인 (Google, Kakao, Naver)
- JWT 토큰 기반 인증
- 자격 증명 암호화 저장
- 관리자 권한 관리

---

## 프로젝트 구조

```
budgetops/
├── budgetops-be/          # 백엔드 (Spring Boot)
│   ├── src/
│   │   ├── main/java/com/budgetops/backend/
│   │   │   ├── admin/         # 관리자 기능
│   │   │   ├── ai/            # AI 채팅 (Claude)
│   │   │   ├── aws/           # AWS 통합
│   │   │   ├── azure/         # Azure 통합
│   │   │   ├── billing/       # 구독/결제
│   │   │   ├── budget/        # 예산 관리
│   │   │   ├── costs/         # 비용 분석
│   │   │   ├── gcp/           # GCP 통합
│   │   │   ├── ncp/           # NCP 통합
│   │   │   ├── notification/  # 알림 시스템
│   │   │   ├── oauth/         # OAuth 인증
│   │   │   └── simulator/     # UCAS 시뮬레이터
│   │   └── resources/costs/   # 최적화 규칙 (YAML)
│   ├── docs/                  # 백엔드 문서
│   └── README.md
│
├── budgetops-fe/          # 프론트엔드 (Next.js)
│   ├── app/                   # Next.js 13+ App Router
│   │   ├── dashboard/         # 대시보드
│   │   ├── resources/         # 리소스 관리
│   │   ├── costs/             # 비용 분석
│   │   ├── notifications/     # 알림
│   │   └── mypage/            # 설정
│   ├── components/            # React 컴포넌트
│   ├── lib/api/               # API 클라이언트
│   ├── store/                 # 상태 관리 (Zustand)
│   └── README.md
│
├── PROJECT_SUMMARY.md     # 프로젝트 요약
├── PROJECT_FEATURES.md    # 기능 상세
└── README.md              # 이 파일
```

---

## 기술 스택

### 백엔드
- **Framework**: Spring Boot 3.2.x
- **Language**: Java 17
- **Database**: PostgreSQL (배포), H2 (개발)
- **Build**: Gradle 9.0
- **Testing**: JUnit 5, Mockito, AssertJ
- **Cloud SDKs**: AWS SDK, GCP Java SDK, Azure SDK
- **AI**: Anthropic Claude API
- **Payment**: Stripe API, 아임포트

### 프론트엔드
- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **UI**: TailwindCSS, shadcn/ui
- **State**: Zustand
- **Data Fetching**: TanStack Query
- **Charts**: Recharts
- **AI Chat**: Google Gemini API

### AI 서비스
- **Framework**: FastAPI
- **Language**: Python 3.11+
- **AI**: Claude API, Gemini API

### 인프라
- **Container**: Docker
- **Deployment**: OCI (Oracle Cloud Infrastructure)
- **CI/CD**: GitHub Actions

---

## 빠른 시작

### 사전 요구사항
- **Java 17+** (백엔드)
- **Node.js 18+** (프론트엔드)
- **Python 3.11+** (AI 서비스)
- **Docker** (선택사항)

### 1. 저장소 클론
```bash
git clone https://github.com/your-org/budgetops.git
cd budgetops
```

### 2. 백엔드 실행
```bash
cd budgetops-be

# 로컬 개발 환경
./gradlew bootRun

# 또는 Docker로 실행
docker build -t budgetops-be .
docker run -p 8080:8080 budgetops-be
```

**API 서버**: http://localhost:8080

### 3. 프론트엔드 실행
```bash
cd budgetops-fe

# 의존성 설치
npm install

# 개발 서버 실행
npm run dev

# 또는 프로덕션 빌드
npm run build
npm start
```

**웹 애플리케이션**: http://localhost:3000

### 4. AI 서비스 실행 (선택사항)
```bash
cd budgetops-ai

# 가상환경 생성 및 활성화
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 의존성 설치
pip install -r requirements.txt

# 서버 실행
uvicorn api.main:app --reload
```

**AI API**: http://localhost:8000

### 5. 환경 변수 설정

각 프로젝트의 `.env` 파일을 생성하고 필요한 API 키를 설정하세요:

**budgetops-be/.env**
```env
# Database
SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/budgetops
SPRING_DATASOURCE_USERNAME=postgres
SPRING_DATASOURCE_PASSWORD=your_password

# JWT
JWT_SECRET=your_jwt_secret

# OAuth
OAUTH_GOOGLE_CLIENT_ID=your_google_client_id
OAUTH_GOOGLE_CLIENT_SECRET=your_google_client_secret

# AI
CLAUDE_API_KEY=your_claude_api_key

# Payment
STRIPE_API_KEY=your_stripe_api_key
```

**budgetops-fe/.env.local**
```env
NEXT_PUBLIC_API_URL=http://localhost:8080/api
NEXT_PUBLIC_GEMINI_API_KEY=your_gemini_api_key
```

---

## 아키텍처

### 시스템 아키텍처
```
┌─────────────┐
│   사용자     │
└──────┬──────┘
       │
       ▼
┌─────────────────────────────────────────┐
│         프론트엔드 (Next.js)             │
│  ┌──────────┬──────────┬─────────────┐ │
│  │ Dashboard │ Resources │ Costs       │ │
│  └──────────┴──────────┴─────────────┘ │
└─────────────┬───────────────────────────┘
              │ REST API
              ▼
┌─────────────────────────────────────────┐
│         백엔드 (Spring Boot)             │
│  ┌──────────┬──────────┬─────────────┐ │
│  │ AWS      │ GCP      │ Azure       │ │
│  │ Service  │ Service  │ Service     │ │
│  └──────────┴──────────┴─────────────┘ │
│  ┌──────────┬──────────┬─────────────┐ │
│  │ Simulator│ AI Chat  │ Billing     │ │
│  └──────────┴──────────┴─────────────┘ │
└─────────────┬───────────────────────────┘
              │
    ┌─────────┴─────────┐
    │                   │
    ▼                   ▼
┌───────────┐    ┌─────────────┐
│   Cloud   │    │  AI Service │
│   APIs    │    │  (Claude)   │
└───────────┘    └─────────────┘
```

### 데이터 흐름
1. **사용자 인증**: OAuth 2.0 → JWT 토큰 발급
2. **클라우드 연동**: 자격 증명 암호화 저장 → Cloud SDK 호출
3. **비용 수집**: Cost API → 데이터 정규화 → DB 저장
4. **최적화 분석**: UCAS 시뮬레이터 → AI 추천 → 사용자 제시
5. **알림 발송**: 임계치 감지 → Slack/이메일 발송

---

## 문서

### 백엔드 문서
- [백엔드 README](budgetops-be/README.md) - 백엔드 개요 및 실행 가이드
- [테스트 가이드](budgetops-be/docs/TESTING_GUIDE.md) - 테스트 작성 기준
- [OAuth 통합](budgetops-be/docs/OAUTH_INTEGRATION.md) - 소셜 로그인 구현
- [AWS EC2 가이드](budgetops-be/docs/AWS_EC2_GUIDE.md) - AWS 통합 가이드

### 프론트엔드 문서
- [프론트엔드 README](budgetops-fe/README.md) - 프론트엔드 개요
- [계정 연동 가이드](budgetops-fe/docs/accounts-integration.md) - 클라우드 계정 연동
- [Azure 연동 튜토리얼](budgetops-fe/docs/azure-account-tutorial.md) - Azure 연동 방법

### 프로젝트 문서
- [프로젝트 요약](PROJECT_SUMMARY.md) - 프로젝트 개요 및 성과
- [기능 상세](PROJECT_FEATURES.md) - 주요 기능 상세 설명
- [AI 활용 보고서](AI_UTILIZATION_REPORT.md) - AI 개발 활용 사례

---

## 테스트 방법

### 백엔드 테스트
```bash
cd budgetops-be

# 전체 테스트 실행
./gradlew test

# 특정 테스트 실행
./gradlew test --tests "AwsAccountServiceTest"

# 테스트 보고서 확인
open build/reports/tests/test/index.html
```

**테스트 커버리지**: Service 계층 80% 이상

### 프론트엔드 테스트
```bash
cd budgetops-fe

# 테스트 실행 (구현 예정)
npm test
```
