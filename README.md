# Integris AI View

Website: https://msuddeth.github.io/integris-ai-dashboard/

Original review: October 29, 2026. Latest flagged-issue rescan: October 30, 2026.

24 pages checked. 137 open findings remain, down from 149: 7 verified resolutions, 6 closed audit corrections, and 1 previously uncounted open Leadership finding restored. The 34/100 Integris and 56/100 First Focus scores remain historical October 29 assessments; this update does not rescore them or rescan First Focus.

## Publish or refresh

See [update instructions](UPDATE-DASHBOARD.md) for uploading this package to GitHub. GitHub Pages serves main / root and republishes committed changes automatically. The build tools do not perform a live audit themselves.

## Rebuild from source

```bash
python3 -m pip install -r requirements.txt
python3 scripts/build.py
python3 scripts/bundle.py
```

The compiled CSS is included. Report-text changes do not require a Tailwind rebuild.

## Files

- index.html: overview, current finding counts and links to the page reports.
- pages/: the 24 individual reports, change log, example AI page, seller cards and historical scorecard.
- content/: editable Markdown reports and change log.
- src/: supplemental HTML templates and CSS source.
- shared/scorecard.html: historical comparison template.
- site.json: navigation, summary text and configuration.
- assets/: existing compiled styles, preserved in this update.
- scripts/build.py: generates the site from the sources.
- scripts/bundle.py: generates both hand-off downloads, including build tools in the ZIP.
- downloads/integris-ai-view.html: self-contained offline report.
- downloads/integris-ai-view-site.zip: complete upload/rebuild package.
- RESCAN-2026-10-30.md: concise rescan results and limitations.
- audit/rescan-2026-10-30.json: item-level evidence ledger, source URLs and raw HTML hashes.
- ai-website-review-prompt.md: original general audit prompt for reference.

The First Focus report files were not supplied. Comparison links open the original externally hosted First Focus report; it remains outside this repository. No external website or GitHub writes were made while preparing this package.

## Method

Fresh initial HTML was fetched for the 24 Integris pages, without JavaScript, to recheck earlier findings. Contact and Privacy were additionally inspected in a JavaScript-enabled browser. No form was submitted. Metadata, source links and page counts were updated; original descriptive narrative remains historical where not explicitly refreshed. Some open findings are editorial recommendations rather than proven defects.

Every report carries crawler noindex tags, which are indexing requests rather than access controls. The dashboard remains a public GitHub Pages site.
