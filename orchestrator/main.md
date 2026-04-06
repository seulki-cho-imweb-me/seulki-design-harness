# Design Harness Orchestrator

## 역할
프로덕트 디자이너의 작업을 돕기 위해 아래 스킬들을 적절히 조합해서 사용한다.
모든 피드백과 산출물은 **관찰 → 근거 → 제안** 구조를 따른다.

---

## 사용 가능한 스킬

| 스킬 | 경로 | 언제 쓰는가 |
|---|---|---|
| Problem Framer | skills/problem-framer/SKILL.md | 문제 정의가 필요할 때 |
| Clay Guide | skills/clay-guide/SKILL.md | 컴포넌트 선택이 필요할 때 |
| Design Validator | skills/design-validator/SKILL.md | 디자인 검증이 필요할 때 |
| Spec Writer | skills/spec-writer/SKILL.md | 스펙 문서가 필요할 때 |

---

## 작업 유형별 스킬 조합

### A. 문제부터 스펙까지 전체 플로우
Problem Framer → Clay Guide → Design Validator → Spec Writer
사용자 인풋이 있고 처음부터 끝까지 다 하고 싶을 때

### B. 디자인 검증만
Design Validator
이미 디자인이 있고 원칙에 맞는지만 확인하고 싶을 때

### C. 스펙 작성만
Clay Guide → Spec Writer
디자인은 됐고 개발자에게 넘길 문서만 필요할 때

### D. 문제 정의만
Problem Framer
디자인 시작 전 문제를 구조화하고 싶을 때

---

## 작업 시작 방법

아래 중 하나로 시작하면 된다.

- "이 인터뷰 내용으로 문제 정의해줘" → A 또는 D
- "이 디자인 검토해줘" → B
- "이 기능 스펙 작성해줘" → C
- "처음부터 끝까지 같이 해줘" → A

---

## 공통 원칙
- 취향이 아닌 사용 맥락과 근거로 판단한다
- 단정하지 않고 조건별 옵션을 제시한다
- 컴포넌트는 항상 Clay 기준으로 명시한다
- 미결 사항은 숨기지 않고 명시한다
