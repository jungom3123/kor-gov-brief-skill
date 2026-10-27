# kor-gov-brief-skill

**English** · [한국어 README](README.ko.md)

### The design rules behind 283 Korean government briefing decks, packed into a Claude skill.

> Tell Claude your topic. It builds a clean 16:9 deck using **16 proven layouts and one consistent design system**,
> ready for client pitches, internal reports, or your portfolio.

**The references: 100 hand-picked pages from 32 decks of Korea's annual government R&D briefings, 2020–2026**

![Wall of reference slides](docs/reference-wall.jpg)

**What the skill produces: a sample deck built only from the rules (fictional internal proposal, in Korean)**

![Nine example slides](docs/example-overview.jpg)

[Browse all 100 reference layouts](skills/rnd-reference-deck-style/references/README.md) · [Example deck (HTML)](examples/sample-deck.html) · [Design system + PowerPoint template](skills/rnd-reference-deck-style/design-system/README.md) · [Read SKILL.md](skills/rnd-reference-deck-style/SKILL.md)

---

## Why government decks?

Every January, dozens of Korean ministries and agencies present their R&D programs at a joint briefing. Seven years of those decks add up to hundreds of design attempts at the same job: explaining something complex to a large audience, fast. This skill studies them for **design only, never content**.

- All **283 PDFs (about 17,800 pages)** were catalogued, with aspect ratio, dominant color, and duplicates measured across every file.
- **53 decks were scanned as contact sheets, and 32 of them were reviewed page by page** to define 6 style families.
- **100 of the best pages** were rendered at 1800px, measured one by one (composition, margins, colors, type sizes, charts, tables), and sorted into 16 layout types. Every rule in the skill comes from those measurements.

A few findings: about 85% of the 225 slide decks use a single navy/blue palette, and 16:9 went from 7% of decks in 2020 to 48% in 2026.

## What the skill teaches Claude

| | |
| --- | --- |
| 🎨 **Color** | Navy `#1D3466` · Blue `#2A70BE` · Sky `#8FC1F2` · Card `#EAF1FA` · Gray `#8A94A6` for "before" · Accent red `#E1614F` (numbers and keywords only). Gray → blue for before/after, one same-saturation 4-color set for categories |
| 🔠 **Type** | Bold sans headings, sans body (e.g. Pretendard). At 1920×1080: cover 80–110px · section number 90–250px · title bar 56–60px · headline 44–60px · big numbers 60–150px · body 28–36px · sources 18–22px (÷2 for pt in pptx) |
| 📐 **Grid** | 16:9, 80px side margins, 60px top and bottom. Three title-bar variants (full navy bar 110–150px, short left bar, no bar) → one-line key message → 2–4 blocks → source and page number. Cards 30–40px apart, 12–20px radius |
| 🧩 **16 layouts** | Cover · Agenda · Section divider · Key message · Stat cards · Chart · As-Is/To-Be · Strategy cards · Diagram · Process · Timeline · Map · Table · Program detail · Photo and icon cards · Closing, each with measured sizes and 3–10 reference pages |
| 🎭 **6 style families** | Navy policy · Isometric illustration · Dark photo · Brand color · Table-heavy · Print booklet ([details, in Korean](skills/rnd-reference-deck-style/references/style-families.md)) |
| 🚫 **Avoid** | Two tables on one slide, highlighter overload, mixing illustrations with stock photos, 4:3, body text under 22px |
| 🔁 **Shared grammar** | One message per slide · color only the keywords · big number, small unit · gray-before/blue-after · pill labels · navy conclusion band · one decoration style per deck |

## Install

### Claude Code

```bash
git clone https://github.com/jungom3123/kor-gov-brief-skill.git
mkdir -p ~/.claude/skills
cp -r kor-gov-brief-skill/skills/rnd-reference-deck-style ~/.claude/skills/
```

To use it in one project only, copy it into that project's `.claude/skills/` instead.

### Claude app (claude.ai)

```bash
cd kor-gov-brief-skill/skills
zip -r rnd-reference-deck-style.zip rnd-reference-deck-style
```

Upload the ZIP from the Skills section of Claude's settings.

## Try it

Once installed, just ask:

```text
Make a 10-slide deck pitching our data analytics service to a new client.
Their brand color is #0F9D58.
```

```text
Build a quarterly results report for the leadership team.
Key numbers: revenue +18%, 42 new customers, churn 3.1%.
```

```text
Lay out three portfolio projects in the isometric illustration style.
```

Claude picks a style family for the use case, assigns a layout type to each slide, opens the matching reference images for composition, and then builds the deck. The skill itself is written in Korean, and Claude follows it in any language.

## What's in the repo

```text
kor-gov-brief-skill/
├── skills/rnd-reference-deck-style/   ← the skill itself
│   ├── SKILL.md                       design rules and workflow
│   ├── references/
│   │   ├── README.md                  layout gallery (100 pages, with sources and per-type rules)
│   │   ├── style-families.md          the 6 style families
│   │   └── layouts/01_표지 … 16_마무리/
│   └── design-system/                 tokens, slide CSS kit, component docs, PowerPoint template
├── examples/
│   ├── sample-deck.html               9-slide example built from the rules
│   └── images/
├── docs/                              images for this README
├── LICENSE                            MIT (reference images excluded)
└── NOTICE.md                          sources and rights for reference images
```

## Make it yours

Fork the repo and change the colors and the font under **2. 기본 틀** (base frame) in `SKILL.md`. That is all it takes to get a skill for your own brand. If you collect your own references, keep the `references/layouts/` folder structure and swap the images.

## License and sources

- `SKILL.md`, the docs, `design-system/`, and `examples/` are [MIT licensed](LICENSE). The example slides were made from the rules alone, with no reference images.
- The 100 images in `references/layouts/` are **not covered by MIT**. Rights stay with the issuing agencies and original creators. They are here for design study only. See [NOTICE.md](NOTICE.md) for sources and takedown requests.
