# Site Hierarchy Plan — bucksheatpumps.co.uk

Lead-generation site for air source heat pump installation across Buckinghamshire
(Aylesbury, Buckingham, Wendover, Princes Risborough, Winslow, and the rural
North Bucks villages — oil/LPG heartland). Architecture follows the gaps
identified in `research/competitor-analysis.md`.

## Principles

1. **Shallow commercial layer.** Homepage, three core service pages, and the
   grant hub all sit in the main nav, one click from anywhere. These are the
   money pages and receive site-wide link equity.
2. **Guides silo out of nav.** Everything under `/guides/` is deliberately
   **excluded from the main navigation**. Guides earn rankings on
   informational queries and pass equity to the commercial pages through
   **in-content contextual links only** (guide → service page, service page →
   supporting guide). This keeps the nav focused on conversion while the silo
   does the topical-authority work.
3. **Every guide links up.** Each guide must link to at least one core service
   page and to the grant hub where relevant. Commercial pages link down to the
   guides that answer their objections (as the homepage FAQ teaser already does).
4. **No orphans.** Every page must be reachable through at least one in-content
   link, and everything goes in `sitemap.xml`.

## Hierarchy

```
/ (homepage)
│
├── IN MAIN NAV — commercial layer
│   ├── /air-source-heat-pumps.html        Core service: ASHP design + installation
│   ├── /oil-boiler-replacement.html       Core service: oil/LPG → heat pump conversion (£9,000 angle)
│   ├── /air-to-air-heat-pumps.html        Core service: air-to-air systems (£2,500 grant angle)
│   ├── /boiler-upgrade-scheme.html        Grant hub: BUS explained, eligibility, we-apply-for-you
│   ├── /about.html                        Trust page: team, MCS number, accreditations, guarantees
│   └── /contact.html                      Conversion page: survey booking form, phone, service area
│
└── NOT IN NAV — /guides/ silo (in-content links only)
    ├── /guides/9000-pound-heat-pump-grant-oil-lpg.html
    │       P1 gap. The 21 July 2026 £9,000 oil/LPG uplift: who qualifies,
    │       deadline (31 Mar 2027), off-gas-grid Bucks villages angle.
    │       Links to: /oil-boiler-replacement.html, /boiler-upgrade-scheme.html
    ├── /guides/heat-pump-running-costs-buckinghamshire.html
    │       P2 gap. Running costs vs oil, LPG, gas and electric at 2026
    │       tariffs; SCOP explained; heat pump tariffs.
    │       Links to: /oil-boiler-replacement.html, /air-source-heat-pumps.html,
    │       /boiler-upgrade-scheme.html
    ├── /guides/heat-pump-cost-guide.html
    │       Installed prices by property type (2-bed cottage → 5-bed
    │       farmhouse); price drivers; grant maths in 3 worked scenarios.
    │       Links to: all three service pages, /boiler-upgrade-scheme.html
    ├── /guides/heat-pump-planning-permission-buckinghamshire.html
    │       P3 + P4 gaps combined. Permitted development after the May 2025
    │       rule change (1 m boundary rule scrapped), MCS 020 noise limit,
    │       conservation areas (Chilterns villages, Aylesbury old town), and
    │       a dedicated #listed-buildings section (consent process).
    │       Links to: /air-source-heat-pumps.html, /boiler-upgrade-scheme.html,
    │       noise + old-houses guides
    ├── /guides/do-heat-pumps-work-in-old-houses.html
    │       Suitability for pre-1980s/solid-wall/rural stock; insulation-first
    │       logic; EPC recommendations rule; radiator maths; high-temp units.
    │       Links to: /air-source-heat-pumps.html, /oil-boiler-replacement.html,
    │       /boiler-upgrade-scheme.html, planning + costs guides
    ├── /guides/heat-pump-vs-oil-boiler.html
    │       Head-to-head decision table (10 factors, winner per row); honest
    │       "when the boiler wins" section; hybrid exclusion.
    │       Links to: /oil-boiler-replacement.html, /boiler-upgrade-scheme.html,
    │       £9,000 + running-costs + cost + old-houses guides
    ├── /guides/heat-pump-noise-guide.html
    │       Real dB table (sound power vs pressure), R290 units, placement
    │       tactics, defrost noise, neighbour reassurance.
    │       Links to: /air-source-heat-pumps.html, /boiler-upgrade-scheme.html,
    │       planning guide
    └── /guides/air-to-air-heat-pump-grant.html
            P5 gap. The £2,500 air-to-air BUS route vs the £7,500/£9,000
            air-to-water route; residential-only rules; full-replacement rule.
            Links to: /air-to-air-heat-pumps.html, /boiler-upgrade-scheme.html
```

## Location pages (built — footer-linked only)

Exactly four, each with genuinely local content (housing stock by estate/era,
5–8 named off-grid villages, town-specific conservation notes, one worked
grant scenario). Linked from the footer "Areas We Cover" column on every
page — deliberately NOT from the homepage body or main nav.

- /heat-pumps-aylesbury.html          Bedgrove/Southcourt/old town + Weedon,
                                      Hardwick, Whitchurch, Oving, N. Marston,
                                      Quainton, Cuddington, Dinton
- /heat-pumps-buckingham.html         Georgian centre/Page Hill/Lace Hill +
                                      Gawcott, Tingewick, Padbury, Maids
                                      Moreton, Akeley, Thornborough,
                                      Leckhampstead, the Lillingstones
- /heat-pumps-princes-risborough.html Town/Princes Estate + ridge villages:
                                      Lacey Green, Loosley Row, Speen, Bledlow
                                      Ridge, Saunderton, Whiteleaf, Ilmer,
                                      Bledlow (AONB angle)
- /heat-pumps-wendover.html           High Street CA/Halton + The Lee, Lee
                                      Common, South Heath, Dunsmore, St
                                      Leonards, Cholesbury, Wendover Dean,
                                      Ellesborough (LPG angle)

## Future expansion (not built yet)

- **Case studies** (phase 2): `/case-studies/` — named village, heat loss
  numbers, before/after running costs, photos. Feeds trust signals identified
  as the competitor bar (P7).

## Nav spec (as implemented on the homepage)

Air Source Heat Pumps · Oil Boiler Replacement · Air-to-Air Heat Pumps ·
£9,000 Grant (grant hub) · About · Get a Quote (CTA-styled contact link)

Footer carries: copyright, company registration, MCS certificate number,
privacy policy. Guides are **not** in the footer either — contextual links only.
