# 16:9 웹 PPT 공통 프롬프트 템플릿

---

## ✅ 기본 사용법

아래 [공통 프롬프트]를 먼저 붙여넣고,  
그 아래에 **[주제 요청]** 을 추가하면 됩니다.

```
[공통 프롬프트 전체 복사]

[주제 요청]
주제: Netcode for GameObjects 개념 정리
슬라이드 수: 8장
```

---

## 📋 공통 프롬프트 (복사해서 사용)

```
아래 스펙을 그대로 지켜서 16:9 웹 PPT HTML 파일을 만들어줘.

## ❶ 전체 구조

- 단일 HTML 파일로 작성 (CSS·JS 모두 인라인)
- 뷰포트: 1280×800px 고정 슬라이드
- 슬라이드 전환: 좌우 슬라이드 애니메이션 (translateX 56px, 0.38s ease)
- 반응형 스케일: window 크기에 맞게 transform:scale() 자동 적용
- 하단 컨트롤 바: 이전/다음 버튼 + 중앙 점 네비게이션 + 슬라이드 번호
- 키보드: ← → 방향키로 이동

## ❷ 디자인 시스템 (CSS 변수 — 반드시 준수)

:root {
  --bg:#0a0c10;        /* 슬라이드 기본 배경 */
  --bg2:#111318;       /* 카드·패널 배경 */
  --bg3:#1c1f28;       /* 중첩 배경 */
  --accent:#00d4a0;    /* 메인 강조색 (초록) */
  --purple:#7b5cf5;    /* 보조 강조색 */
  --orange:#f5a623;    /* 경고·주의 */
  --red:#ef4444;       /* 오류·금지 */
  --blue:#3b82f6;      /* 정보·링크 */
  --text:#e8eaf2;      /* 기본 텍스트 */
  --muted:#6b7280;     /* 보조 텍스트 */
  --border:rgba(255,255,255,0.08); /* 테두리 */
  --slide-w:1280px;
  --slide-h:800px;
}

## ❸ 텍스트 색상 규칙 (절대 위반 금지)

- html, body에 color:#e8eaf2 전역 지정
- 모든 텍스트 태그(p,span,div,li,td,th,h1~h6,strong,em,code,pre)에
  color:inherit 전역 적용 → 어두운 배경에서 검정 글자 방지
- .slide에 color:var(--text) 명시
- 인라인 style에 font-size 또는 font-weight가 있으면 반드시 color도 함께 지정
- 인라인 color 미지정 시 color:inherit 또는 color:rgba(232,234,242,N) 사용

## ❹ 공통 CSS 클래스 (반드시 이 이름으로 사용)

### 슬라이드 내부 래퍼
.si   → padding:36px 60px, flex column

### 슬라이드 헤더 요소
.sn   → 슬라이드 번호 (Bebas Neue, 13px, muted, letter-spacing:4px)
.stag → 카테고리 태그 배지 (12px, 대문자, letter-spacing:3px)
.sh   → 슬라이드 제목 (32px, font-weight:700)
.sd   → 슬라이드 설명 (14.5px, muted 58%)

### 태그 색상 클래스
.tg  → 초록 (accent)
.tp  → 보라 (purple)
.to  → 주황 (orange)
.tr  → 빨강 (red)
.tb  → 파랑 (blue)
.ty2 → 노랑

### 레이아웃 그리드
.c2  → 2단 그리드 (1fr 1fr, gap:20px, flex:1)
.c3  → 3단 그리드
.c4  → 4단 그리드
.col → flex column 컨테이너

### 카드
.card  → bg2 배경 카드 (border-radius:10px, padding:18px 20px)
.ct    → 카드 상단 2px 컬러 라인
.ct-g / .ct-p / .ct-o / .ct-r / .ct-b / .ct-y → 색상별 라인
.ch    → 카드 제목 (15px, bold)
.cp    → 카드 본문 (14px, muted 68%)

### 하이라이트 박스
.hb + .hg/.hp/.ho/.hr/.hb2 → 색상별 배경 박스
.ht → 하이라이트 박스 제목 (bold)

### 아키텍처 박스
.ab                  → 중앙 정렬 박스 (13px, bold)
.ab-sub              → 서브텍스트 (12px, opacity .7)
.ab-g/.ab-p/.ab-b/.ab-o/.ab-r/.ab-y → 색상별

### 수직 스텝 리스트
.vstep → flex column 컨테이너
.vsi   → 스텝 아이템 (gap:10px, padding:7px 0)
.vbadge → 스텝 번호 배지 (26×26px)
.vb-g/.vb-p/.vb-o/.vb-b/.vb-r → 색상별 배지
.vt h4 → 스텝 제목 (13.5px, bold, --text)
.vt p  → 스텝 설명 (12.5px, muted 58%)

### 비교 테이블
.tbl    → 전체 테이블
.tbl th → 헤더 (12px, muted, letter-spacing:1.5px)
.tbl td → 셀 (muted 82%)
.ck → 체크(accent), .cx → X(red), .cp2 → 부분(orange)

### 표지 전용
.kicker → 상단 키커 텍스트 (JetBrains Mono, accent, ::before 라인)
.badge  → 기술 스택 배지 (JetBrains Mono, muted)

### 기타
code    → 인라인 코드 (JetBrains Mono, bg:rgba(255,255,255,0.08))
.bignum → 큰 숫자 (Bebas Neue, 40px)
.bg-grid → 배경 격자 패턴 (accent 색 2.8% 투명도)
.glow    → 배경 빛 번짐 효과 (blur:110px)

## ❺ JS 컨트롤러 (동일 코드 사용)

const TOTAL = [슬라이드 수];
let cur = 0, anim = false;
// 점 네비게이션 자동 생성 (id="dn")
// go(nx, dir) 함수로 슬라이드 전환
// 클래스: .ai(앞으로 in) / .ao(앞으로 out) / .air(뒤로 in) / .aor(뒤로 out)
// setTimeout 400ms 후 정리
// 키보드: ArrowRight/Down = next, ArrowLeft/Up = prev
// rescale(): transform:scale()로 뷰포트 맞춤 (하단 48px 컨트롤 바 제외)

## ❻ HTML 슬라이드 구조 템플릿

<!-- 슬라이드 구조 -->
<div class="slide [active]" id="sN">
  <div class="bg-grid"></div>
  <!-- 선택: glow 효과 -->
  <div class="glow" style="width:400px;height:400px;top:-100px;right:-60px;
    background:radial-gradient(circle,rgba(0,212,160,0.15),transparent 70%);opacity:.35;"></div>

  <div class="si">
    <div class="sn">N / 전체수</div>
    <span class="stag [tg|tp|to|tr|tb]">카테고리</span>
    <div class="sh">슬라이드 제목</div>
    <div class="sd">한 줄 설명</div>

    <!-- 본문: c2, c3, c4, col 조합 -->
    <div class="c2">
      <div class="col">
        <!-- 카드, 하이라이트 박스, 스텝 리스트 등 -->
      </div>
      <div class="col">
        <!-- 아키 박스, 비교 테이블 등 -->
      </div>
    </div>
  </div>
</div>

## ❼ 표지 슬라이드 구조 (s0 고정)

- 왼쪽: kicker + 대제목(66px, 900) + 설명(17px, muted) + badge 목록
- 오른쪽: 고정 패널 (width:300px, bg:rgba(accent,0.04), border-left)
  → 슬라이드 인덱스 목록 표시
- glow 2개: 좌상단(accent) + 중앙하단(purple)

## ❽ 콘텐츠 밀도 규칙 (잘림 방지)

- 슬라이드 내부 총 높이: 800px - 72px(패딩) = 728px 이내
- .si 패딩: padding:36px 60px 고정
- .sh + .sd + .sn + .stag 헤더 높이: 약 96px
- 본문 가용 높이: 약 632px
- 카드 내부 padding: 14~18px (내용 많을 때 14px)
- vstep 아이템 padding: 7px 0
- gap: 5~10px (내용 많을 때 5px)
- 폰트 크기: 최소 12px (가독성 한계)
- 내용이 많은 슬라이드는 반드시 2단(c2) 분할 사용

## ❾ 금지 사항

- 슬라이드 내부 스크롤 금지 (overflow:hidden 유지)
- color 미지정 인라인 스타일 금지
- 배경색과 구분 안 되는 텍스트 색상 금지
- 슬라이드마다 다른 배경색 사용 금지 (--bg 통일)
- 외부 CSS 프레임워크 로드 금지 (Google Fonts 제외)
- 슬라이드 번호(.sn)와 TOTAL 불일치 금지

## ❿ 폰트

Google Fonts CDN 사용:
- Noto Sans KR: 300, 400, 500, 700, 900 (기본 본문)
- JetBrains Mono: 400, 700 (코드, 배지, 숫자)
- Bebas Neue (슬라이드 번호, bignum, 장식 숫자)

## ⓫ 편집기 호환성 (HTML PPT Editor 후편집 호환)

생성된 PPT를 https://muttul58-coder.github.io/HTML_PPT_EDIT/ 같은 web editor에서
드래그/리사이즈/텍스트 수정할 것을 가정한 추가 규칙. **반드시 적용**:

### A. 전역 box-sizing
:root 직후에 다음 줄을 반드시 포함:
```
*, *::before, *::after { box-sizing: border-box; }
```
→ 편집기에서 W/H 입력 값이 padding 포함 실제 박스 크기와 일치
→ 코드 블록 등을 리사이즈할 때 내용이 잘리거나 사라지는 현상 방지

### B. 인라인 스타일 최소화 (자식이 부모 스타일을 덮지 않게)
- `<code>`, `<strong>`, `<em>`, `<span>` 같은 인라인 태그에
  `line-height`, `font-size`, `letter-spacing`을 직접 인라인 style로 지정 금지
- 필요한 경우 클래스 또는 부모 요소에서만 지정
- ❌ `<code style="line-height:1.65">NetworkVariable</code>`
- ✅ `<code>NetworkVariable</code>` (부모의 line-height 상속)
→ 편집기에서 부모의 line-height/letter-spacing 변경이 자식까지 자연 적용

### C. 텍스트 + 인라인 태그 혼합 시 단일 부모로 유지
설명 한 문단은 한 요소 안에 모두 넣되, 강조는 인라인 태그로:
- ✅ `<p>호스트가 5~15초 간격으로 <code>SendHeartbeatPingAsync()</code> 호출. 30초 이상 미전송 시 로비 자동 삭제됨.</p>`
- ❌ `<span>호스트가 5~15초</span><span>간격으로</span><code>...</code>` (조각내지 말 것)
→ 편집기 우측 텍스트 패널에서 HTML 모드로 한 번에 줄바꿈/수정 가능

### D. 레이아웃은 정상 흐름(flex/grid) 유지
- 본문 콘텐츠에 `position: absolute`, `left`, `top` 직접 지정 금지
- 모든 카드/박스/텍스트는 `.c2`, `.col`, flex/grid의 자연 흐름에 맡길 것
- 절대 위치는 `.glow`, `.bg-grid`, 표지의 장식 패널 같은 고정 장식에만 사용
→ 편집기에서 클릭/드래그 시 필요한 요소만 자동으로 absolute 전환됨
→ 처음부터 absolute가 깔려 있으면 형제 요소가 reflow되며 레이아웃 깨짐

### E. 인라인 아이콘은 별도 요소로 감싸기
이모지/아이콘과 텍스트를 같은 flex 컨테이너 안에 넣을 때:
- ✅ `<div class="hb hr"><span class="icon">❤</span><div class="ht">Heartbeat</div></div>`
- ❌ `<div class="hb hr">❤ Heartbeat</div>` (텍스트 노드와 섞이면 편집기에서 아이콘만 선택 불가)
→ 아이콘만 따로 위치 조정/색상 변경 가능

### F. 슬라이드 ID 연속성
- 모든 슬라이드 `id="s0"`부터 1씩 증가 (s0, s1, s2 ...)
- 누락/중복/건너뜀 금지
- 첫 슬라이드만 `class="slide active"`, 나머지는 `class="slide"`
→ 편집기 좌측 슬라이드 목록 및 점 네비게이션 정상 동작

### G. 줄바꿈은 `<br>` 사용
문단 내 줄바꿈은 `<br>` 태그로:
- ✅ `<p>첫 줄<br>두번째 줄</p>`
- ❌ `<p>첫 줄</p><p>두번째 줄</p>` (분리하면 편집 단위가 나뉨)
→ 편집기에서 Enter 키로 자연스럽게 줄바꿈 가능

```

---

## 📌 주제 요청 예시

### 예시 1 — 기본
```
주제: Unity Netcode for GameObjects (NGO) 개념 정리
슬라이드 수: 8장
언어: 한국어
```

### 예시 2 — 슬라이드 구성 직접 지정
```
주제: Git 브랜치 전략 (Git Flow / GitHub Flow / Trunk-Based)
슬라이드 수: 9장
슬라이드 구성:
  1. 표지
  2. 버전 관리란?
  3. 브랜치 개념
  4. Git Flow 설명
  5. GitHub Flow 설명
  6. Trunk-Based Development
  7. 세 가지 비교
  8. 팀 규모별 선택 가이드
  9. 핵심 요약
언어: 한국어
```

### 예시 3 — 강조 색상 커스텀
```
주제: Docker & Kubernetes 기초
슬라이드 수: 10장
메인 강조색: #0ea5e9 (하늘색, Docker 브랜드)
언어: 한국어
```

> 강조색을 바꿀 때는 --accent 변수 값과
> .bg-grid의 rgba 색상, .kicker의 색상,
> .tg 클래스, .glow의 radial-gradient 색상을 함께 변경해야 합니다.

---

## 🎨 슬라이드 구성 패턴 레퍼런스

| 패턴 | 클래스 조합 | 적합한 내용 |
|------|------------|------------|
| 2단 카드 | `c2 > col > card*N` | 비교, 특징 나열 |
| 2단 코드+설명 | `c2 > (code-wrap + col)` | API 설명, 코드 분석 |
| 전체 스텝 | `vstep` | 순서가 중요한 흐름 |
| 2단 스텝+다이어그램 | `c2 > (vstep + arch)` | 설치·설정 가이드 |
| 3단 카드 | `c3 > card*3` | 3가지 개념 비교 |
| 비교 테이블 | `tbl` | 다항목 스펙 비교 |
| 흐름 다이어그램 | `ab + 화살표` | 아키텍처, 데이터 흐름 |
| 수치 강조 | `bignum + hb` | 요금, 제한, 통계 |
| 표지 | `kicker + 대제목 + badge` | 표지 고정 패턴 |

---

## ⚠️ 자주 발생하는 오류와 해결법

| 오류 | 원인 | 해결 |
|------|------|------|
| 글자가 검정으로 보임 | color 미지정 | 모든 태그에 color:inherit 전역 적용 |
| 슬라이드 하단 잘림 | 콘텐츠 높이 초과 | 패딩 축소, 폰트 축소, gap 축소 |
| 슬라이드 번호 불일치 | TOTAL 값 오류 | TOTAL = 실제 슬라이드 수와 일치 |
| 점 네비게이션 오작동 | s0~sN ID 누락 | 모든 슬라이드 id="s0"부터 순서대로 |
| 모바일에서 작게 보임 | rescale 미적용 | JS rescale() 함수 반드시 포함 |
| 카드 배경이 흰색 | --bg2 미적용 | background:var(--bg2) 명시 |
| 편집기 리사이즈 시 코드 잘림 | box-sizing:content-box 기본값 | `* { box-sizing: border-box; }` 전역 적용 (⓫-A) |
| 부모 line-height 변경 시 코드만 안 바뀜 | 자식 `<code>`에 인라인 line-height 직접 지정 | 자식 인라인 스타일 제거, 부모 상속 (⓫-B) |
| 인라인 요소 위치 변경 시 형제가 reflow | 처음부터 position:absolute 사용 | flex/grid 정상 흐름 사용, 절대위치는 장식만 (⓫-D) |
| 아이콘만 따로 선택/이동 불가 | 텍스트 노드와 아이콘이 같은 요소 안 혼재 | 아이콘을 별도 `<span>`으로 감싸기 (⓫-E) |
| 한 문단을 편집기에서 한 번에 수정 불가 | 한 문장을 여러 `<p>`/`<div>`로 분할 | 단일 부모 요소 안에 인라인 태그로 강조 (⓫-C) |
