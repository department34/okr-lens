# 🎯 OKR Lens — AI-Powered OKR Management Platform

**OKR Lens**는 2026 OKR 기반 개인평가제도를 처음 운영하는 IT 조직을 지원하는 **3역할 협력 플랫폼**입니다.

- **R1 피평가자**: AI 기반 KR 초안 자동 생성 → 대화형 정제 → 자신감 있게 제출
- **R2 평가자**: AI 규칙 검증 → 근거 있는 승인/반려 → 공정한 코칭
- **R3 인사담당자**: 위험 KR 자동 식별 → 사전 코칭 → 평가위원회 사전 준비

## 🚀 Quick Start

### 요구사항
- Node.js 18+
- npm 또는 yarn
- Anthropic API Key (Claude API 사용)

### 설치 & 실행

```bash
# 의존성 설치
npm install

# 환경 변수 설정
echo "ANTHROPIC_API_KEY=your_api_key_here" > .env.local

# 개발 서버 시작
npm run dev
```

브라우저에서 다음 주소로 접속:
- **R1 피평가자**: http://localhost:3000/r1-employee
- **R2 평가자**: http://localhost:3000/r2-evaluator
- **R3 인사담당자**: http://localhost:3000/r3-hr

## 📂 Project Structure

```
okr-lens/
├── app/
│   ├── r1-employee/       # R1 피평가자 페이지
│   ├── r2-evaluator/      # R2 평가자 페이지
│   └── r3-hr/             # R3 인사담당자 페이지
├── shared/
│   ├── types.js           # KR 데이터 스키마
│   ├── diagnosticEngine.js # 위험 태깅 엔진
│   └── dataAccess.js      # 데이터 읽기/쓰기
├── src/data/
│   └── krs.json           # 공유 KR 데이터 저장소
└── PRD.md                 # 상세 기획서
```

## ✨ Key Features

### R1 피평가자
- **KR 초안 생성**: 자유형 입력 → Claude API → 4가지 초안 자동 생성
- **대화형 정제**: 피드백 입력 → 수정안 생성 (반복 가능)
- **확정 & 제출**: 최종 KR 저장 후 평가자에게 제출

### R2 평가자
- **OKR 검토**: 팀원 KR 아코디언 뷰로 조회
- **AI Validation**: 9개 체크 항목 자동 평가 → 위험도 판정
- **승인/반려**: 근거 있는 의사결정 + 코칭 메모

### R3 인사담당자
- **위험 자동 태깅**: KR 로드 → 위험도·유형 자동 계산
- **필터 & 검색**: 위험도(🔴 상/🟡 중/🟢 하) 필터링
- **사전 코칭**: 위험 KR 상세 패널 + 개선 권고

## 🔧 Tech Stack

| 계층 | 기술 |
|------|------|
| **Framework** | Next.js 14 (App Router) |
| **Styling** | Tailwind CSS |
| **Charts** | Recharts |
| **State Management** | React Context + useState |
| **AI** | Claude API (claude-sonnet-4-6) |
| **Data** | JSON + git |
| **Deployment** | Vercel (또는 로컬) |

## 📊 Diagnostic Engine (위험 태깅)

### 9개 체크 항목
```
① 수치로 측정 가능한가?
② 외부 의존성이 없는가?
③ 도전적인가?
④ 현실적으로 달성 가능한가?
⑤ 명확한 언어인가?
⑥ 다른 팀과 겹치지 않는가?
⑦ 신기술 과의존하지 않는가?
⑧ 단순 건수형이 아닌가?
⑨ 평가자가 확인할 수 있는가?
```

### 위험도 판정
- **🟢 하**: 체크 위반 0~1개 (코칭 불필요)
- **🟡 중**: 체크 위반 2~3개 (주의 필요)
- **🔴 상**: 체크 위반 4개 이상 (즉시 코칭)

## 📅 Development Timeline

| 일정 | 내용 |
|------|------|
| **Day 1** | 공유 스키마 + 환경 셋업 |
| **Day 2~4** | 각 역할 Feature 1 개발 + 최소 경로 통합 |
| **Day 5~6** | 고도화 (Feature 2·3) |
| **Day 7** | 정기점검 + 데이터 무결성 검증 |
| **Day 8~9** | UI 완성 + mock 데이터 보강 |
| **Day 10** | 최종 리허설 + 시연 준비 |

## 📚 Documentation

- **[PRD.md](./PRD.md)** — 상세 기획서 (목표, 기능, 성공 기준)
- **[final_spec.md](./final_spec.md)** — 기술 스펙 + 개발 일정

## 🎬 Demo Scenario

### 10분 데모 시나리오

1. **R1 (2분)**: 업무 입력 → AI 초안 4종 생성 → 정제 → 제출
2. **R2 (2분)**: R1 KR 조회 → AI Validation → 승인
3. **R3 (3분)**: 위험 KR 자동 식별 → 필터 → 사전 코칭 리스트
4. **통합 (3분)**: R1→R2→R3 연쇄 동작 확인

## 🔐 Security & Privacy

- **데이터**: 로컬 JSON (git 추적)
- **API 키**: `.env.local`에만 저장 (git ignore)
- **감사 로그**: git commit으로 변경 이력 자동 기록
- **역할 기반 접근**: R1/R2/R3 간단한 역할 분리

## 📈 Success Criteria

- [ ] R1: KR 초안 4종 생성 (Claude API)
- [ ] R1: 대화형 정제 + 저장
- [ ] R2: KR 조회 + AI Validation + 승인/반려
- [ ] R3: 위험 자동 태깅 + 필터 + 상세 패널
- [ ] **통합**: R1→R2→R3 전체 파이프라인 정상 동작

## 🤝 Contributing

이 프로젝트는 3명의 팀원이 10일 안에 완주하도록 설계되었습니다.

### Git Workflow
```bash
# feature 브랜치에서 작업
git checkout -b feature/r1-kr-generation

# 매일 저녁 PR 올리기
git push origin feature/r1-kr-generation

# 매일 아침 리뷰 및 병합
# → develop 브랜치로 병합
```

### Daily Sync
- **수요일**: 진도 + 블로커 체크
- **금요일**: 통합 검증 + 다음주 계획

## 📞 Support

문제가 발생하면 [Issues](https://github.com/department34/okr-lens/issues)를 통해 보고해주세요.

## 📄 License

이 프로젝트는 내부 교육용으로 제작되었습니다.

---

**이 프로젝트는 3명의 팀이 10일 안에 완주할 수 있도록 설계된 실행 가능한 기획서입니다.**  
**즉시 개발을 시작할 수 있습니다.** 🚀
