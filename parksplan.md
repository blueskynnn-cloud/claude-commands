---
description: Park의 표준 개발 워크플로우 — gstack + superpowers 10단계 하이브리드 파이프라인
argument-hint: [선택적 기능 설명]
---

# Park's Standard Workflow (parksplan)

사용자 요청: **$ARGUMENTS**

지금부터 아래 10단계 표준 워크플로우를 **순서대로** 진행하세요. 각 단계를 완료하기 전에 다음 단계로 넘어가지 마세요. 단계 사이마다 사용자에게 "다음 단계 진행할까요?"를 묻고 승인을 받으세요.

## 핵심 원칙
- **Planning is not review. Review is not shipping.**
- "바로 만들어줘" 금지. 문제 재정의부터 시작.
- 플랜 이중검증 통과 전 코딩 진입 금지.

## 실행할 10단계

### 🧠 STAGE 1 — Think
**Step 1. `/office-hours` 실행**
- gstack의 office-hours 스킬을 Skill 툴로 호출
- 15-20분 Q&A 진행 (왜 / 어떤 상황 / 팀 규모 / 유사 툴 불편점)
- 추상적 답변 받으면 구체적 사례 재질문

**Step 2. 대화 내용을 `design-doc.md`로 정리**
- 프로젝트 루트 또는 `docs/` 아래에 저장
- 뭘·왜·어떻게 3축으로 구조화

### 📐 STAGE 2 — Plan
**Step 3. `superpowers:brainstorming` 실행**
- 빈틈 채우기
- UX/UI 작업이면 **목업 자동 생성** 적극 활용 (피그마 대체)

**Step 4. `superpowers:writing-plans` 실행**
- 단계별 `plan.md` 생성
- 앞으로 모든 작업의 기준점

**Step 5. 플랜 이중검증**
- `/plan-eng-review` (gstack) — 엔지니어링 관점
- `/codex` (gstack) — OpenAI Codex CLI의 2차 소견
- 불일치 findings만 사용자에게 판단 요청
- **승인 없으면 STAGE 1로 복귀**

### 🔨 STAGE 3 — Build
**Step 6. `superpowers:using-git-worktrees` 실행**
- 기능별·작업단위별 독립 공간 분리
- 자동 커밋 활성화 (의미 단위 기록)

**Step 7. `superpowers:subagent-driven-development` 실행**
- plan.md를 서브에이전트에게 병렬 분배
- 메인 Claude는 오케스트레이터 역할
- UI 작업 중간에 `/design-review`로 AI Slop 차단

### ✅ STAGE 4 — Verify & Ship
**Step 8. `/review` + `/qa` 실행**
- `/review` — 프로덕션 버그 사냥 (스태프 엔지니어 관점)
- `/qa` — 실제 Chromium으로 E2E 검증 + 회귀 테스트 자동 생성

**Step 9. `superpowers:verification-before-completion` 실행**
- "완료" 선언 전 강제 검증 체크리스트

**Step 10. `/ship` 실행**
- main 동기화 → 테스트 → 커버리지 감사 → PR 생성

## 상세 레퍼런스
메모리 파일 `workflow_parksplan.md`에 전체 맥락과 숨은 팁이 있음. 필요 시 참조.

## 진행 규칙
1. 각 단계 시작 전 **"Step N: [이름] 시작합니다"** 선언
2. 각 단계 완료 후 **산출물 경로 명시** 후 사용자 승인 대기
3. 단계 건너뛰기 요청 시 **왜 위험한지 설명** 후 재확인
4. 에러·블로커 발생 시 **이전 단계로 롤백 여부** 사용자에게 질문
