# Launch Submission Checklist — bucksheatpumps.co.uk

## 0. Pre-launch verification (state at last audit)

Verified in the repository and over a local HTTP server:

- ✅ All 19 canonicals self-reference `https://bucksheatpumps.co.uk/...` — zero
  netlify.app or staging URLs anywhere (grep-verified across HTML/XML/TXT)
- ✅ All 19 sitemap.xml `<loc>` entries on `https://bucksheatpumps.co.uk`
- ✅ All `og:url` and JSON-LD `url` values on the live domain
- ✅ `/robots.txt` serves (HTTP 200) with the correct `Sitemap:` line and
  explicit allows for GPTBot, ClaudeBot, PerplexityBot, Google-Extended
- ✅ `/llms.txt` serves (HTTP 200) with the canonical entity description

⚠️ **Run these against the live domain before submitting** — outbound network
is blocked from the build sandbox, so live reachability could not be confirmed
from here:

```bash
curl -I https://bucksheatpumps.co.uk/robots.txt      # expect 200
curl -I https://bucksheatpumps.co.uk/llms.txt        # expect 200
curl -I https://bucksheatpumps.co.uk/sitemap.xml     # expect 200
curl -I https://bucksheatpumps.co.uk/no-such-page    # expect 404 (serving 404.html)
curl -sI https://www.bucksheatpumps.co.uk/ | grep -i location   # www should 301 to apex (or vice versa — pick ONE canonical host)
curl -sI http://bucksheatpumps.co.uk/ | grep -i location        # http should 301 to https
```

If the site is on Netlify, also confirm the `*.netlify.app` subdomain
redirects (301) to the custom domain — otherwise Google can index both.

## 1. Google Search Console

1. Add a **Domain property** for `bucksheatpumps.co.uk` (covers http/https,
   www/non-www) — verify via the DNS TXT record your registrar/host provides.
2. Submit the sitemap: *Indexing → Sitemaps →* `https://bucksheatpumps.co.uk/sitemap.xml`
   → confirm status "Success" and 19 discovered URLs.
3. **Request indexing manually, in this order** (URL Inspection → Request
   indexing; ~10/day quota, these five first):
   1. `https://bucksheatpumps.co.uk/`
   2. `https://bucksheatpumps.co.uk/oil-boiler-replacement.html` ← the £9,000 money page, window opens 21 July
   3. `https://bucksheatpumps.co.uk/boiler-upgrade-scheme.html`
   4. `https://bucksheatpumps.co.uk/air-source-heat-pumps.html`
   5. `https://bucksheatpumps.co.uk/air-to-air-heat-pumps.html`
   Next day: the £9,000 guide, cost guide, running-costs guide, then locations.
4. While in GSC: check *Page experience* and *Core Web Vitals* after ~28 days;
   spot-check the FAQ/Article rich results under *Enhancements*.

## 2. Bing Webmaster Tools

1. Add the site at bing.com/webmasters — use **"Import from Google Search
   Console"** (one click, inherits verification).
2. Submit `https://bucksheatpumps.co.uk/sitemap.xml`.
3. Use *URL Submission* for the same five priority pages (Bing's quota is
   generous). Bing feeds Copilot answers and DuckDuckGo — worth the ten minutes.

## 3. Citation / directory targets (10)

NAP discipline: use the **exact** footer strings everywhere — business name
"Bucks Heat Pumps", the address as printed in the site footer, one phone
number. Inconsistent citations dilute local rankings.

| # | Directory | Why it matters for a heat pump installer |
|---|---|---|
| 1 | **Google Business Profile** | The local-pack ranking factor. Category "Heat pump supplier" + secondary "Heating contractor"; service area = the five towns; link the site; post the £9,000 window as an Offer |
| 2 | **Bing Places for Business** | Feeds Bing/Copilot local results; import from GBP |
| 3 | **MCS "Find a Contractor"** (mcscertified.com) | Comes with certification — verify the listing shows the trading name, postcode and live website link; consumers and Ofgem both check it |
| 4 | **TrustMark directory** (trustmark.org.uk) | Government-endorsed register; BUS-adjacent trust signal, links from a .org.uk |
| 5 | **Checkatrade** | 14 competing ASHP listings in Aylesbury — it's a lead channel as much as a citation; reviews here double as the review-schema source later |
| 6 | **Trustpilot** | Claim the free profile; the review link to send every completed install; competitor Air To Heat runs on 25 reviews — beatable quickly |
| 7 | **Which? Trusted Traders** | Paid vetting, but the badge converts affluent rural homeowners — exactly the target demographic |
| 8 | **Yell.com** | Free listing; still syndicates NAP data to smaller UK directories and sat-nav/data aggregators |
| 9 | **FreeIndex** | Free, dofollow-friendly UK directory with real review weight in local SERPs |
| 10 | **Nextdoor Business** | Village-level word of mouth is how off-grid North Bucks actually buys; claim the business page and serve the five towns' neighbourhoods |

Worth adding when time allows: Thomson Local, Bark (lead-gen — set a budget
cap), the Buckinghamshire Business First member directory, and the parish
magazine websites for the named villages (Waddesdon, Padbury, Lacey Green
etc.) — cheap, hyper-relevant links no competitor bothers with.

## 4. First-week monitoring

- GSC *Pages* report: all 19 indexable pages should move to "Indexed" within
  1–3 weeks; 404.html should not appear (it's noindexed and unlinked in sitemap)
- Search `site:bucksheatpumps.co.uk` — check titles render as written
- Watch *Queries* for "£9,000 heat pump grant" impressions from ~21 July —
  that's the content bet paying off (or not) in near real time
