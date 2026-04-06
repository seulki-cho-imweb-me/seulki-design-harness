## 역할
디자인 산출물을 개발자와 협업 가능한 형태로 문서화한다.
매 프로젝트마다 내용은 달라지지만, 아래 구조와 규칙은 항상 동일하게 유지한다.

---

## 스펙 문서 구조

### 1. 개요
- 이 기능이 왜 필요한가 (해결하는 문제)
- 대상 사용자
- 범위 (이번에 다루는 것 / 다루지 않는 것)

### 2. 사용자 시나리오
- 핵심 플로우 (Happy Path)
- 예외 케이스 (Error, Empty, Loading 상태)

### 3. 화면별 스펙
- 컴포넌트 명세 (Clay 컴포넌트 이름 기준으로 작성)
- 각 요소의 상태 (default / hover / disabled / error 등)
- 조건부 노출 규칙 (언제 보이고 언제 숨겨지는가)

### 4. 인터랙션
- 사용자 액션 → 시스템 반응 형태로 작성
- 예: "저장 버튼 클릭 → 로딩 상태 → 성공 토스트 노출"

### 5. 엣지케이스
- 데이터가 없을 때 (Empty State)
- 오류가 발생했을 때 (Error State)
- 로딩 중일 때 (Loading State)

### 6. 미결 사항
- 아직 결정되지 않은 것
- 개발자/기획자와 확인이 필요한 것

---

## 작성 규칙

- 컴포넌트는 반드시 Clay 컴포넌트 이름으로 명시한다
- 조건은 "~이면 ~한다" 형태로 명확하게 쓴다
- 취향이나 의도가 아니라 동작 기준으로 쓴다
- 미결 사항은 숨기지 않고 명시한다

### Clay 컴포넌트 이름 작성 시 주의사항

Figma 라이브러리의 실제 컴포넌트 이름과 variant props로 추론한 이름이 다른 경우가 있다.
스펙에는 **Figma 실제 이름을 우선** 쓰되, 필요시 괄호 안에 역할을 병기한다.

예시:
- ✅ `Assets/CardHeader (Section Header, Action=Switch)`
- ✅ `Page Default Banner (Inline Alert, action=accent + secondary)`
- ❌ `Section Header` (Figma에서 이 이름으로 검색 안 됨)

자주 헷갈리는 매핑:
| 흔히 부르는 이름 | Figma 실제 이름 |
|---|---|
| Section Header | Assets/CardHeader |
| Text Field (with label) | Select |
| Alert / Inline Alert | Page Default Banner |
| Modal Header | _modalHeader/Desktop |
| Modal Footer | _modalFooter/Desktop |

상세 매핑은 `skills/clay-guide.md`의 "Figma 컴포넌트 이름 매핑" 섹션 참조.

### 토큰 명시 규칙

색상, 타이포, 스페이싱을 명시할 때는 Clay 시맨틱 토큰으로 쓴다.

예시:
- ✅ `text-slate-50` (Default text), `surface-critical-secondary` (에러 배경)
- ✅ `heading/2xlarge-bold` (24px Pretendard Bold)
- ❌ `#15181E`, `font-size: 24px` (직접 값 사용 금지)

---

## 메타 정보
- 이 스킬은 내용이 아닌 구조(틀)만 정의한다
- 실제 스펙 내용은 매 프로젝트마다 새로 생성된다
- 출력은 대화창에서 바로 받아 Notion/Figma에 복붙하는 방식으로 사용한다
