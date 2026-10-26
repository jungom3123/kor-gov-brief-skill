# rnd-reference-deck-style

### 정부 발표자료 283개에서 뽑아낸 "잘 만든 슬라이드"의 규칙을, Claude가 바로 쓰는 스킬로.

> 주제만 말하면 Claude가 **검증된 레이아웃 13종과 디자인 규칙**으로 16:9 발표자료를 만듭니다.
> 고객사 제안, 사내 보고, 포트폴리오 어디에나 씁니다.

**레퍼런스 (2020~2026 정부 R&D 부처합동설명회 72장 선별)**

![레퍼런스 사례 모음](docs/reference-wall.jpg)

**이 스킬로 만든 예시 (가상의 사내 보고 「문서 업무 자동화 도입 제안」)**

![예시 슬라이드 6장](docs/example-overview.jpg)

[레이아웃 갤러리 72장 보기](skills/rnd-reference-deck-style/references/README.md) · [예시 HTML 원본](examples/sample-deck.html) · [SKILL.md 읽기](skills/rnd-reference-deck-style/SKILL.md)

---

## 왜 정부 발표자료인가

한국 정부 부처는 매년 초 수십 개 기관이 같은 자리에서 R&D 설명회를 엽니다. 7년 치를 모으면 같은 목적(복잡한 내용을 많은 사람에게 짧게 설명)을 두고 수백 가지 디자인 시도가 쌓여 있는 셈입니다. 이 스킬은 그 자료를 **내용이 아니라 디자인만** 뜯어본 결과입니다.

- **283개 PDF, 약 17,800쪽**을 모두 목록화하고 화면비·주색·중복을 집계했습니다.
- 그중 **대표 자료 20여 개를 직접 검토**해 스타일 계열 6종과 디자인 규칙을 정했습니다.
- 유형별로 **좋은 페이지 72장**을 골라 13개 레이아웃으로 묶었습니다.

몇 가지 발견: 슬라이드 225개 중 약 85%가 네이비·블루 한 가지 색 체계를 쓰고, 16:9 비율은 2020년 7%에서 2026년 48%로 늘었습니다.

## 스킬이 Claude에게 알려 주는 것

| | 내용 |
| --- | --- |
| 🎨 **색** | 네이비 `#1D3466` · 블루 `#2A70BE` · 카드 `#EAF1FA` · 포인트 레드 `#E1614F`(숫자·키워드에만) |
| 🔠 **글자** | 굵은 고딕 제목 + 고딕 본문(Pretendard 등). 표지 40 · 간지 36 · 제목 바 24 · 핵심 메시지 20 · 본문 14~16pt |
| 📐 **틀** | 16:9, 좌우 여백 80px, 제목 바 110px. 제목 바 → 핵심 문장 1줄 → 2~3단 → 출처·쪽번호 |
| 🧩 **레이아웃 13종** | 표지 · 목차 · 간지 · 핵심 메시지 · 수치 카드 · As-Is/To-Be · 카드형 과제 · 구조 도식 · 타임라인 · 지도 · 표 · 사진 · 마무리 |
| 🎭 **스타일 6계열** | 네이비 정책형 · 아이소메트릭 일러스트형 · 다크 사진형 · 컬러 테마형 · 표 중심형 · 인쇄 자료집 ([설명](skills/rnd-reference-deck-style/references/style-families.md)) |
| 🚫 **피할 것** | 한 장에 표 두 개, 형광 강조 남발, 일러스트와 스톡사진 섞기, 4:3 비율 |

## 설치

### Claude Code

```bash
git clone https://github.com/jungom3123/rnd-reference-deck-style.git
mkdir -p ~/.claude/skills
cp -r rnd-reference-deck-style/skills/rnd-reference-deck-style ~/.claude/skills/
```

한 프로젝트에서만 쓰려면 `~/.claude/skills/` 대신 그 프로젝트의 `.claude/skills/`에 복사하세요.

### Claude 앱 (claude.ai)

```bash
cd rnd-reference-deck-style/skills
zip -r rnd-reference-deck-style.zip rnd-reference-deck-style
```

만든 ZIP을 Claude 설정의 스킬(Skills) 메뉴에서 업로드합니다.

## 사용 예시

스킬이 설치되어 있으면 이렇게 말하기만 하면 됩니다.

```text
신규 고객사에 데이터 분석 서비스를 제안하는 10장짜리 발표자료를 만들어 줘.
고객사 브랜드 색은 #0F9D58이야.
```

```text
이번 분기 팀 성과를 경영진에게 보고하는 자료를 만들어 줘.
핵심 수치는 매출 18% 증가, 신규 고객 42곳, 이탈률 3.1%야.
```

```text
내 포트폴리오용으로 프로젝트 3개를 소개하는 슬라이드를 아이소메트릭 일러스트형으로 구성해 줘.
```

Claude는 용도에 맞는 스타일 계열을 고르고, 슬라이드마다 레이아웃 유형을 정한 뒤, 갤러리 이미지를 열어 구도를 참고해서 만듭니다.

## 레포 구성

```text
rnd-reference-deck-style/
├── skills/rnd-reference-deck-style/   ← 이 폴더가 스킬 본체
│   ├── SKILL.md                       디자인 규칙과 작업 순서
│   └── references/
│       ├── README.md                  레이아웃 갤러리 (72장, 출처 표기)
│       ├── style-families.md          스타일 계열 6종
│       └── layouts/01_표지 … 13_마무리/
├── examples/
│   ├── sample-deck.html               규칙만으로 만든 예시 6장 (HTML)
│   └── images/                        예시 슬라이드 이미지
├── docs/                              README용 이미지
├── LICENSE                            MIT (레퍼런스 이미지 제외)
└── NOTICE.md                          레퍼런스 이미지 출처와 권리 안내
```

## 내 스타일로 바꿔 쓰기

이 레포를 포크한 뒤 `SKILL.md`의 **기본 디자인 규칙**에서 색 4개와 글꼴만 바꾸면 내 브랜드용 스킬이 됩니다. 다른 레퍼런스를 모았다면 `references/layouts/` 폴더 구조를 그대로 두고 이미지만 바꿔 넣으세요.

## 라이선스와 출처

- `SKILL.md`, 문서, `examples/`는 [MIT 라이선스](LICENSE)입니다. 예시 슬라이드는 레퍼런스 이미지를 쓰지 않고 규칙만으로 새로 만들었습니다.
- `references/layouts/`의 이미지 72장은 **MIT 대상이 아니며** 각 기관에 권리가 있습니다. 디자인 공부용으로만 두었고, 자세한 내용과 삭제 요청 방법은 [NOTICE.md](NOTICE.md)에 있습니다.

---

## English summary

**rnd-reference-deck-style** is a Claude skill that turns design patterns from 283 Korean government R&D briefing decks (2020–2026) into reusable rules for 16:9 business presentations.

- **What it gives Claude:** a navy/blue color system, type scale, grid and margins, 13 layout types (cover, agenda, section divider, key number, stat cards, as-is/to-be, strategy cards, diagram, timeline, map, table, photo, closing), and 6 style families mapped to use cases.
- **What's included:** `SKILL.md`, a gallery of 72 hand-picked reference pages with sources, and an original 6-slide example built only from the rules.
- **Install (Claude Code):** copy `skills/rnd-reference-deck-style` into `~/.claude/skills/`. For the Claude app, zip that folder and upload it as a skill.
- **License:** MIT for the skill, docs and examples. The 72 reference images are excluded; rights stay with the issuing agencies (see [NOTICE.md](NOTICE.md)).
