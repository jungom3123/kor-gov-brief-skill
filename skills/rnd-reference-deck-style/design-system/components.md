# Brief Deck 컴포넌트

`brief-deck.css`의 클래스다. 글자 크기는 `tokens.css`의 `t-*` 클래스로 준다. 미리보기는 HTML 슬라이드(`.bd-slide`, 1920×1080) 기준이다.

## Slide

1920×1080 슬라이드 한 장의 틀로, 제목·본문·풋터 자리를 정한다.

### 넣는 것

`<section class="bd-slide">` 안에 TitleBar, `.bd-body`(좌우 `space-margin-x`, 블록 사이 `space-block`), `.bd-foot`(출처 좌하단, 쪽번호 알약 우하단, 바닥에서 30px)를 둔다. 표지·간지·마무리는 `data-theme="dark"`를 준 슬라이드에 만든다.

### 할 것 / 하지 않을 것

- 할 것: 제목 아래 핵심 문장 1줄을 먼저 둔다. 본문 덩이는 2~4개.
- 하지 않을 것: 한 장에 표 2개, 차트 3개 이상. 풋터에 22px 이상 글자.

### 마크업

```html
<section class="bd-slide">
  <header class="bd-titlebar bd-titlebar--plain">…</header>
  <div class="bd-body">…</div>
  <footer class="bd-foot"><span class="t-caption">출처: …</span><span class="t-caption bd-foot__page">4</span></footer>
</section>
```

## TitleBar

페이지 제목 바로, 전폭·짧은 사선·바 없음 세 가지 중 덱 전체에서 하나만 쓴다.

### 넣는 것

번호(`.bd-titlebar__no`, 2자리), 작은 장 표시(`t-caption`), 제목(`t-title`). 전폭 바는 높이 `titlebar-h`(130), 짧은 사선 바는 폭 680·높이 100에 `sky` 사선. 바 없음은 `heading` 제목 + `primary` 밑줄로 공간이 넓어 도식·차트 페이지에 맞다.

### 할 것 / 하지 않을 것

- 할 것: 제목은 한 줄, 20자 안팎.
- 하지 않을 것: 한 덱에서 바 종류 섞기, 제목 바에 문장형 핵심 메시지 넣기.

### 마크업

```html
<header class="bd-titlebar">
  <span class="bd-titlebar__no">01</span>
  <div><p class="t-caption bd-titlebar__kicker">2027 고객 경험 혁신 제안</p><h2 class="t-title">현황 진단</h2></div>
</header>
```

## KeyMessage

제목 아래 핵심 문장 1줄로, 그 장의 결론을 먼저 말한다.

### 넣는 것

라벨(`.bd-key__label`, 2~4자)과 문장(`t-headline`). 핵심어 2~4개만 `.bd-em`. 전폭 밴드형(`.bd-key--band`)은 장 끝 요약이나 카드 위 머리말에 쓰고 밴드 안 핵심어는 `accent-inverse`가 된다.

### 할 것 / 하지 않을 것

- 할 것: 문장은 1~2줄, 숫자를 넣는다.
- 하지 않을 것: 문장 전체 색칠, 한 장에 핵심 문장 두 개.

### 마크업

```html
<div class="bd-key"><span class="bd-key__label t-card-head">핵심</span><p class="t-headline">첫 90일 이탈의 <b class="bd-em">68%</b>가 설정 단계</p></div>
```

## Pill

둥근 알약 라벨로, 섹션 라벨·카드 헤더·차트 제목·날짜에 쓴다.

### 넣는 것

글자(`t-card-head`)만 받는다. 높이 `pill-h`(64), 모서리 `radius-pill`. 변형: 기본(`primary`), `--soft`(`surface-tint`), `--line`(테두리), `--accent`(신규·강조).

### 할 것 / 하지 않을 것

- 할 것: 한 장 안에서 같은 역할의 알약은 같은 변형.
- 하지 않을 것: 알약 안에 두 줄, 문장.

### 마크업

```html
<span class="bd-pill t-card-head">추진 배경</span>
```

## BigNumber

큰 숫자와 1/3 크기 단위로, 그 장의 가장 중요한 값을 보여 준다.

### 넣는 것

숫자(`t-number`, 60~150px), 단위(`.bd-num__unit`), 선택적으로 증감(`.bd-up` ▲) 또는 전→후(`.bd-before` → `.bd-num--accent`).

### 할 것 / 하지 않을 것

- 할 것: 한 장에 큰 숫자 1~4개. 소수점은 한 자리.
- 하지 않을 것: 단위를 숫자와 같은 크기로, 증감을 `signal` 외 색으로.

### 마크업

```html
<span class="t-number bd-num">92<span class="bd-num__unit">%</span></span> <b class="t-headline bd-up">▲ 7%p</b>
```

## ConclusionBand

페이지 하단의 결론 1줄로, 전폭 네이비 띠 또는 대괄호 두 형태가 있다.

### 넣는 것

문장 1줄(`t-headline`), 핵심어 `.bd-em`. 띠는 높이 `band-h`(200)로 슬라이드 바닥에 붙인다. 대괄호(`.bd-bracket`)는 본문 중간에도 쓸 수 있다.

### 할 것 / 하지 않을 것

- 할 것: 근거를 다 보인 뒤 마지막에 둔다.
- 하지 않을 것: 결론 띠와 대괄호를 한 장에 같이 쓰기.

### 마크업

```html
<div class="bd-band"><p class="t-headline">투자 회수 기간 <b class="bd-em">14개월</b></p></div>
```

## StatCard

색 헤더와 큰 숫자로 된 수치 카드로, 3~5개를 한 줄에 놓는다.

### 넣는 것

헤더(`t-card-head`, 8자 이내), 숫자 + 단위, 설명 1줄 또는 전→후 + 증가율 배지(`.bd-badge`). `.bd-cards`에 `--cols`로 열 수를 준다. 4열 이상은 `.bd-cards--dense`.

### 할 것 / 하지 않을 것

- 할 것: 카드 높이·안 여백을 같게, 숫자 크기도 같게.
- 하지 않을 것: 카드마다 다른 헤더 색(분류가 아니면), 설명 3줄 이상.

### 마크업

```html
<div class="bd-cards" style="--cols:4">
  <div class="bd-stat"><div class="bd-stat__head t-card-head">재계약률</div>
    <div class="bd-stat__body"><span class="t-number bd-num">92<span class="bd-num__unit">%</span></span></div></div>
</div>
```

## TaskCard

헤더 알약이 위에 걸친 카드로, 전략 과제·서비스 구성·강점을 3~4개 나란히 보여 준다.

### 넣는 것

헤더(Pill, 카드 위 32px 걸침), 불릿 2~4개(`.bd-list`, `t-body`, 핵심어 `.bd-em`), 선택적 ※ 보충(`.bd-note`). 분류색은 `--c1`~`--c4`. 2행이면 2×2 또는 3+2 중앙 정렬.

### 할 것 / 하지 않을 것

- 할 것: 카드 위에 KeyMessage 한 줄을 둔다. 불릿은 한 줄씩.
- 하지 않을 것: 카드 5개 초과, 불릿 6줄 초과.

### 마크업

```html
<div class="bd-task bd-task--c1"><span class="bd-pill bd-task__head t-card-head">빠른 시작</span>
  <ul class="bd-list t-body"><li><b class="bd-em">설정 마법사</b> 도입</li></ul></div>
```

## BeforeAfter

현재(회색)와 개선 후(주색)를 좌우로 비교한다.

### 넣는 것

두 쪽의 라벨(As-Is/To-Be, 현행/개선, 현재/미래)과 같은 수의 불릿. 가운데 화살표(`.bd-ba__arrow`, `accent`). 개선 쪽 핵심어만 `.bd-em`.

### 할 것 / 하지 않을 것

- 할 것: 양쪽 항목을 같은 순서로 짝지운다.
- 하지 않을 것: 전(前) 쪽에 색 강조, 세 쪽 이상 비교.

### 마크업

```html
<div class="bd-ba">
  <div class="bd-ba__side bd-ba__side--before"><div class="bd-ba__head t-card-head">As-Is</div><div class="bd-ba__body">…</div></div>
  <div class="bd-ba__arrow"></div>
  <div class="bd-ba__side bd-ba__side--after">…</div>
</div>
```

## BarChart

전(회색)·후(블루) 쌍 막대 차트로, 기간이나 항목별 변화를 보여 준다.

### 넣는 것

막대 높이(px, 값에 비례), 값 라벨(전부 표기, `t-chart`), x축 라벨, 범례, 단위(우상단 `t-caption`). 증가율은 `.bd-up` ▲. 그릴 영역 높이 `--plot-h`, 격자 간격 `--grid`. 실제 차트 도구로 그릴 때도 색·라벨 규칙은 같다.

### 할 것 / 하지 않을 것

- 할 것: 계열 2~3개, 마지막 해만 주색인 추세도 좋다.
- 하지 않을 것: 4계열 초과, 세로 격자, 3D·그림자.

### 마크업

```html
<div class="bd-bar bd-bar--after" style="height:312px"><span class="t-chart">78</span></div>
```

## DataTable

한 장에 하나만 두는 표로, 주색 헤더와 가로 괘선, 합계 행을 쓴다.

### 넣는 것

헤더 행, 본문 행(숫자 열 `.num` 오른쪽 정렬), 합계 행(`tr.bd-total`, `surface-total`), 신규 표시(`.bd-new`). 위에 요약 문장 1줄(`t-card-head` + `.bd-em`), 단위는 우상단.

### 할 것 / 하지 않을 것

- 할 것: 12행 넘으면 2단, 20행 넘으면 두 장으로.
- 하지 않을 것: 세로 괘선, 줄마다 다른 색, 한 장에 표 두 개.

### 마크업

```html
<table class="bd-table t-table"><thead><tr><th>플랜</th><th class="num">매출</th></tr></thead>
<tbody><tr class="bd-total"><td>합계</td><td class="num bd-up">+81</td></tr></tbody></table>
```

## ProcessSteps

가로 쉐브론 단계로, 3~8단계 진행 방식을 보여 준다.

### 넣는 것

단계 이름(`t-card-head`, 6자 이내), 선택적으로 아래 설명 박스(기간·설명). 단계는 `primary`와 `accent`가 번갈아 나온다.

### 할 것 / 하지 않을 것

- 할 것: 단계 수와 설명 박스 수를 같게.
- 하지 않을 것: 단계 이름 두 줄, 8단계 초과.

### 마크업

```html
<div class="bd-steps t-card-head"><div class="bd-step">진단</div><div class="bd-step">설계</div></div>
```

## Timeline

날짜 알약이 가로 축에 놓인 일정표로, 연혁·추진 일정에 쓴다.

### 넣는 것

날짜(알약 안 `2027. 1Q` 형식), 제목(`t-card-head`), 설명 1줄. 지난 일정은 `.bd-tl__item--done`(회색). 열 수는 `--cols`.

### 할 것 / 하지 않을 것

- 할 것: 날짜 형식을 한 덱에서 통일.
- 하지 않을 것: 한 줄에 6개 초과. 그 이상은 월별 표나 2행으로.

### 마크업

```html
<div class="bd-tl" style="--cols:4"><div class="bd-tl__item"><span class="bd-pill bd-tl__date">2027. 1Q</span><p class="t-card-head bd-heading">마법사 출시</p></div></div>
```
