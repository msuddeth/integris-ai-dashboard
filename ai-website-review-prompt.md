# Prompt: "How AI sees our website" — audit, report site, seller cards and scorecard

Copy everything below the line into an AI assistant that can browse the web, run code and create files (for example Claude with tools enabled). Replace every `{{PLACEHOLDER}}` first. Delete any optional phase you don't need.

---

You are going to audit how AI assistants and AI buying agents read a company's website, then turn the findings into a polished, shareable report site. Work in phases, show me results as you go, and ask me before anything that publishes, deletes or can't be undone.

## Inputs

- **Company:** {{COMPANY_NAME}}
- **Website:** {{https://www.example.com}}
- **Exclude:** {{/blog/ and individual articles; any subdomains}}
- **Contact form platform:** {{HubSpot / Gravity Forms / Marketo / unknown}}
- **Model AI info page to compare against (optional):** {{https://www.firstfocus.com.au/ai-info-page/}}
- **Second company to compare (optional):** {{COMPARE_COMPANY}} at {{https://compare.example.com}}
- **Where to publish (optional):** GitHub repo {{owner/repo}}; custom subdomain {{ai.example.com}} on {{Cloudflare / other DNS}}
- **Audience:** internal stakeholders at {{COMPANY_NAME}}

## Ground rules

- **Use only public information.** Never invent facts. Every fact on every page must trace back to a page you read; say which page.
- **Read pages the way AI does.** Use a fetch-and-summarize web reader, not a full browser, for the page reports. Note that it doesn't run JavaScript, play video or render embedded widgets. Anything that only appears that way counts as "missing to AI," and the report should say so.
- **Paraphrase.** Don't reproduce long passages from the site or from third-party sources.
- **Don't act on sites.** Don't submit forms, accept cookie banners or sign in anywhere. Read only.
- **Verify before claiming.** Before reporting something as fixed or broken, check the live page. Bypass caches, and remember redirect rules may not match URLs with query strings added.
- **Flag bias.** Where cited research comes from vendors that sell AI-search services, say so.
- **Warn before publishing.** A public site is visible to competitors. Ask whether the repo and site should be public before publishing.

## Phase 1 — Read every top-level page

1. List every page in the main navigation, mega-menus and footer. Exclude the paths I listed and show me the list before reading.
2. Read each page with the web reader. Save one markdown file per page, numbered by section (`01-home.md`, `02-…`), in exactly this structure:

```
# {Page name} — How AI reads this page

**URL:** {url}
**Captured:** {date}, through an AI web reader

> Everything below is the AI's own reading of the page as served.

## Metadata
| Field | Value |
|---|---|
(Title tag, og:title, Meta description, Canonical, Robots, Last modified)

## Heading structure
- **H1:** …
- (main H2s in order)

## What the AI takes away
(2–4 sentences: what the company offers here and for whom)

## Claims and proof points the AI picked up
- (statistics, prices, SLAs, onboarding times, certifications, awards, named testimonials — as stated)

## Calls to action and links
- (and whether any form fields are readable)

## Issues the AI flagged
- **Short label:** explanation (placeholder or lorem ipsum text, typos, contradictions, metadata problems,
  canonical/robots problems, content only in images/JS/video, unsourced claims, missing pricing/SLAs/hours, stale pages)
```

3. Write `00-README-summary.md` with these exact sections:
   - **How this was done:** method and the JavaScript limitation.
   - **The overall picture:** what AI gets right, then a numbered list of where AI gets confused, such as company age, size, pricing, proof and locations.
   - **Highest-priority fixes:** a table `| # | Issue | Page(s) |` listing the page numbers.
   - **Recurring patterns:** issues that repeat across pages, including a typo list.
   - **Index.**

## Phase 2 — Technical checks (use a real browser for these)

- `/llms.txt`, `/robots.txt`, `/sitemap_index.xml`, `/.well-known/agent-card.json`, `/.well-known/agent.json`, `/.well-known/mcp`: does each exist, and what does it say? Read `/llms.txt` in full and flag wrong links, legacy brand names, copied descriptions and missing key pages.
- **Structured data (JSON-LD):** types on the home, contact and main service pages. Read the Organization record in full and compare its hours, address, area served and employee count against the visible site.
- **The contact or discovery form:**
  - Is it in the raw HTML, or drawn by JavaScript or inside an iframe?
  - Which platform is it, and does it use a CAPTCHA?
  - Does it actually render in a browser?
  - Is there a scheduling link anywhere, and plain-text alternatives such as email and phone?
- Canonical tags pointing at other or redirected URLs; `nofollow` on pages meant to rank; redirects for removed pages; indexed mirror copies on CDN or other subdomains.
- **Brand palette and fonts:** sample the computed colors of buttons, dark sections and links, plus the heading and body fonts. Note signature design elements.

## Phase 3 — Build the report site

Build a static HTML site with Tailwind CSS, styled to the company's palette. If its font is licensed, use the closest free Google Font. If npm is blocked, use Tailwind's standalone CLI binary. Store colors as CSS variables so the same build can serve a second brand.

- **Overview page:**
  - Hero ("How AI sees {domain}.").
  - A **"Some key findings"** heading over a callout card of headline numbers: pages reviewed, issues flagged, high-priority fixes open, the most striking contradiction, and the contact-route problem.
  - A full-width alert bar linking to the contact-form fix.
  - Promo cards for the AI Page example and the seller cards.
  - Then: the overall picture, the priority fixes table (each page number linked), recurring patterns, and a card per page grouped by section, showing its issue count.
- **One page per report:** hero with "View live page," the capture date and the issue count; a sidebar of all pages; the Issues section highlighted; previous/next links.
- **Header:**
  - Wordmark, then nav grouped with separators: `Findings | {section links} | AI Page example · Seller cards · Scorecard · Change log`, plus a Download button.
  - Below 1440px, a **Menu** button opens a full-height panel that slides in from the right, with links stacked vertically. It closes with ×, Esc, clicking outside, or choosing a link.
- **Every page carries:** `<meta name="robots" content="noindex, nofollow, noarchive, nosnippet, noimageindex, noai, noimageai">` plus googlebot and bingbot noindex tags.
- **Test:** no horizontal scroll at 390, 768, 1024, 1280, 1440 and 1920px. Every internal link and anchor resolves.

## Phase 4 — AI Page example

Build a draft "Official information about {company}" page modeled on the model AI info page. Sections:
- Basic information
- About
- Services and pricing
- Service levels
- Differentiators
- Ideal for
- Not suitable for
- Awards
- Accreditations
- Client results
- AI assistant guidelines
- Contact

Fill it only with public facts. Mark each missing fact with a **GAP** badge and each contradiction with a **CONFLICT** badge, and add a review note explaining where the problem shows up. Add:
- A **Show gaps** toggle that hides the review notes to preview the finished page.
- A gap summary table.
- Suggested Organization JSON-LD.

If the company already has an AI info page, make this an updated version of it instead.

## Phase 5 — Seller cards for AI buying agents

A page that:
1. **Explains** that "seller cards" have no ratified standard yet. In practice a card is one fact sheet published in layers: a visible fact page, matching schema.org JSON-LD (Service/Offer/Organization), an `/llms.txt` entry, and an action route agents can use. An A2A agent card at `/.well-known/agent-card.json` comes later, once the company runs its own agent.
2. **Links to examples and specs:** the model AI info page, llmstxt.org, schema.org/Service, an A2A agent-card explainer, Google's A2A purchasing-concierge codelab, an agent.json vs agent-card.json explainer, and B2B agent-shortlisting research.
3. **Shows cards:** a company card and one card per main service, using the fields agents shortlist on. Mark each missing field **Gap**, each contradictory one **Conflict**, and each published only in hidden markup **Hidden**.
4. **Shows a JSON-LD example** for one service.
5. **Maps where cards should live** as a site-structure tree, marking exists / fix / add / later.
6. **Reviews** the current `/llms.txt` and structured data.
7. **Opens with a critical callout** if no AI buying agent can use the contact form. Explain why in plain terms, then give fix steps for the form platform:
   - Describe the route in plain text.
   - Publish a scheduling link (for HubSpot: a Meetings page).
   - Add a no-JavaScript fallback.
   - Build an agent intake route: a short separate form behind a server-side endpoint that validates, rate-limits and forwards to the platform's submission API (for HubSpot, the Forms submission API; confirm the current endpoint, since v3 is labeled legacy).
   - Confirm with the buyer by email before sales follows up.
   - Test with real agents (ChatGPT agent mode, Perplexity Comet, Gemini in Chrome).
8. **Ends with a priority checklist** with owners and effort.

## Phase 6 — Typos, rescans and the change log

- **Typo list:** turn each typo into a link to its exact spot on the live page, using a text fragment (`page#:~:text=typo`, with hyphens encoded as `%2D`). Verify each still exists live before linking.
- **When I say "rescan":**
  - Re-check only what was flagged.
  - Strike through fixed items with ✅ and stop counting them in the issue totals.
  - Remove pages I say were deleted or redirected, and check where they now go.
  - Report anything new the change caused, such as canonicals pointing at redirected URLs or leftover links.
- **Change log:** keep a page in the top nav listing every rescan and report update, newest first, with times.

## Phase 7 — Hand-off downloads

Add **Download as HTML** (header, footer, menu) and **Download full site (.zip)** (overview hero, footer):
- **The HTML file** is one self-contained document: every page, CSS inlined, every internal link rewritten to an in-page anchor, and links to any other site pointing at its published address. It must work offline.
- **The zip** holds the full multi-page site, the markdown sources and the build scripts.

## Phase 8 (optional) — Compare a second company

Run phases 1–7 for {{COMPARE_COMPANY}} as its own set of pages, in its own palette and font. Cross-link the two with "See how {other} compares" in the hero, the footer and the menu. Add a shared **Scorecard** page to both sites. Score each criterion 0–10, then calculate points = weight × score ÷ 10:

| Criterion | Weight |
|---|---|
| Facts findable and consistent (founding, size, location, ownership, counts) | 20 |
| Pricing and what's included | 15 |
| Service levels and onboarding terms | 10 |
| Proof in readable text (case studies with figures, named testimonials, dated awards) | 15 |
| Machine-readable layer (/llms.txt, structured data, AI info page) | 15 |
| A route an AI agent can use | 15 |
| Technical and copy hygiene | 10 |

Show each score with its evidence, both totals, the combined average, and "what each can borrow from the other."

## Phase 9 (optional) — Publish

1. Push to the GitHub repo and turn on GitHub Pages from `main` / root, with a `.nojekyll` file. The Pages URL is case-sensitive, so it must match the repo name exactly.
2. **For a custom subdomain on Cloudflare:**
   - In Cloudflare, add a CNAME record from `{subdomain}` to `{github-user}.github.io`, set to DNS only (grey cloud) until GitHub issues the certificate.
   - Then set the custom domain in the repo's Pages settings.
3. **For stronger crawler blocking,** if the DNS record is set to proxied, Cloudflare can block AI bots and add an `X-Robots-Tag: noindex` header. Explain these options; don't change account or DNS settings yourself.
4. Confirm every page, download and cross-link loads on the live URL, then give me the links.

## Deliverables

- The markdown reports.
- The live report site (or the built files).
- Both download files.
- A one-paragraph summary of the biggest findings, with the three fixes that matter most.
