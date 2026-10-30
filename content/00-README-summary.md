# How AI Sees integrisit.com — Summary & Index

**Prepared:** October 29, 2026
**Scope:** 24 top-level pages on integrisit.com — every page in the main navigation and footer. The /blog/ directory and the separate events and trust-center subdomains were not read.

**Last rescanned:** October 30, 2026 at 9:43 AM CDT. All 24 previously reviewed pages returned HTTP 200. Open findings: **149 → 137** (7 verified resolutions, 6 closed audit corrections, and 1 previously uncounted open Leadership finding restored). This is a flagged-issue rescan, not a new whole-site audit or a rescore. See the [change log](changelog.md).

## How this was done

The original review is dated October 29. On October 30, 2026 at 9:43 AM CDT, previously flagged issues on all 24 pages were checked using fresh HTTP fetches with cache-control headers. Script, style and tracking markup was separated from readable page content; metadata and links were checked in the HTML. Contact and Privacy were also inspected in a JavaScript-enabled browser. No form was filled or submitted.

**Scope and limits:** this method tests what a non-JavaScript reader receives; it does not replicate every AI assistant. A missing field in initial HTML does not establish universal agent failure. Verified resolutions and earlier audit errors are shown separately. Remaining editorial recommendations are counted as open findings, not proven technical defects. Original descriptive content remains historical where not explicitly refreshed. First Focus and the October 29 comparison scores were not rescanned.

**Cache discrepancy:** a search-reader copy showed a broader privacy policy, while both a fresh HTML fetch and a browser showed cookie-policy content at the same URL. The privacy finding remains open; the divergent response is recorded rather than treated as a verified fix.

## The overall picture

**What AI gets right.** AI clearly understands Integris as an SMB-focused managed service provider offering managed IT, the CORE AI-era managed service, managed cybersecurity and compliance, managed cloud and advisory, with vertical depth in banking, credit unions, legal and manufacturing. The Clutch #1 ranking, ISO 27001/42001, SOC 2 Type II and the CORE/Shamrock story come through consistently.

**Where AI gets confused or comes up empty:**

1. **How old is Integris?** Pages say "founded in 2021" (About), "20+ years" (most service pages) and "30+ years" (Financial Institutions). The Leadership page explains the 1997 → 2021 lineage; that distinction should be made clearer on the other pages.
2. **How big is Integris?** "115K endpoints" (home), "115" and "115k" on the same Managed IT page, "100k+ assets" elsewhere.
3. **What does it cost?** Nothing. The Pricing page has no figures and the calculator is unreadable to AI.
4. **What do clients say?** Testimonial sections on Managed IT, Cybersecurity, Managed Cloud and Financial Institutions come up empty for AI (video/widget), and the homepage's testimonial heading sits over blog posts. Named, text testimonials exist only on the Law Firms, Manufacturers and Pricing pages — the Financial Institutions service page lacks a named bank quote in its primary copy, while Pricing does quote Fayette Savings Bank.
5. **Proof of results.** Resources now links two case studies, including Rensa Filtration dated October 30. The current listing no longer states the 80% Shamrock figure, so the old Resources-vs-CORE contradiction is closed. CORE still needs evidence and methodology for its ROI claim.
6. **Where is Integris?** 18 U.S. offices are listed on Locations, but international expansion appears in press releases, and the Leadership biography mentions the First Focus acquisition; core company pages still emphasize the U.S.

## Highest-priority fixes

| # | Issue | Page(s) |
|---|---|---|
| 1 | ✅ ~~**Canonical tag on Financial Institutions points to the removed Credit Unions URL**~~ — **Fixed** at 1:38 pm; the canonical now points to the page itself | 09 |
| 2 | ✅ ~~**"nofollow" robots tag** on Financial Institutions~~ — **Fixed** at 3:04 pm rescan; the page is now "index, follow" | 09 |
| 3 | **Lorem ipsum placeholder text** in the "Managed IT services overview" section | 03 |
| 4 | **"115" vs "115k" endpoints** on the same page | 03 |
| 5 | **Company age contradictions** (2021 / 20+ / 30+ years) | 09, 17 + service pages |
| 6 | **FAQ #19 answers the wrong question** (security packages → Managed IT benefits) | 05 |
| 7 | **No readable pricing** of any kind | 15 |
| 8 | **Privacy Statement is only a cookie policy**; Contact links to a 2025 archived privacy page | 23, 26 |
| 9 | ✅ ~~**Cookie-banner placeholders** on the three flagged pages~~ — verified absent on October 30; Osano is loaded | 12, 14, 24 |
| 10 | **"Microsoft Gold Partner"** (retired tier) vs "Solution Partner" | 06, 20 |

## Recurring patterns

- **Script-dependent contact route.** Contact fields are absent from the initial HTML, but the HubSpot form rendered in a JavaScript-enabled browser with reCAPTCHA. Submission and agent compatibility were not tested. Sales CTAs remain in the initial HTML of Careers, Support, Terms and Privacy.
- **Claims needing qualification:** the 95%/top-5% and CSAT/NPS statements lack supporting figures or methodology on the reviewed pages. The homepage does label its Clutch Leaders Matrix August 2026, so its ranking is not treated as wholly unsourced.
- **Three names for CORE** (CORE Intelligent Managed Services / CORE Managed AI / CORE Managed Services) and **three for Managed Cloud**.
- **CORE coverage varies:** Advisory already mentions deploying AI, and Law Firms links AI articles; both now have October 29 modification timestamps. Their main narratives still lack a dedicated CORE explanation. Highly Regulated Industries and Manufacturers also lack a clear CORE offer in their primary copy.
- **Legacy TechMD contact details** on 7 locations and the Support page.
- **Leftover UI text** ("Expand," "Bio*Expand*") and image file names used as alt text.
- **Typos AI will notice** — rechecked October 30, 2026: **3 open, 7 previously fixed**, and 6 more went away with the removed Community Banks and Credit Unions pages.
    - **Still open** (each link opens the live page; in Chrome and Edge it scrolls to the typo and highlights it):
        - [“excelling Integris”](https://integrisit.com/about/leadership/#:~:text=excelling%20Integris){target="_blank" rel="noopener"} — unclear wording, probably “advancing Integris' future-ready service model” · *Leadership*
        - [“subprocessores”](https://integrisit.com/privacy-statement-us/#:~:text=subprocessores){target="_blank" rel="noopener"} — should be “subprocessors” · *Privacy Statement*
        - [“interested-based”](https://integrisit.com/privacy-statement-us/#:~:text=interested%2Dbased){target="_blank" rel="noopener"} — should be “interest-based” · *Privacy Statement*
    - **Fixed since the first scan:** ~~“CORE Manage AI”~~ (Homepage) · ~~“ConverageOne”~~ (Leadership) · ~~“President on Integris”~~ (Leadership) · ~~“s AI adoption grows”~~ (CORE) · ~~“work-from-anywhere-on any-device”~~ (Advisory Services) · ~~“assessment, done”~~ (Advisory Services) · ~~“Suchof”~~ (Law Firms)

## Index

| File | Page | URL |
|---|---|---|
| [01-home.md](01-home.md) | Homepage | / |
| [02-solutions.md](02-solutions.md) | Solutions overview | /services/ |
| [03-managed-it.md](03-managed-it.md) | Managed IT | /services/managed-it/ |
| [04-core.md](04-core.md) | CORE Intelligent Managed Services | /services/core/ |
| [05-cybersecurity.md](05-cybersecurity.md) | Managed Cybersecurity & Compliance | /services/cybersecurity/ |
| [06-managed-cloud.md](06-managed-cloud.md) | Managed Cloud | /services/managed-infrastructure-services/ |
| [07-advisory.md](07-advisory.md) | Advisory Services | /services/advisory/ |
| [08-industries.md](08-industries.md) | Industries overview | /industries/ |
| [09-financial-institutions.md](09-financial-institutions.md) | Financial Institutions | /industries/financial-services/ |
| [12-law-firms.md](12-law-firms.md) | Law Firms | /industries/legal/ |
| [13-manufacturers.md](13-manufacturers.md) | Manufacturers | /industries/manufacturing-it-services/ |
| [14-highly-regulated-industries.md](14-highly-regulated-industries.md) | Highly Regulated Industries | /industries/highly-regulated-industries/ |
| [15-pricing.md](15-pricing.md) | Pricing | /services/managed-it/pricing/ |
| [16-resources.md](16-resources.md) | Resources | /resources/ |
| [17-about.md](17-about.md) | About Us | /about/ |
| [18-careers.md](18-careers.md) | Careers | /about/careers/ |
| [19-leadership.md](19-leadership.md) | Leadership | /about/leadership/ |
| [20-partners.md](20-partners.md) | Partners | /our-partners/ |
| [21-media-center.md](21-media-center.md) | Media Center | /about/press/ |
| [22-locations.md](22-locations.md) | Locations | /our-locations/ |
| [23-contact.md](23-contact.md) | Contact | /contact/ |
| [24-client-support.md](24-client-support.md) | Client Support | /support/ |
| [25-terms-and-conditions.md](25-terms-and-conditions.md) | Terms & Conditions | /terms-and-conditions/ |
| [26-privacy-statement.md](26-privacy-statement.md) | Privacy Statement (US) | /privacy-statement-us/ |

*Not included: /blog/ (excluded by request), events.integrisit.com and trustcenter.integrisit.com (separate subdomains).*
