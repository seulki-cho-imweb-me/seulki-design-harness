# iframe 모달 통신 & 공유 Overlay 패턴

## The Insight
iframe 안에 모달을 넣고 부모 페이지에서 감싸는 구조에서는, **모달 전환 플로우를 반드시 부모 페이지에서 관리**해야 한다. iframe 내부에서 후속 모달(넛지, 설정 등)을 보여주면 iframe 크기/배경이 비쳐 보이는 문제가 반복된다.

## Why This Matters
- iframe 모드 CSS에 `!important`로 `display: block`을 걸면, JS에서 `el.style.display = 'none'`이 무시됨
- iframe 내부의 `position: fixed` 모달은 iframe 뷰포트에 국한되어 부모 페이지와 레이어가 불일치
- 모달 전환 시 dimmed 배경이 깜빡이거나, 이전 모달 콘텐츠가 비쳐 보임

## Recognition Pattern
- 부모 페이지에서 iframe으로 모달을 열고, iframe 내부에서 추가 모달을 띄워야 할 때
- `postMessage`로 부모-자식 간 통신이 필요할 때
- iframe 내부 요소가 `display: none`으로 안 숨겨질 때

## The Approach

### 1. 공유 Overlay + 패널 전환
```
부모 페이지:
  <div class="shared-overlay">      ← 하나의 dimmed 배경
    <div class="panel" id="panelA"> ← 충전 모달 (iframe)
    <div class="panel" id="panelB"> ← 넛지 모달 (부모 HTML)
    <div class="panel" id="panelC"> ← 설정 모달 (iframe)
  </div>
```
- dimmed는 유지하고, `display: none/flex`로 패널만 전환
- 후속 모달(넛지 등)은 iframe이 아닌 부모 페이지에 직접 구현

### 2. iframe → 부모 통신 원칙
- **단방향 이벤트만 전달**: `postMessage({ type: 'chargeComplete', data })`
- **UI 제어는 부모가 담당**: iframe은 "완료됨"만 알리고, 어떤 모달을 보여줄지는 부모가 결정
- **데이터 전달**: 설정값은 메시지에 포함하여 부모가 저장

### 3. iframe 재오픈 시 상태 복원
- 저장된 설정값을 **URL 파라미터**로 전달: `iframe.src = 'modal.html?condition=100&amount=10만'`
- iframe 내부에서 `URLSearchParams`로 읽어서 pre-fill
- 매번 새로 로드: `iframe.src = '...&t=' + Date.now()`

### 4. CSS !important 충돌 회피
- iframe 모드에서 `!important`를 쓸 때는 **숨김용 클래스도 `!important`로 정의**
```css
.overlay { display: block !important; }        /* 기본 표시 */
.overlay.charged { display: none !important; } /* 숨김 override */
```
- JS에서 `style.display = 'none'` 대신 **클래스 토글** 사용

### 5. 메시지 타입 일람
프로젝트에서 사용하는 `postMessage` 타입 정리:
| type | 방향 | 용도 |
|------|------|------|
| `closeModal` | iframe→부모 | 모달 닫기 (X 버튼, overlay 클릭) |
| `chargeComplete` | iframe→부모 | 충전 완료 + 넛지 표시 여부 + 자동충전 설정값 |
| `autoChargeConfigured` | iframe→부모 | 자동 충전 설정 완료 + 조건/금액 값 |
| `showToast` | iframe→부모 | 토스트 메시지 표시 |

### 6. sandbox 권한
- `allow-scripts allow-same-origin allow-forms allow-popups` — `allow-popups` 빠지면 새 탭 열기 차단됨

## Example
```js
// iframe에서 부모로 충전 완료 + 설정값 전달
window.parent.postMessage({
  type: 'chargeComplete',
  showPrompt: !autoRechargeEnabled,
  autoConfigured: true,
  condition: '100',
  amountLabel: '10만'
}, '*');

// 부모에서 수신 후 처리
window.addEventListener('message', (e) => {
  if (e.data.type === 'chargeComplete') {
    if (e.data.showPrompt) showPanel('panelPrompt');
    else {
      closeAllModals();
      if (e.data.autoConfigured) activateAutoCharge(e.data.condition, e.data.amountLabel);
    }
  }
});
```
