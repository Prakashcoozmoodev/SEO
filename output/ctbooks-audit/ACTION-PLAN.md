# Action Plan — ctbooks.co (CTBOOKS)

**Owner:** Christopher Thomas / Web Admin • **Due:** Rolling (P0 = 7 days, P1 = 14 days, P2 = 30 days)  
**How to use:** Check off items, add Assignee + Done date. Column *Impact* = SEO impact if fixed (1–10). *Effort* = hours.

## P0 — Critical (Unblocks Indexing) — Do This Week

| # | Issue | Fix | Impact | Effort | Assignee | Done |
|---|---|---|---:|---:|---|---|
| P0-1 | Sitemap 500 + robots triple declaration | Keep **one** SEO plugin (Yoast 25.9), uninstall AIOSEO completely (DB + `wp-content/aioseo-*`), purge LiteSpeed, re-generate sitemaps, verify 200, clean `robots.txt` to single `Sitemap: https://ctbooks.co/sitemap_index.xml`, submit to GSC + Bing. | 10 | 1h |  |  |
| P0-2 | Homepage is template dump (`Lorem ipsum`, `Vulputate …`, 3× `John Doe — CEO`, typo `The Salvation On Equation`, duplicate testimonial carousel) | Delete placeholder Elementor sections, fix H1 to single `The Salvation Equation`, rewrite hero copy to 80–120 words (value prop + free PDF + Amazon trust), keep **one** testimonial block with 2 real Amazon reviews (link to Amazon). | 9 | 2h |  |  |
| P0-3 | `[products]` shortcode literal + dead Woo blocks | Decide: **Remove WooCommerce** if not selling on-site (recommended) → delete shortcode, replace with static Book card + Amazon CTA + `301` pages `302–306` type `332`. If keep Woo, populate real product + `Product` schema. | 8 | 1h |  |  |
| P0-4 | Hash navigation dead ends (`#` for Shop / Videos / Listen Now) | Remove sections with no inventory or link to real URLs (`/books/`, YouTube channel, etc.). No hash links. | 7 | 1h |  |  |
| P0-5 | Duplicate title `Home - CTBOOKS` + empty metas | Set Yoast title template `%%title%% %%sep%% CTBOOKS`, write manual metas (see Appendix B in full report). Rewrite H1 hierarchy (1× H1, H2 for sections). | 8 | 30m |  |  |
| P0-6 | Elfsight empty widget waste | Remove `elfsight-app-dead9cfd-…` from `/testimonials/` until 10+ real Google reviews exist; self-host testimonials. | 6 | 30m |  |  |

**Exit criteria P0:** `curl -I https://ctbooks.co/sitemap_index.xml` → 200; `curl -I https://ctbooks.co/` shows single H1; homepage contains zero `Lorem ipsum` / `John Doe`.

---

## P1 — High (Content & E-E-A-T) — Next 14 Days

| # | Issue | Fix | Impact | Effort | Done |
|---|---|---|---|---|---|
| P1-1 | Author bio 2 sentences, no E-E-A-T, author = `greenjoyful@yahoo.com` | Rewrite `/biography/` 500–700w with credentials, photo, Amazon Author Central `sameAs`, add `Person` schema (JSON-LD in report §4). Change WP user Display Name to `Christopher Thomas`, set professional email. | 9 | 3h |  |
| P1-2 | 10 thin posts on same day `2025-09-15` (≈300w, 1 min, `Uncategorized`, keyword `Christian eBook` cannibalization) | **Consolidate:** Merge 4 `Christian eBook` thin posts → one pillar `/christian-ebook-guide/` (1,800w). 301 redirect thin URLs. Keep 2–3 distinct Christopher-book posts but expand to 1,200w, new categories (`Bible Study`, `Salvation`), add tags, FAQs, interlinks. | 10 | 2–3 days |  |
| P1-3 | No Book / FAQ schema → no rich results | Add Book + Product + AggregateRating JSON-LD (report §4) + FAQPage for homepage (“What is the Salvation Equation?” etc.). Validate in Rich Results Test. | 8 | 2h |  |
| P1-4 | Images oversized, alt irrelevant, placeholder.png | Recompress/rename covers (`the-salvation-equation-front-cover-…`), enable LiteSpeed WebP, add keyword-aware alts, set LCP `fetchpriority=high`, add OG image 1200×630. | 7 | 2h |  |
| P1-5 | No AI citability (`llms.txt`, FAQ) | Create `/llms.txt` (template in §8), add homepage FAQ block + speakable. Explicitly `Allow: GPTBot, CCBot` in robots. | 6 | 1h |  |
| P1-6 | `Theological Schola` typo + duplicate quotes | Fix → `Theological Scholar`, de-dupe testimonials to 1 block, cite source (Amazon). | 5 | 30m |  |

---

## P2 — Medium (Performance, Trust, Authority) — 30 Days

| # | Issue | Fix | Impact | Effort | Done |
|---|---|---|---|---|---|
| P2-1 | Heavy stack (Elementor + ElementsKit + Templately + ZipWP + 2 SEO plugins) → poor CWV | LiteSpeed tune (defer JS, preconnect `fonts.gstatic.com`, critical CSS, exclude LCP from lazy), audit plugins → remove unused (`templately/v1`, `zipwp/v1`, `hostinger-easy-onboarding`, amplitude). | 7 | 3h |  |
| P2-2 | No analytics / GSC / consent | Install GA4 (with `generate_lead` on PDF click), connect GSC + Bing, add cookie consent (Hostinger Cookie banner or Complianz), create `/privacy-policy/` (currently missing?) link in footer + newsletter. | 8 | 2h |  |
| P2-3 | Low authority (3 indexed URLs, 1 Hashnode mention) | Create Goodreads + Amazon Author Central + YouTube trailers, pitch 2 guest posts (GotQuestions, Christian blog), add `rel=me` sameAs. | 7 | 1 week outreach |  |
| P2-4 | Newsletter no GDPR | Replace raw link with Fluent Forms + double opt-in, add `I agree to privacy policy` checkbox, store consent, add success redirect. | 6 | 2h |  |
| P2-5 | REST author enumeration + email leak | Disable enumeration (`functions.php` filter), change author slug, hide `greenjoyful@yahoo.com`, enable 2FA. | 5 | 1h |  |
| P2-6 | PDF direct link no tracking | Gated PDF via email or at least UTM `?utm_source=ctbooks&utm_medium=pdf` + GA4 event, add affiliate disclosure if Amazon affiliate. | 5 | 1h |  |

---

## P3 — Low (Backlog)

- Add visible breadcrumbs (Astra), `HowTo` schema for “How to study the Bible with the book”, `Speakable`, image sitemap after sitemap fixed.
- Decide `/biography/` vs `/about/` → keep one, 301 the other.
- Security headers: `HSTS`, `X-Content-Type-Options`, `CSP` via Hostinger/Cloudflare.
- CDN: Enable Cloudflare free → cache static, early hints.
- Create `/sitemap/` HTML sitemap for users.

---

## Weekly Review Cadence

- **Week 1:** Verify sitemap 200, titles fixed, placeholders removed → submit GSC → log “P0 complete” in `.seo-cache/`.
- **Week 2:** Publish new biography + pillar guide, add schemas → validate Rich Results.
- **Week 4:** Run PageSpeed + GSC Coverage → compare indexed count (`site:ctbooks.co`) should be ≥12. Re-run audit `drift_compare.py`.

**KPI targets (60 days post-P0+P1):** Indexed URLs 12+, Impressions +60–120%, Avg. position for `The Salvation Equation` top 10, LCP ≤2.5s, 0 sitemap errors, 0 hash links.

---

*Full evidence, CWV estimates, and JSON-LD snippets in `FULL-AUDIT-REPORT.md` Appendix A–C.*
