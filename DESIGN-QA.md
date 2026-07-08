# Design QA — bucksheatpumps.co.uk

Audited: all 20 pages (19 content pages + 404.html) × 3 viewports
(360 / 768 / 1280 px), headless Chromium, measurements taken after the full
stylesheet applies. Audit scripts: `qa_audit2.js` + `sticky_check.js`
(session scratchpad; re-runnable).

**Final result: zero issues at all three widths across all 20 pages.**

Re-verified after the favicon/404/README changes touched every page head:

- Overflow / tap targets / sub-16px text / hero fit: 0 findings at 360, 768, 1280
- Sticky call bar: 14px clearance above the last footer line at full scroll
- FAQ accordions (functional test): open on click ✅ close on click ✅
  open via keyboard Enter ✅ focusable with visible ring ✅
- Link crawl (20 pages, including anchors and asset hrefs): 0 broken
- 404.html: skip link, `#main`, one H1, no sticky bar (intentional — no
  body padding reserved), noindexed, in no sitemap

## Responsive & interaction fixes

| Issue found | Where | Fix |
|---|---|---|
| Horizontal overflow, 11px | index.html @360 (comparison table) | All 21 `<table class="compare-table">` wrapped in `.table-scroll` (`overflow-x:auto`, `tabindex="0"`, `role="region"`, labelled). Verified: `document.scrollWidth == 360` |
| Horizontal overflow, 36px | contact.html @768 (grid blowout — unbreakable email link set the aside's min-content wider than its track) | `.contact-grid > * { min-width: 0 }` + `overflow-wrap: anywhere` on contact/footer links; same guard on `.footer-grid` |
| Table crush/overflow on mobile | 3-column tables @360 | 3+-column tables get `min-width: 560px` inside the scroll container (via `:has()`), plus a visible "Swipe to see the full table →" hint injected above (mobile only) |
| Text under 16px on mobile | 13px header phone, 14px `--text-sm` everywhere (nav, buttons, labels, tables, footer, breadcrumb), 15px `.data` | Mobile-first token flip: `--text-sm: 1rem` and `.data: 1em` at base; restored to `0.875rem` / `0.9em` from 768px. Nothing under 15.5px computed at 360 |
| Tap targets under 44px | Logo (28px), breadcrumb links (16px), footer links (31px), homepage card-title links (24px) | Logo → 44px flex; breadcrumb/footer/card links → padding-block + negative-margin trick (44px hit area, no layout shift). Inline links inside paragraphs/table cells are exempt per WCAG 2.5.8's inline exception (documented, not "fixed") |
| Hero taller than one 360×740 viewport | index 785px→, oil 878px, a2a 845px, risborough 842px + others | Mobile hero padding reduced (`--space-6/8`, full padding restored ≥768), `--text-4xl`/`--text-3xl` clamp minimums lowered to 2rem/1.75rem, hero-sub at `--text-base` + tighter margins on mobile. All 19 heroes now ≤736px |
| Header phone wrapped below logo @360 (side-effect of the 16px floor) | all pages | ≤419px: decorative phone icon hidden, tighter padding/gap, logo 1rem. Phone verified back on row one, flush right (right edge 344/360) |
| Sticky call bar overlap | — | Verified with a real scroll to page bottom: 14px clearance between the last footer line and the bar (`body` reserves `--space-16`). Bar also **added to the homepage** — it was on 18/19 pages, a consistency gap |
| FAQ accordions | all pages | Native `<details>/<summary>` — verified toggling; summaries ≥44px; `+/–` marker via CSS with default marker suppressed. No JS involved, nothing to misbehave |
| Font loading flash | all pages | No FOIT (async CSS + `display=swap`); FOUT minimised: preconnects, metric-reasonable fallbacks (Georgia / system-ui), fonts CSS non-blocking. Residual one-time swap on first visit is inherent to third-party fonts; eliminate fully only by self-hosting (noted as an option, not done) |
| Focus states | `summary` and scrollable table regions had none | Added `summary:focus-visible` and `[tabindex="0"]:focus-visible` to the global copper focus-ring rule. First Tab hits the skip link (verified) |

## Consistency pass

| Check | Result |
|---|---|
| Spacing rhythm | All section/component spacing uses the 4px-base tokens; zero raw-px paddings in the stylesheet (grep-verified) |
| Temperature-gradient rule | Now under **H1 only** — `.section-title::after` and the `.on-ink` variant removed per this instruction (supersedes the earlier "H1s and section headers" spec; H2s no longer carry the rule) |
| Copper usage | Raw `--copper` remains in exactly two places: the H1 signature gradient and the focus ring. CTAs and `.data` use `--copper-deep` (AA-compliant); former copper separators (breadcrumb `›`, trust-marker `·`) switched to `--ink-soft`; link hover deepened to `--copper-cta-hover` (was 4.1:1, now 8.5:1) |
| Lorem ipsum / orphaned text | Zero hits site-wide |
| Intentional launch placeholders (not orphans) | `[Street address]` `[postcode]` `[MCS-XXXXXX]` `[TM-XXXXXX]` `[XXXXXXXX]` `[GBXXXXXXXXX]` `[Privacy policy]` ×19 pages (footer), `[TODO: street address]` `[TODO: postcode]` ×1 (homepage JSON-LD) — all must be replaced before launch |
| Internal links | Crawl of all 19 pages: **0 broken links, 0 broken anchors** (`#listed-buildings`, `#quote`, `#main` all resolve) |

## Notes for future changes

- The inline critical CSS in each page head mirrors the design system; if
  header/hero/button styles change in `css/styles.css`, regenerate the inline
  block (script in session scratchpad) or the first paint will drift.
- 360px header fit is tight by design (16px text floor + phone top-right).
  If the brand name or phone number gets longer, re-check ≤419px.
