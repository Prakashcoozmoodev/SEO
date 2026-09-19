# ctbooks.co Audit Package — 2026-09-19

This folder contains the complete SEO audit for **https://ctbooks.co/** (CTBOOKS — *The Salvation Equation* by Christopher Thomas).

## Files

- **FULL-AUDIT-REPORT.md** — 13-section full audit (Technical, Content/E-E-A-T, On-Page, Schema, Sitemap, Performance/CWV, Images, GEO/AI, E-commerce, Backlinks, SXO) with health score **38/100**, Top-5 Critical + Quick Wins, and Appendix with evidence + fixed metadata + JSON-LD.
- **ACTION-PLAN.md** — Prioritized checklist (P0/P1/P2/P3) with Impact/Effort, assignee, and exit criteria. Designed for 7 / 14 / 30-day execution.

## How it was produced

Direct egress for non-GitHub hosts is blocked in the sandbox (MITM proxy allows only `github.com`/`api.github.com`). All non-blocked fetches would 500/timeout via `requests`/`curl`. This audit therefore used the **platform `fetch_page` tool** (which has separate egress) + `wp-json` (`wp/v2/posts`, `wp/v2/pages`, `/wp-json/`) + `web_search` for `site:ctbooks.co`, plus manual cross-check of the Amazon listing (`B0CJDKRMFQ`). Sitemap 500s were confirmed via the tool; PageSpeed/CrUX were estimated from front-end stack (Elementor/Astra/LiteSpeed/Elfsight) because Google APIs were also blocked.

To reproduce with headless runners from an unrestricted network:

```bash
python scripts/fetch_page.py https://ctbooks.co/ --json > homepage.json
python scripts/run_headless_audit.py https://ctbooks.co/ --json --output-root output/ctbooks-audit
python scripts/analyze_schema.py https://ctbooks.co/
python scripts/analyze_sitemap.py https://ctbooks.co/
python scripts/pagespeed_check.py https://ctbooks.co/
```

Then compare with drift tools:

```bash
python scripts/drift_baseline.py https://ctbooks.co/
python scripts/drift_compare.py https://ctbooks.co/
```

## Immediate ask

Fix **P0** (sitemap 500 due to Yoast+AIOSEO conflict, placeholder content, hash links) and resubmit sitemap to Google Search Console. That alone unblocks indexing and lifts the health score by ~15 points.

*See FULL-AUDIT-REPORT.md Appendix B for copy-paste titles/metas and §4 for Book/Person JSON-LD.*
