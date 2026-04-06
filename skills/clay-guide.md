# Clay Guide Skill

## 역할
Clay 디자인시스템 기준으로 컴포넌트 선택과 사용 방법을 안내한다.
자주 쓰는 컴포넌트부터 쌓아가며 업데이트한다.

---

## 컴포넌트 목록

### Button
- **언제 쓰는가:** 사용자의 주요 액션 트리거 (저장, 충전, 확인 등)
- **언제 쓰지 않는가:** 단순 네비게이션 (→ Link), 토글 동작 (→ Switch)
- **주요 variant:**
  - Props: `rounded`, `tonal`, `size`, `state`, `fullWidth`, `icon`
  - size: tiny / small / medium / large
  - state: default / hover / pressed / disabled / loading
  - icon: none / leading / trailing / only
  - tonal: True / False (Primary 계열에서 톤 다운)
  - rounded: True / False
  - fullWidth: True / False
- **자주 쓰는 조합:** Modal footer에서 `size=medium, fullWidth=True` 쌍 (accent + secondary)
- **주의사항:** tonal=True는 보조 액션용. 1920+ variants로 가장 큰 컴포넌트 세트

### Social Login Button
- **언제 쓰는가:** 소셜 로그인/연동 (Google, 카카오, 네이버, 페이스북 등)
- **언제 쓰지 않는가:** 일반 액션 버튼
- **주요 variant:**
  - Props: `variants`, `size`, `state`, `fullWidth`, `label`
  - variants: Google / 카카오 / 네이버 / 페이스북 등
- **자주 쓰는 조합:** 로그인 페이지에서 fullWidth=True 세로 스택
- **주의사항:** 각 플랫폼 브랜드 가이드 준수 필요

### Icon Button
- **언제 쓰는가:** 아이콘만으로 액션을 표현할 때 (닫기, 더보기, 편집 등)
- **언제 쓰지 않는가:** 라벨이 필요한 주요 액션
- **주요 variant:**
  - Props: `compact`, `size`, `state`, `variant`
  - variant: filled / outlined
  - compact: True / False
- **자주 쓰는 조합:** Modal 헤더 닫기 버튼, 리스트 아이템 trailing action
- **주의사항:** compact=True는 터치 타겟이 줄어드므로 모바일 주의

### Text Field (Input)
- **언제 쓰는가:** 단일 행 텍스트/숫자 입력
- **언제 쓰지 않는가:** 긴 텍스트 (→ Textarea), 선택형 (→ Select)
- **주요 variant:**
  - Props: `content`, `helperText`, `label`, `size`, `state`
  - size: medium / Large
  - state: default / hover / focus / disabled / success / invalid
  - content: placeholderText / filledText / filledNumeric / filledTag
  - label: True / False
  - helperText: True / False
- **자주 쓰는 조합:** label=True + helperText=True (폼 필드 기본)
- **주의사항:** filledTag는 태그 입력용. filledNumeric은 숫자 전용 표시

### Textarea
- **언제 쓰는가:** 여러 줄 텍스트 입력 (메모, 설명 등)
- **언제 쓰지 않는가:** 단일 행 입력 (→ Text Field)
- **주요 variant:**
  - Props: `content`, `height`, `size`, `state`
  - height: min / default / max
  - content: empty / placeholderText / filled
- **자주 쓰는 조합:** height=default, size=medium
- **주의사항:** height=max는 고정 높이, min은 자동 확장

### Select / Dropdown
- **언제 쓰는가:** 정해진 옵션 중 하나를 선택할 때
- **언제 쓰지 않는가:** 자유 입력이 필요할 때 (→ Text Field), 2~3개 선택지 (→ Radio)
- **주요 variant:**
  - Props: `filledTag`, `size`, `state`, `type`
  - size: medium / large
  - type: default / doubleLines
  - state: default / hover / focus / readOnly / disabled
  - filledTag: True / False
- **자주 쓰는 조합:** type=default, filledTag=False (단일 선택)
- **주의사항:** doubleLines는 부가 정보가 필요한 경우

### Option List / Option Item
- **언제 쓰는가:** Select, Popover 내부의 선택지 리스트
- **언제 쓰지 않는가:** 독립적인 리스트 UI (→ List Item)
- **주요 variant:**
  - Props: `Action`, `Allow multiple`, `Popover`, `Size`, `State`, `Subtitle`, `Type`
  - Allow multiple: None / Checkbox / Checkbox count
  - State: Default / Hover / Selected / Disabled
  - Size: Default / Large
- **자주 쓰는 조합:** Allow multiple=None + Popover=False (단일 선택 드롭다운)
- **주의사항:** Checkbox count는 다중 선택 시 선택 개수 표시

### Checkbox
- **언제 쓰는가:** 다중 선택, 동의/확인 체크
- **언제 쓰지 않는가:** 단일 on/off (→ Switch), 단일 선택 (→ Radio)
- **주요 variant:**
  - Props: `Checked`, `Indeterminate`, `Size`, `State`
  - Size: Medium / Large
  - State: Default / Hover / Disabled
- **자주 쓰는 조합:** Size=Medium, Indeterminate=False (기본 체크박스)
- **주의사항:** Indeterminate는 전체선택에서 일부만 선택된 상태

### Checkbox List Item
- **언제 쓰는가:** 체크박스가 포함된 리스트 항목
- **언제 쓰지 않는가:** 단순 체크박스만 필요할 때
- **주요 variant:**
  - Props: `Indeterminate`, `Size`, `checkbox position`, `checked`, `state`
  - checkbox position: leading / trailing
- **자주 쓰는 조합:** checkbox position=leading, Size=Medium
- **주의사항:** trailing은 우측 배치

### Radio List Item
- **언제 쓰는가:** 여러 항목 중 하나만 선택
- **언제 쓰지 않는가:** 다중 선택 (→ Checkbox), 3개 이하 간단한 선택 (→ Segment)
- **주요 variant:**
  - Props: `Size`, `radio position`, `selected`, `state`
  - radio position: leading / trailing / only
- **자주 쓰는 조합:** radio position=leading, Size=Medium
- **주의사항:** only는 라벨 없이 라디오 버튼만 표시

### Switch / Toggle
- **언제 쓰는가:** 기능 on/off 전환 (자동 충전, 알림 등)
- **언제 쓰지 않는가:** 복수 선택 (→ Checkbox), 즉시 반영 아닌 경우 (→ Checkbox)
- **주요 variant:**
  - Props: `Selected`, `Size`, `Status`
  - Size: Medium / Large
  - Status: Default / Hover
- **자주 쓰는 조합:** Size=Medium, Section Header의 Action=Switch와 함께
- **주의사항:** 토글은 즉시 반영이 기본. 저장 버튼이 별도로 있으면 Checkbox 고려

### Tab
- **언제 쓰는가:** 같은 맥락의 콘텐츠를 전환할 때
- **언제 쓰지 않는가:** 단계별 진행 (→ Stepper), 페이지 이동 (→ Navigation)
- **주요 variant:**
  - Props: `badge`, `fullWidth`, `size`, `state`, `status`
  - status: default / warning / success
  - badge: none / dot / number
  - state: default / hover / selected / disabled
- **자주 쓰는 조합:** fullWidth=True, badge=none (기본 탭)
- **주의사항:** status는 탭 내 콘텐츠 상태 표시용 (경고, 성공 등)

### Tab Item
- **언제 쓰는가:** Tab 컴포넌트 내부의 개별 탭 버튼
- **주요 variant:**
  - Props: `Align`, `Badge`, `Size`, `Text`

### Badge / Tag
- **언제 쓰는가:** 상태 표시, 카테고리 라벨, 카운트 표시
- **언제 쓰지 않는가:** 액션이 필요한 경우 (→ Button)
- **주요 variant:**
  - Props: `background`, `icon`, `size`, `variant`
  - variant: plain / success / critical / warning / accent 등
  - size: xsmall / small / medium / large
  - icon: none / leading / trailing / both / only
- **자주 쓰는 조합:** variant=plain, size=small (기본 태그)
- **주의사항:** background=False면 텍스트만 표시

### Tag (Removable)
- **언제 쓰는가:** 사용자가 추가/제거할 수 있는 태그 (필터, 선택된 항목 등)
- **주요 variant:**
  - Props: `size`, `variant`, `warp`
  - variant: filled / removable
  - warp: True / False (줄바꿈 허용)

### Avatar
- **언제 쓰는가:** 사용자/멤버 프로필 이미지
- **언제 쓰지 않는가:** 로고, 아이콘
- **주요 variant:**
  - Props: `selected`, `size`, `userImg`, `badge`
  - size: xsmall / small / medium / large / xlarge / 3xlarge
  - badge: none / dot / number
- **자주 쓰는 조합:** size=medium, userImg=True
- **주의사항:** userImg=False면 이니셜/기본 아바타

### Tooltip
- **언제 쓰는가:** 부가 설명이 필요할 때 (hover/click으로 표시)
- **언제 쓰지 않는가:** 중요한 안내 (→ Alert), 긴 설명 (→ Popover)
- **주요 variant:**
  - Props: `Action`, `Dark`, `Pointer`, `Supporting text`
  - Pointer: None / Top center / Bottom center / Left / Right 등
  - Dark: True / False
- **자주 쓰는 조합:** Dark=True, Pointer=Bottom center
- **주의사항:** Action=True면 버튼 포함 가능

### Coach Mark / Popover Guide
- **언제 쓰는가:** 온보딩, 기능 안내 (단계별 가이드)
- **주요 variant:**
  - Props: `Pointer`, `closeButton`, `showFooter`, `showStep`
- **자주 쓰는 조합:** showStep=True, showFooter=True (다단계 가이드)

### Modal / Dialog
- **언제 쓰는가:** 중요한 액션 확인, 폼 입력, 상세 정보 표시
- **언제 쓰지 않는가:** 간단한 알림 (→ Toast), 경량 선택 (→ Popover)
- **주요 variant:**
  - Props: `breakPoint`, `height`, `width`
  - width: small / medium / large / full
  - height: default / full-height
  - breakPoint: desktop / mobile
- **자주 쓰는 조합:** width=small, breakPoint=desktop (기본 확인 모달)
- **주의사항:** full-height는 콘텐츠가 긴 경우. mobile breakPoint에서 자동 full-width

### Dialog Footer
- **언제 쓰는가:** Modal 하단 액션 버튼 영역
- **주요 variant:**
  - Props: `breakPoint`, `buttonGroup`, `scroll`
- **자주 쓰는 조합:** buttonGroup=True, scroll=False

### Section Header
- **언제 쓰는가:** 폼/설정 영역의 섹션 구분
- **언제 쓰지 않는가:** 페이지 타이틀 (→ Page Header)
- **주요 variant:**
  - Props: `Action`, `Align`, `Header`, `Inline`, `Separator`
  - Header: Large / Medium (추정)
  - Action: None / Icon / Switch / Text
  - Align: Left
- **자주 쓰는 조합:** Action=Switch (설정 on/off 섹션), Separator=True
- **주의사항:** Inline=True면 한 줄에 라벨+액션 배치

### Alert / Banner
- **언제 쓰는가:** 중요 알림, 상태 변경 안내, 경고
- **언제 쓰지 않는가:** 일시적 피드백 (→ Toast)
- **주요 variant:**
  - Props: `Action`, `Size`, `State`
  - State: Critical / Warning / Info 등
  - Action: None / icon / textButton
  - Size: Small / Medium
- **자주 쓰는 조합:** Size=Medium, Action=textButton
- **주의사항:** Critical은 빨간색 배경, 즉각 조치 필요 시

### Inline Alert
- **언제 쓰는가:** 폼 내부 경고/안내 (입력 영역 근처)
- **주요 variant:**
  - Props: `action`, `state`
  - action: none / accent + secondary / dismissible / critical + secondary
- **자주 쓰는 조합:** action=none (단순 안내)

### Toast / Snackbar
- **언제 쓰는가:** 일시적 피드백 (저장 완료, 복사됨 등)
- **주요 variant:**
  - Props: `Dark`, `Type`
  - Type: Confirm / Primary
  - Dark: True / False

### Progress / Stepper
- **언제 쓰는가:** 진행 상태 표시
- **주요 variant:**
  - Props: `size`, `state`
  - state: 퍼센트(70%) 또는 단계(1/3, 3/5) 표기

### File Upload
- **언제 쓰는가:** 파일/이미지 업로드
- **주요 variant:**
  - Props: `Compact`, `Stack`, `Status`, `Type`
  - Type: Solid / Outlined
  - Status: Upload / Uploading / Complete 등
  - Stack: 1~5 item

### Date Picker
- **언제 쓰는가:** 날짜/기간 선택
- **주요 variant:**
  - Input: `align`, `content`, `presets`, `state`, `variant` (singleDate / rangeDate)
  - Calendar: `action`, `presets`, `selected`, `variant` (multiMonth)
- **자주 쓰는 조합:** variant=singleDate, presets=Off
- **주의사항:** rangeDate는 시작일~종료일 범위 선택

### Table
- **언제 쓰는가:** 데이터 목록 표시 (이력, 리스트 등)
- **주요 variant:**
  - Props: `fixedHeight`, `modal`, `stickyHeader`
- **자주 쓰는 조합:** stickyHeader=True, fixedHeight=False

### Navigation (Side)
- **언제 쓰는가:** 좌측 사이드바 네비게이션
- **주요 variant:**
  - Menu Item: `compact`, `small screen`, `state`, `subMenu`
  - Section: `compact`, `small screen`, `type` (logo / sectionTitle)

### Bottom Navigation
- **언제 쓰는가:** 모바일 하단 탭 네비게이션
- **주요 variant:**
  - Props: `icon`, `state`
  - icon: home / user / contents / campaign 등

### Page Layout
- **언제 쓰는가:** 전체 페이지 레이아웃 프레임
- **주요 variant:**
  - Props: `Screen`, `column`
  - Screen: 375 / 600 / 1024 / 1440 / 1920 / 3200
  - column: 2단 / 3단 (1440/1024 only)

### Chart (Line)
- **언제 쓰는가:** 시계열 데이터 시각화
- **주요 variant:**
  - Props: `Comparison`, `Dot`, `Lines count`, `Null`, `Skeleton`, `Spline`

### Chart Header
- **언제 쓰는가:** 차트 상단 기간/비교 선택 영역
- **주요 variant:**
  - Props: `Current`, `Skeleton`, `Small screen`, `Time intervals`

---

## 토큰 체계

### Color Palette (Core)

| 이름 | 50 | 100 | 200 | 300 | 400 | 500 (Key) | 600 | 700 | 800 | 900 |
|---|---|---|---|---|---|---|---|---|---|---|
| slate | #F8F9FB | #E2E5E9 | #DBDEE3 | #BCC0C6 | #9FA3AB | #717680 | #4B515B | #24282F | #1D2027 | #15181E |
| blue | #ECF9FF | #DEF3FF | #B6EAFF | #75DBFF | #2CCAFF | #00B9FF | #0090D4 | #0072AB | #00608D | #065074 |
| coralRed | #FFEEEE | #FFDFDF | #FFC5C5 | #FF9D9D | #FF6464 | #FF4040 | #ED1515 | #C80D0D | #A50F0F | #881414 |
| neonGreen | #E8FFE4 | #CBFFC5 | #9AFF92 | #5BFF53 | #24FB20 | #00E600 | #00B505 | #028907 | #086C0C | #0C5B11 |
| mustard | #FFFBD8 | #FFF6C5 | #FFEE85 | #FFDE46 | #FFCC1B | #FFAA00 | #E28100 | #BB5902 | #984508 | #7C380B |
| pink | #FFF3FC | #FFE6FA | #FFCCF5 | #FFA3EA | #FF6DDB | #FF50DA | #E316B3 | #BD0E91 | #9A0E75 | #7E115F |
| neonPurple | #FDF3FF | #F9E6FF | #F2CCFF | #ECA4FF | #E26EFF | #CD28FD | #B818E1 | #9C10BB | #810F99 | #6D127D |

각 색상에 tint 변형: `{color}-tint-{5|10|15|20}` (예: `rgba(0, 185, 255, 0.10)`)
특수값: `black (#000000)`, `white (#FFFFFF)`

### Semantic Token (Light mode 🌝)

**토큰 네이밍 규칙:** `element-role/emphasis-state` (하이픈 구분, 기본→구체 순서)

| 카테고리 | 토큰 | 용도 |
|---|---|---|
| **Background** | bg-slate-50 | 페이지 배경 (#F8F9FB) |
| | surface-slate-100 | 카드/섹션 배경 |
| | surface-critical-primary/secondary | Critical 요소 배경 (coralRed) |
| | surface-warning-primary/secondary | Warning 요소 배경 (mustard) |
| | surface-success-primary/secondary | Success 요소 배경 (neonGreen) |
| | surface-highlight-primary/secondary | Informative 요소 배경 (blue) |
| | surface-toast-100 | Toast 배경 (slate-900 @85%) |
| | field-sub-100 | Textfield 배경 |
| | field-disabled-100 | Disabled 필드 배경 (slate-tint-5) |
| **Text** | text-slate-50 | Default text, Primary label (→ slate-900) |
| | text-sub-100 | Secondary label, Placeholder (→ slate-500) |
| | text-minimal-100 | Minimal text (→ slate-400) |
| | text-sub-disabled | Disabled text (→ slate-300) |
| | text-critical-100 | Error text (→ coralRed-500) |
| | text-warning-100 | Warning text (→ mustard-600) |
| | text-success-100 | Success text (→ neonGreen-600) |
| | text-accent-100 | Link, Primary text button (→ blue-500) |
| | text-inverse | Button text on dark bg (→ white) |
| **Border** | border-slate-50 | Default border (→ slate-200) |
| | border-sub-disabled | Disabled border (→ slate-100) |
| | border-critical | Error border (→ coralRed-500) |
| | border-success-100 | Success border (→ neonGreen) |
| | border-highlight-100 | Informative border (→ blue) |
| **Action** | action-accent-100/hover/pressed/disabled | Accent 버튼 (blue 계열) |
| | action-primary-100/hover/pressed/disabled | Primary 버튼 (slate-900 계열) |
| | action-secondary-100/hover/pressed/disabled | Secondary 버튼 (white/border) |
| | action-critical-100/hover/pressed/disabled | Critical 버튼 (coralRed 계열) |
| | action-accentTonal/primaryTonal/criticalTonal | Tonal 버튼 (각색 tint) |
| | action-toggle-100 | Switch/Toggle |
| **Layer** | layer-hover-100 | Row hover (slate-tint-5) |
| | layer-selected-hover | 선택된 row hover |

### Typography

| 스타일 | Font Family | Size | Weight | Line Height |
|---|---|---|---|---|
| heading/5xlarge-bold | Pretendard | 48px | Bold | 64px |
| heading/4xlarge-bold | Pretendard | 36px | Bold | 48px |
| heading/3xlarge-bold | Pretendard | 30px | Bold | 40px |
| heading/2xlarge-bold | Pretendard | 24px | Bold | 32px |
| heading/xlarge-bold | Pretendard | 20px | Bold | 28px |
| heading/large | Pretendard | 18px | Regular | 24px |
| heading/large-bold | Pretendard | 18px | Bold | 24px |
| heading/medium | Pretendard | 16px | Regular | 24px |
| heading/medium-bold | Pretendard | 16px | Bold | 24px |
| body/large | imweb Sans | 16px | 400 | 24px |
| body/large-bold | imweb Sans | 16px | 600 | 24px |
| body/medium | imweb Sans | 14px | 400 | 20px |
| body/medium-bold | imweb Sans | 14px | 600 | 20px |
| body/small | imweb Sans | 12px | 400 | 16px |
| body/small-bold | imweb Sans | 12px | 600 | 16px |
| label/medium | imweb Sans | 14px | 400 | 20px |
| label/medium-bold | imweb Sans | 14px | 600 | 24px |
| label/small | imweb Sans | 12px | 400 | 16px |
| label/small-bold | imweb Sans | 12px | 600 | 16px |
| label/xsmall | imweb Sans | 11px | 600 | 12px |

### Spacing
- 단계: 4 / 6 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48
- medium이 기본값 (🏁 표시)

### Effects (Shadow)

| 토큰 | 용도 |
|---|---|
| dropShadow/none | 그림자 없음 |
| dropShadow/card | 카드 (0 1px 3px rgba(0,0,0,0.06)) |
| dropShadow/toast | Toast (0 4px 12px rgba(0,0,0,0.15)) |
| dropShadow/popover | Popover/Dropdown (0 4px 16px rgba(0,0,0,0.12)) |
| dropShadow/modal | Modal (0 8px 32px rgba(0,0,0,0.16)) |
| dropShadow/layer | Layer |
| dropShadow/pageAside | 사이드 패널 |
| dropShadow/raisedButton | 떠있는 버튼 |

### Grid

| 토큰 | Columns |
|---|---|
| Column Grid - Xsmall (375) | 4 cols |
| Column Grid - Small (600) | 8 cols |
| Column Grid - Medium (1024) | 12 cols |
| Column Grid - Large (1440) | 12 cols |
| Column Grid - Extra Large (1920) | 12 cols |
| Column Grid - 2XL (3200) | 12 cols |

### 색상 참조 문서
- https://design.imweb.me/foundation/colors

---

## Figma 컴포넌트 이름 매핑

props 기반 추론 이름과 Figma 라이브러리 실제 이름이 다른 경우가 있다.
스펙 작성 시 Figma 실제 이름을 우선 사용한다.

| 이 문서의 이름 | Figma 실제 이름 | 비고 |
|---|---|---|
| Button (Primary) | Primary Button | accent 버튼 |
| Text Field | Select (label+input+helper 구조) | Figma에서 Select로 분류됨 |
| Text Field (Tag) | Outlined Textfield (Tag) | 검색/태그 입력용 |
| Section Header | Assets/CardHeader | Action=Switch 포함 |
| Alert / Banner | Page Default Banner | state별 분기 |
| Inline Alert | Page Default Banner | action 포함 변형 |
| Toast | Toast | Dark pill 형태 |
| Modal Header | _modalHeader/Desktop | 타이틀 + 닫기 |
| Modal Footer | _modalFooter/Desktop | 버튼 그룹 + 안내 텍스트 |

---

## 컴포넌트 조합 규칙

### Modal 폼 패턴
Modal + Section Header + Text Field/Select + Dialog Footer(buttonGroup=True)

### 설정 토글 패턴
Section Header(Action=Switch) + 하위 폼 필드들 (Switch off 시 disabled)

### 리스트 선택 패턴
Select → Option List(Option Item) 또는 Radio List Item 그룹

### 알림/피드백 계층
- 즉각 인지: Alert/Banner (페이지 내 고정)
- 일시 피드백: Toast (자동 사라짐)
- 부가 설명: Tooltip (hover)
- 온보딩: Coach Mark (단계별)

### 폼 유효성 패턴
Text Field(state=invalid) + helperText=True (에러 메시지)

### 충전/결제 모달 패턴
_modalHeader + Slider + 주문요약 카드(surface 배경) + 결제카드 선택 + _modalFooter(안내텍스트 + Button)
- 슬라이더 하단에 "최다선택"(neonGreen) / "최대혜택"(blue) 태그 배치
- 주문 요약: label 좌측 + value 우측 정렬, 총 금액은 heading/xlarge-bold
- 결제 카드: 카드 브랜드 아이콘 + 카드명 + 번호 + chevron-down

---

## 새 컴포넌트를 만들어야 하는 기준
- 기존 컴포넌트로 흡수가 안 될 때
- 3개 이상의 화면에서 동일한 패턴이 반복될 때

---

## 메타 정보
- 원본 출처: Figma Clay 라이브러리 (Clay-2.6.26, 6,776 components / 133 variant groups)
- 컬러/타이포/이펙트 토큰: Figma get_styles API에서 추출 (2026-04-06)
- 컬러 팔레트: Figma 컬러 페이지(node 2358-3200)에서 추출 (2026-04-06)
- 마지막 업데이트: 2026-04-06
- 컴포넌트 추가 방식: 쓸 때마다 하나씩 추가
- 참고: Figma 컴포넌트 이름 매핑 섹션 참조 — props 추론 이름과 실제 이름이 다를 수 있음
