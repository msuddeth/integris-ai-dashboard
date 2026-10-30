# Integris AI View

How AI assistants read **integrisit.com**: a review of 24 top-level pages (everything in the main navigation and footer), captured October 29, 2026 and last rescanned at 3:04 pm. The /blog/ directory and the events and trust-center subdomains are excluded.

Each page was read with an AI web reader, the same fetch-and-summarize approach ChatGPT, Claude, Perplexity and Google AI Overviews use. The report shows what the AI took away, the claims it picked up, and the issues it flagged.

## View the site

Open `index.html` in a browser. Everything is static: no server and no build step needed to view it.

## Hand-off downloads

Every page has a **Download as HTML** button (header and footer), and the overview also offers **Download full site (.zip)**:

- `downloads/integris-ai-view.html` — the whole report in one self-contained file: the overview, all 24 page reports and the Integris AI Page example, with styling inlined and every link pointing within the file. It works offline with no GitHub needed; fonts load from Google when online and fall back to system fonts when not.
- `downloads/integris-ai-view-site.zip` — the full multi-page site plus the markdown sources.

## Two reports

| Site | Folder | Live |
|---|---|---|
| **Integris** (integrisit.com, 24 pages) | repo root | https://crlkysr.github.io/integris_AI_recommendations/ |
| **First Focus** (firstfocus.com.au, 52 pages) | `firstfocus/` | https://crlkysr.github.io/integris_AI_recommendations/firstfocus/ |

Each links to the other ("See how First Focus compares" / "See how Integris compares"), and both carry the same **Scorecard** (`pages/scorecard.html`): ten criteria worth 10 points each (100 total), Integris 34 and First Focus 56.

## Repository layout

| Path | What it is |
|---|---|
| `index.html` | Overview: key findings, priority fixes, and cards for every page |
| `pages/` | One HTML report per page |
| `pages/seller-cards.html` | **Seller cards for AI buying agents** — examples, Integris company and service cards with gaps marked, site structure, and the discovery-form fix (source: `src/seller-cards.html`) |
| `pages/changelog.html` | **Change log** — every rescan and report update, newest first (source: `content/changelog.md`) |
| `pages/ai-page-example.html` | **Integris AI Page example** — a draft AI info page modeled on First Focus's, built from public facts, with a Show gaps toggle |
| `src/ai-page-example.html` | Editable source for the AI page example |
| `content/` | The source markdown reports (`00-README-summary.md` is the overview) |
| `assets/site.css` | Compiled Tailwind CSS |
| `src/input.css` | Tailwind source with the component styles |
| `tailwind.config.js` | Integris palette and fonts |
| `scripts/build.py` | Turns a site's `content/*.md` and `site.json` into HTML pages |
| `site.json`, `firstfocus/site.json` | Per-site config: brand colours, fonts, navigation, stats, downloads |
| `shared/scorecard.html` | The scorecard page, built into both sites |
| `firstfocus/` | The First Focus report (same layout: `content/`, `src/`, `pages/`, `downloads/`) |

## Design

Colors were sampled from integrisit.com:

| Token | Hex | Used for |
|---|---|---|
| `integris-red` | `#CE0019` | Primary buttons, links, accents |
| `integris-purple` | `#532C99` | Secondary buttons |
| `integris-plum` | `#3A2742` | Dark sections, table headers |
| `integris-orange` | `#F18614` | Sparing highlights |
| `integris-gray` | `#666666` | Muted text |

Integris uses Neue Haas Grotesk, a licensed Adobe font, so this site uses Inter and Inter Tight from Google Fonts as the closest free match.

## Rebuilding after editing the markdown

```bash
pip install markdown
python3 scripts/build.py              # Integris
python3 scripts/build.py firstfocus   # First Focus
# Tailwind standalone CLI v3: https://github.com/tailwindlabs/tailwindcss/releases/tag/v3.4.17
./tailwindcss -i src/input.css -o assets/site.css --minify && cp assets/site.css firstfocus/assets/site.css
python3 scripts/bundle.py && python3 scripts/bundle.py firstfocus   # rebuild both sites' downloads/
```

## Hosting note

Published with GitHub Pages from the `main` branch. Every page carries `noindex, nofollow, noai` tags so search engines and AI crawlers won't list or reuse it.
