# firecrawl vs scraperapi: Real Success Rates, True Credit Costs, and Which One Fits Your Pipeline

Most "Firecrawl vs ScraperAPI" comparisons stop at the list price — $19 entry for Firecrawl, $49 for ScraperAPI — and leave you to figure out the rest. That's a problem, because the sticker price tells you very little once you factor in how each service charges credits per request. On the one dimension that matters to nearly everyone, the picture most articles paint is incomplete: a 2026 benchmark by Scrapeway measured an average success rate of **72.1% for Firecrawl versus 52.3% for ScraperAPI** across a panel of real targets, yet on zillow.com ScraperAPI actually came out slightly ahead, and LinkedIn produced data on ScraperAPI while Firecrawl returned nothing at all.

So the honest answer is: Firecrawl wins on average, ScraperAPI wins in specific corners, and your bill can look very different from either list price depending on which sites you're hitting. Here's the breakdown with the numbers filled in.

> **Quick take:** If you're leaning ScraperAPI, the entry Hobby plan costs **$49/month** ($44.10/month billed annually) with 100,000 API credits and 20 concurrent threads, and you can test it first with a 7-day, 5,000-credit free trial that requires no credit card. There's also a 7-day no-questions-asked refund policy on paid plans. 👉 [Check the current ScraperAPI plans and start the free trial](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## What's actually different about the two tools

ScraperAPI is proxy infrastructure with a scraping API on top. You send a URL, it rotates through a proxy pool (over 40 million IPs), handles CAPTCHAs and anti-bot systems, optionally renders JavaScript, and returns HTML. Parsing is your job — with one exception: more than 20 Structured Data Endpoints for sites like Amazon, Google, and Walmart return clean JSON.

Firecrawl was built around a different contract. Every scrape returns clean Markdown by default, with HTML and structured JSON as options. It has a native `/crawl` endpoint that recursively walks an entire domain, a `/map` endpoint that lists every URL on a site in seconds, and an agent endpoint where you describe what you want in plain English and it browses on its own.

The practical consequence shows up when a target site ships a frontend redesign. With ScraperAPI, your CSS selectors break and your pipeline goes down until someone fixes them. With Firecrawl, the output is generated from the page's semantic content rather than its DOM structure, so a layout change usually doesn't break anything.

Whether that matters depends on where your output goes. Feeding an LLM prompt or a vector database? Markdown by default is a real advantage. Loading a structured database with parsers you've already built and maintain? HTML is perfectly fine, and ScraperAPI's extra SDKs (Python, JavaScript, Ruby, PHP, NodeJS, versus Firecrawl's Python and JavaScript) plus its persistent sessions and webhook support fit that workflow better.

## The benchmark numbers, site by site

Averages hide the interesting parts. Scrapeway's 2026 benchmark (data range September 11–25, a single test window with its own parameter setup) ran both services against the same panel of targets. Here's the full per-site success rate:

| Target | Firecrawl | ScraperAPI |
| --- | --- | --- |
| All-site average | 72.1% | 52.3% |
| amazon.com | 91.7% | 90.2% |
| booking.com | 91.8% | 1.1% |
| etsy.com | 99.7% | 96.2% |
| indeed.com | 66.6% | 28.1% |
| realtor.com | 72.0% | 24.2% |
| stockx.com | 94.6% | 59.8% |
| walmart.com | 85.3% | 83.5% |
| zillow.com | 92.7% | 93.7% |
| instagram.com | no data | no data |
| linkedin.com | no data | 57.7% |
| twitter.com | 74.4% | no data |

Three readings worth your attention:

1. **Heavily protected travel and real-estate sites were lopsided.** booking.com went 91.8% to 1.1%, realtor.com 72.0% to 24.2%. These are single-window measurements, not permanent laws — but a gap that wide is a signal worth testing against your own URLs.
2. **On mainstream e-commerce, they're close.** Amazon (91.7% vs 90.2%), Walmart (85.3% vs 83.5%), and Etsy (99.7% vs 96.2%) were effectively a wash — and on zillow.com ScraperAPI won outright.
3. **LinkedIn and Twitter are exclusive territories.** Only ScraperAPI produced LinkedIn data in this test; only Firecrawl produced Twitter data. If your project lives on one of those sites, that single row should settle the question.

One caveat worth repeating: this is one benchmark with one parameter configuration. It's strong evidence of relative behavior, not a guarantee for your particular URLs — which is exactly why both services give you free credits to run your own test (more on that below).

## The full ScraperAPI plan list, with the annual discount included

ScraperAPI's pricing page currently shows seven tiers. Every plan includes the same core feature set: JS rendering, premium residential and mobile IPs, advanced bypassing, parsing and structured data APIs, DataPipeline, full crawler access, and pay-as-you-go support. Annual billing cuts 10% off every tier.

| Plan | Monthly | Annual (per month) | Credits/month | Concurrent threads | Geo-targeting |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 | $44.10 | 100,000 | 20 | US & EU only |
| Startup | $149 | $134.10 | 1,000,000 | 50 | US & EU only |
| Business | $299 | $269.10 | 3,000,000 | 100 | Country-level (50+ countries) |
| Scaling (most popular) | $475 | $427.50 | 5,000,000 | 200 | Country-level |
| Professional | $975 | $877.50 | 10,500,000 | 300 | Country-level |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | Country-level |
| Enterprise | Custom quote | — | 22,000,000+ | 500+ | Country-level |

A few things on this table don't get mentioned often enough. Country-level geolocation targeting — the kind you need for anything outside the US and EU — only starts at **Business ($299/month)**. Hobby and Startup are locked to US and EU exit points. And the performance dashboard on the two lower tiers only retains data for the last 30 days; Business and up get unlimited history.

If you're not sure which tier fits, the trial exists for exactly this reason: every plan can be started as a 7-day trial with 5,000 credits, no card required. There's also a free tier that gives 1,000 API credits per month with a 5-concurrent-connection cap, sized for small ongoing projects rather than one-off tests. 👉 [Try ScraperAPI free with 5,000 credits before picking a tier](https://www.scraperapi.com/?fp_ref=coupons)

Exceed your concurrency limit and ScraperAPI returns a 429 — the request is turned away, never queued, and never charged extra. When credits run out, scraping pauses until renewal by default. From there you have options: auto-upgrade moves Hobby-through-Professional accounts to the next tier automatically when credits run dry, and Scaling-and-above accounts can switch on pay-as-you-go overage at a fixed per-credit rate with a monthly spending cap you set — a cap that's a hard limit, not a pre-charge, so it exists precisely to prevent surprise bills. Annual plans can also renew early for a fresh batch of credits.

## The credit math that changes the real price

Here's the part most comparison posts gloss over: ScraperAPI's headline credit counts are not page counts. ScraperAPI's own pricing FAQ states the scaling directly — a standard page costs 1 credit, **Amazon costs 5, Google and Bing (including subdomains) cost 25, and LinkedIn costs 30**. Sites behind Cloudflare, Datadome, or PerimeterX add 10 credits per request when ScraperAPI bypasses them. Rendering parameters and premium proxies stack additional multipliers on top.

Run the arithmetic: on the Hobby plan, 100,000 credits is 100,000 standard pages — but only 4,000 Google searches or roughly 3,300 LinkedIn pages. That's a very different project scope from what the plan name suggests.

Two mitigation tools exist, and they're worth knowing about before you commit. The dashboard's Domain Cost Estimator tells you the exact credit cost for any URL before you scrape it, and a `max_cost` parameter caps what any single request can consume. Setting `max_cost` on every call is the single easiest way to avoid a surprise bill.

Firecrawl, by contrast, charges a flat 1 credit per successful page regardless of target or complexity. Its modifiers do add up — JSON/LLM extraction adds 4 credits per page, PDF parsing adds 1 per PDF page, and options stack (JSON extraction plus Zero Data Retention is 1+4+1 = 6 credits per page) — but the base request is always 1 credit. For predictability, that's a genuine structural advantage.

Billing on failure works differently at each company, and it's the row most people get wrong. Firecrawl's official docs are explicit: a scrape that returns no result isn't charged, but a page that responds with an error status like 403 or 404 still gets returned to you and costs 1 credit — so "blocked request" and "free request" are not the same thing there. ScraperAPI's official policy is to refund credits on failed requests, though independent benchmark testing has flagged it for often charging blocked requests anyway. Whichever service you pick, verify how failures are billed against your specific targets before the volume ramps up.

## Firecrawl's plans, for comparison

Since pricing is half of this comparison, here are Firecrawl's current tiers (USD, effective September 2026), information only:

| Plan | Monthly | Annual (per month) | Credits/month | Concurrent |
| --- | --- | --- | --- | --- |
| Free | $0 | — | 1,000 | 2 |
| Hobby | $19 | $16 | 5,000 | 5 |
| Standard | $99 | $83 | 100,000 | 25 |
| Growth | $399 | $333 | 500,000 | 50 |
| Scale | $749 | $599 | 1,000,000 | 100 |
| Enterprise | Custom | — | Custom | Custom |

Per-credit, the comparison isn't as lopsided as the entry prices suggest. Firecrawl's Standard works out to roughly $0.001 per credit (monthly) versus ScraperAPI Hobby's $0.00049 — but remember that Firecrawl's credits buy pages at a fixed rate, while ScraperAPI's buy pages at a multiplier-dependent rate. On standard targets ScraperAPI is cheaper per page; on Google, Bing, and LinkedIn it isn't even close.

A few Firecrawl billing rules worth knowing, because they're easy to miss:

- **Credits don't carry over by default** — with one exception: the Scale plan allows a 1-month carryover. ScraperAPI's credits likewise expire with each billing cycle on all tiers.
- **Pay-as-you-go overage exists on both, structured differently.** Firecrawl lets paid plans top up in $5 increments with a monthly cap, starting from Hobby. ScraperAPI's equivalent is limited to Scaling and above.
- **Enterprise exists on Firecrawl too** — custom pricing with dedicated support, SLAs, and zero-data-retention options for approved use cases.

## Feature gaps that actually matter

Where the two services diverge beyond price:

| Capability | ScraperAPI | Firecrawl |
| --- | --- | --- |
| Primary output | Raw HTML (JSON via structured endpoints) | Markdown by default, HTML and JSON optional |
| Full-site crawl | No native crawl endpoint | Native `/crawl` and `/map` |
| Browser control (click, scroll, type) | No | Yes |
| Screenshots | No | Yes, full-page with custom viewport |
| Persistent sessions | Yes, 15-minute sticky IP | No |
| Webhooks | Yes | No |
| JS rendering | Yes, extra credit cost | Yes, on by default |
| Geolocation | 2 countries standard, 13 on top tier | 26 countries |
| SDKs | Python, JS, Ruby, PHP, NodeJS | Python, JS |
| Open source / self-host | No | Yes (AGPL-3.0, anti-bot layer excluded) |

ScraperAPI's Capterra rating stands at 4.6 stars from 62 reviews; Firecrawl has no Capterra rating recorded in that benchmark.

## So which one should you pick?

Work through three questions in order.

**Where does your data end up?** LLM prompt, vector store, or any AI pipeline → Firecrawl's default Markdown saves you a parsing layer, and a site redesign won't break your pipeline the way it breaks selectors. Pre-built structured database with existing parsers → ScraperAPI's HTML works fine, and its wider SDK and webhook support fit that stack.

**What are your target sites?** Mainstream e-commerce and search → either works; on Amazon specifically they scored within 1.5 points of each other. Booking, real estate, sneakers, or other heavily protected verticals → the benchmark gap favors Firecrawl by wide margins. LinkedIn scraping → ScraperAPI was the only one of the two producing data in the benchmark; X/Twitter → Firecrawl.

**What's your selector-maintenance budget?** If nobody on your team owns CSS selectors, ScraperAPI's HTML-first model means you inherit that maintenance cost. If you have engineers already maintaining scrapers, that cost is sunk and ScraperAPI's cheaper per-credit rate on standard targets starts looking better.

Two mistakes worth avoiding before you pay either way:

- **Don't judge by list price alone.** A $49 plan buying 4,000 Google results is a different product than a $49 plan buying 100,000 standard pages. Use the Domain Cost Estimator on your actual URLs first.
- **Don't test against easy URLs.** Both services have free tiers specifically sized for a real evaluation — ScraperAPI's 5,000-credit trial, Firecrawl's 1,000-credit free plan. Run 100–200 requests against your hardest real targets, not a sandbox page, before choosing a tier.

## Frequently asked questions

**Does ScraperAPI have a free trial?**
Yes. A 7-day trial with 5,000 requests' worth of credits, no credit card required, available on every plan. There's also a free plan with 1,000 API credits per month and a 5-concurrent-connection limit.

**Can I get a refund from ScraperAPI?**
Yes. ScraperAPI offers a 7-day no-questions-asked refund policy — contact support and they'll process it. You can also cancel anytime from the dashboard at no charge.

**Does ScraperAPI charge the same for every site?**
No. Standard pages cost 1 credit, Amazon 5, Google and Bing 25, LinkedIn 30, and sites behind Cloudflare/Datadome/PerimeterX add 10 credits per bypassed request. Check any URL with the dashboard's Domain Cost Estimator, and set `max_cost` to cap per-request spend.

**Is Firecrawl cheaper than ScraperAPI?**
Entry pricing, yes — $19 versus $49. Per credit on standard targets, ScraperAPI is actually cheaper. The real difference is predictability: Firecrawl bills a flat credit per page while ScraperAPI's costs scale with target difficulty.

**What happens when I exceed my ScraperAPI limits?**
Over concurrency, you get a 429 and the request is refused with no charge. Over credits, scraping pauses until renewal unless you've enabled auto-upgrade or pay-as-you-go overage (the latter only on Scaling and above).

## Final decision, compressed

Need AI-ready Markdown, whole-site crawling, or browser automation → Firecrawl is the better fit, and its lower entry price reflects a smaller credit allocation, not a better deal per page. Need raw HTML with your own parsers, sessions, webhooks, or LinkedIn access → ScraperAPI, with the Hobby plan covering most solo projects and the annual billing knocking it down to $44.10 a month. If either option could work for your targets, the 7-day free trial settles it with real data instead of benchmarks. 👉 [See ScraperAPI's full plan lineup and start your 7-day trial](https://www.scraperapi.com/pricing/?fp_ref=coupons)
