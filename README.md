# rnd-reference-deck-style

**English** · [한국어 README](README.ko.md)

### The design rules behind 283 Korean government briefing decks, packed into a Claude skill.

> Tell Claude your topic. It builds a clean 16:9 deck using **13 proven layouts and one consistent design system**,
> ready for client pitches, internal reports, or your portfolio.

**The references: 72 hand-picked pages from Korea's annual government R&D briefings, 2020–2026**

![Wall of reference slides](docs/reference-wall.jpg)

**What the skill produces: a sample deck built only from the rules (fictional internal proposal, in Korean)**

![Six example slides](docs/example-overview.jpg)

[Browse all 72 reference layouts](skills/rnd-reference-deck-style/references/README.md) · [Example deck (HTML)](examples/sample-deck.html) · [Read SKILL.md](skills/rnd-reference-deck-style/SKILL.md)

---

## Why government decks?

Every January, dozens of Korean ministries and agencies present their R&D programs at a joint briefing. Seven years of those decks add up to hundreds of design attempts at the same job: explaining something complex to a large audience, fast. This skill studies them for **design only, never content**.

- All **283 PDFs (about 17,800 pages)** were catalogued, with aspect ratio, dominant color, and duplicates measured across every file.
- **About 20 representative decks were reviewed by eye** to define 6 style families and the design rules.
- **72 of the best pages** were sorted into 13 layout types.

A few findings: about 85% of the 225 slide decks use a single navy/blue palette, and 16:9 went from 7% of decks in 2020 to 48% in 2026.

## What the skill teaches Claude

| | |
| --- | --- |
| 🎨 **Color** | Navy `#1D3466` · Blue `#2A70BE` · Card `#EAF1FA` · Accent red `#E1614F` (numbers and keywords only) |
| 🔠 **Type** | Bold sans headings, sans body (e.g. Pretendard). Cover 40 · Section 36 · Title bar 24 · Key message 20 · Body 14–16 pt |
| 📐 **Grid** | 16:9, 80px side margins, 110px title bar. Title bar → one-line key message → 2–3 columns → source and page number |
| 🧩 **13 layouts** | Cover · Agenda · Section divider · Key message · Stat cards · As-Is/To-Be · Strategy cards · Diagram · Timeline · Map · Table · Photo · Closing |
| 🎭 **6 style families** | Navy policy · Isometric illustration · Dark photo · Brand color · Table-heavy · Print booklet ([details, in Korean](skills/rnd-reference-deck-style/references/style-families.md)) |
| 🚫 **Avoid** | Two tables on one slide, highlighter overload, mixing illustrations with stock photos, 4:3 |

## Install

### Claude Code

```bash
git clone https://github.com/jungom3123/rnd-reference-deck-style.git
mkdir -p ~/.claude/skills
cp -r rnd-reference-deck-style/skills/rnd-reference-deck-style ~/.claude/skills/
```

To use it in one project only, copy it into that project's `.claude/skills/` instead.

### Claude app (claude.ai)

```bash
cd rnd-reference-deck-style/skills
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
rnd-reference-deck-style/
├── skills/rnd-reference-deck-style/   ← the skill itself
│   ├── SKILL.md                       design rules and workflow
│   └── references/
│       ├── README.md                  layout gallery (72 pages, with sources)
│       ├── style-families.md          the 6 style families
│       └── layouts/01_표지 … 13_마무리/
├── examples/
│   ├── sample-deck.html               6-slide example built from the rules
│   └── images/
├── docs/                              images for this README
├── LICENSE                            MIT (reference images excluded)
└── NOTICE.md                          sources and rights for reference images
```

## Make it yours

Fork the repo and change the four colors and the font under **기본 디자인 규칙** (base design rules) in `SKILL.md`. That is all it takes to get a skill for your own brand. If you collect your own references, keep the `references/layouts/` folder structure and swap the images.

## License and sources

- `SKILL.md`, the docs, and `examples/` are [MIT licensed](LICENSE). The example slides were made from the rules alone, with no reference images.
- The 72 images in `references/layouts/` are **not covered by MIT**. Rights stay with the issuing agencies and original creators. They are here for design study only. See [NOTICE.md](NOTICE.md) for sources and takedown requests.
