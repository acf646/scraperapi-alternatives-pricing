# ScraperAPI alternative: should you switch, what would you switch to, and which plan should you buy if you stay? (Full plan table plus per-page cost math)

Most people who start looking for a ScraperAPI alternative are not missing a feature. They are holding an invoice where three million credits turned into 300,000 pages because the targets render JavaScript, and they want a cost per page they can put in a spreadsheet. If that's your situation, three short answers. You fetch a known list of URLs and need clean HTML or JSON back: stay, and buy the smallest tier that covers your page count. You need to crawl whole sites, map URLs, or feed markdown into a retrieval index: Firecrawl is built around that. You want finished datasets delivered by someone else's team: Zyte. The rest of this article is the arithmetic and the plan rules for the cases in between.

> **Quick pick:** the entry paid plan (from $49/month) covers most known-URL scraping; **Business at $299/month for 3,000,000 credits** (or 120,000 SERP requests) is the tier to buy once JavaScript rendering pushes your real page count past a million. There is a 7-day, no-questions-asked refund window, which is long enough to measure your own credit multiplier before you commit. 👉 [See ScraperAPI's current plans and credit allowances](https://www.scraperapi.com/?fp_ref=coupons)

## The full plan line-up, and what each tier is actually for

ScraperAPI prices by monthly credit allowance, and the tier names matter less than the credit count once you know your multiplier. These are the tiers the company publishes, with the figures that are stable enough to plan around.

| Plan | Price | Credits per month | Best fit | Purchase |
| --- | --- | --- | --- | --- |
| Free | $0 | 1,000 credits, 5 concurrent connections | Testing the API on a handful of URLs | [Start on the free plan](https://www.scraperapi.com/?fp_ref=coupons) |
| Hobby | from $49/month | Entry-level allowance for small jobs | One or two scripts, low page volume | [Pick the Hobby tier](https://www.scraperapi.com/?fp_ref=coupons) |
| Startup | $149/month | 1,000,000 credits | Steady JS-rendered scraping at mid volume | [Pick the Startup tier](https://www.scraperapi.com/?fp_ref=coupons) |
| Business | $299/month | 3,000,000 credits or 120,000 SERP requests; 100+ concurrent threads | High-volume pipelines and SERP monitoring | [Pick the Business tier](https://www.scraperapi.com/?fp_ref=coupons) |
| Scaling, Professional, Advanced | Listed on the pricing page | Larger allowances plus pay-as-you-go with a monthly spending cap you set | Teams that have outgrown 3M credits | [See the higher tiers](https://www.scraperapi.com/?fp_ref=coupons) |
| Enterprise | Custom quote | Custom volume, dedicated support channel | Committed annual volume | [Talk to sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Three billing details sit outside the table and change how the tiers behave:

- **Annual plans hand over the whole year's credits at signup.** You can spend them on any schedule, and if you run dry before the period ends you can renew the same annual plan early for a fresh allocation.

- **The first seven days are a 5,000-credit trial**, after which a free account drops to 1,000 credits per month. That trial is the cheapest way to find out whether your targets cost 1 credit or 20.

- **Credits are a ceiling, not a queue.** Go over your concurrency limit and the request comes back as a 429 rather than waiting in line, at no extra charge. Go over your credit allowance and scraping pauses until the next cycle unless you have turned on auto-upgrade, which moves you up a tier automatically. Pay-as-you-go past the cap exists only on the higher plans.

That last point is where unpredictable bills come from. If you are close to a limit, auto-upgrade can walk you from a $149 month to a $299 month without anyone approving it.

## What a credit costs at $299, by page type

The multiplier is set by the target site, not by your plan, so the same $299 buys 20 times fewer pages on a hard site than on a plain one. Here is the conversion at the Business rate of $299 for 3,000,000 credits, or roughly $0.0001 per credit.

| Request type | Credits per request | Cost per page | Pages 3M credits buy |
| --- | --- | --- | --- |
| Standard HTML | 1 | $0.0001 | 3,000,000 |
| JavaScript rendering | 5 | $0.0005 | 600,000 |
| JavaScript rendering, heavier pages | 10 | $0.001 | 300,000 |
| Hard anti-bot protection (e.g. DataDome) | 20 | $0.002 | 150,000 |
| Google SERP endpoint | 25 | $0.0025 | 120,000 |

In per-thousand terms: **$0.10 per 1,000 plain pages, $0.50 to $1.00 per 1,000 rendered pages, $2.00 per 1,000 pages behind hard bot protection, and about $2.49 per 1,000 SERP requests.** The SERP figure is a useful cross-check, since 3,000,000 credits divided by 120,000 SERP requests comes out to exactly 25 credits each.

Two practical consequences. First, a "3,000,000 credit" plan is only a three-million-page plan if your targets are static HTML. A pipeline of React-rendered product pages at 10 credits each is a 300,000-page plan, and you should size the tier from that number. Second, the multiplier is inspectable before you spend: the dashboard's Domain Cost Estimator returns the credit cost for any URL, and the `max_cost` parameter caps what a single request is allowed to consume. Setting `max_cost` and turning rendering off for pages that don't need it are the two levers that most directly cut a ScraperAPI bill.

👉 [Size your plan against your real page count](https://www.scraperapi.com/?fp_ref=coupons)

## Where a different tool is the better buy

The comparison pages that rank for this term are mostly written by vendors, so treat the framing with some suspicion and the numbers as their own published pricing. These are the figures each service states.

| Tool | Pricing model and entry price | Stronger than ScraperAPI at | Fits when |
| --- | --- | --- | --- |
| Firecrawl | Free tier of 1,000 credits/month; paid from $19/month billed monthly, $16/month billed annually; 1 credit per successful page with no complexity multiplier | Native crawl and site map endpoints, screenshots, click/scroll/type actions, PDF and DOCX parsing, markdown output, open source, native MCP server | You are ingesting whole sites into an LLM pipeline and want one flat price per page |
| Zyte | Pay per URL: HTTP responses from $0.13/URL on pay-as-you-go, falling to $0.06/URL at a $500 monthly commitment; browser rendering from $1.01/URL; 14-day free trial | Managed data delivery, where Zyte's team runs the scraping and hands over the dataset | Nobody on your side wants to own parsers and retries |
| Apify | Free tier; usage-based at $0.30 per compute unit, plus $8/GB residential proxy, $0.20/GB external transfer, storage billed hourly | A marketplace of 20,000+ prebuilt Actors, full Playwright and Puppeteer control, the open-source Crawlee SDK | You need a ready-made scraper for an odd site, or real browser automation |
| Bright Data | Custom quote; $5 free credit | A 150M+ IP pool across 195 countries, 120+ prebuilt scrapers, a dataset marketplace, AI Scraper Studio | Enterprise procurement, the hardest targets, or buying data instead of collecting it |
| ScrapingBee | From $49/month | Sub-second SERP responses and simple pricing | Your workload is mostly search results and you want one number to budget |
| Scrapy IO | Free with a $5 credit limited to one month; Starter $19/month, Growth $129/month, Scale $439/month | Pay-per-row billing, no charge for failed or empty runs, resumable long jobs, 150+ ready-made site scrapers | You want finished rows with named fields, not HTML you still have to parse |

Two cautions on reading that table. Per-URL and per-credit pricing are not the same unit, so a headline like $0.13/URL against $0.0001/credit does not mean a thousand-fold difference; it means the two vendors meter different things. And a vendor estimating what a competitor's budget buys on its own platform is marketing, not a benchmark.

## What ScraperAPI genuinely does not do

ScraperAPI's unit of work is one GET request: you send a URL, the platform handles proxies, rendering, CAPTCHA and retries, and you get a page or structured JSON back. Anything outside that shape is either missing or something you build yourself.

- **No first-class crawl or site map.** Async Scraper submits millions of jobs and processes them in the background, but you supply the URLs. It does not discover them for you, and there is no endpoint that returns a domain's URL inventory.

- **No screenshots and no interactive actions.** You cannot click, scroll, type, or wait for a state before capture.

- **No open-source SDK and no self-hosting.** The official SDKs cover Python, Node.js, PHP, Java, Ruby and Go, but the platform itself runs only on ScraperAPI's infrastructure.

- **No managed data delivery.** You get pages and JSON; assembling, validating and shipping the dataset is your job.

- **No AI extraction step.** `output_format` will hand you Text or Markdown, which is convenient for an LLM pipeline, but turning a page into typed fields is on your side unless you use one of the prebuilt endpoints.

On that last point, the structured data endpoints cover Amazon, Google, Walmart, eBay and Redfin and return parsed JSON without a parser on your end. If your targets sit inside that list, ScraperAPI is doing more work than a generic fetch API would. If they don't, budget engineering time for parsing, which is the cost that never shows up in a plan comparison.

## Picking by scenario

**Known URL list, mostly static HTML.** Stay. The 1-credit rate is the whole reason to be on this platform, and the entry tier handles a small pipeline without ceremony. 👉 [Buy the smallest tier that covers your page count](https://www.scraperapi.com/?fp_ref=coupons)

**Known URL list, mostly JS-rendered.** Do the 10-credit math first. At $299, 3M credits is 300,000 rendered pages, which is roughly 10,000 a day. If your volume is a tenth of that, Startup at $149 is the honest answer and Business is an upgrade you don't need yet.

**SERP monitoring.** Each Google request costs 25 credits, so the 120,000 SERP requests included in Business are the real ceiling. Compare that against a search-specific provider before deciding, because SERP pricing is where per-credit plans look worst.

**Whole-site crawling, RAG ingestion, markdown for an LLM.** Firecrawl's flat 1 credit per page with no complexity multiplier is easier to forecast, and crawl plus map are core endpoints there rather than something you script around.

**Delivering finished datasets to a client.** Zyte's managed service and Scrapy IO's pay-per-row model both take parsing off your roadmap. Neither is cheaper per request; they are cheaper per finished deliverable.

**Needing a scraper for a specific awkward site.** Apify's Actor marketplace and Bright Data's prebuilt scrapers will usually have something already written, which beats building and maintaining it.

## Before you pay: trial, refunds, and the claims to check

The 5,000-credit, 7-day trial is the highest-value thing on this page. Run your five hardest URLs through the Domain Cost Estimator during it and multiply out a month of real volume; that number, not the plan table, decides your tier. The 7-day no-questions-asked refund sits right behind it if the estimates turn out wrong.

Three things worth confirming in writing before a large commitment:

- **Geotargeting and proxy scale.** ScraperAPI states 150+ geotargeting locations and a 150M+ proxy pool, and a 99.99% success rate. Third-party comparison pages give much smaller numbers for the same proxy network (40M+ proxies, 50+ countries), and one competitor claims full-country targeting requires the $299 tier. Those figures cannot be reconciled from outside, so if a specific country is a hard requirement, get it confirmed rather than inferred from the marketing page.

- **Billing on failed requests.** ScraperAPI's stated policy is that you are charged only for successful requests, with no credits consumed by blocks, timeouts or failures. At least one competitor page claims anti-bot retries burn credits before delivering usable HTML. Test it against your own targets during the trial week, since your targets are the only ones that matter.

- **What triggers an upgrade.** Auto-upgrade and pay-as-you-go are opt-in, but they are also the difference between a paused account and a doubled bill. Decide which behaviour you want before your first month ends.

## FAQ

**Are 3 million credits 3 million pages?**

Only for 1-credit pages. At 5 to 10 credits for JavaScript rendering, 3M credits is 600,000 to 300,000 pages, and at 20 credits for sites behind hard bot protection it is 150,000.

**Can ScraperAPI crawl an entire site?**

Not as a core feature. It fetches the URLs you give it, including millions per batch through Async Scraper; discovering URLs, mapping a domain and following links is where a crawling-first tool fits better.

**Is the $49 plan enough for a small project?**

For a few thousand plain pages a month, yes. The moment most of your targets need rendering, the effective page count drops by 5 to 10 times, and the allowance runs out faster than the plan name suggests.

**Does it return data I can feed to an LLM?**

Yes. `output_format` converts pages to Text or Markdown, and there is a dedicated LangChain integration plus an MCP server, though the page-to-fields step is still yours.

**What happens when I hit the credit limit mid-month?**

Scraping pauses until the next cycle by default. Auto-upgrade moves you to the next tier automatically if you opted in, and pay-as-you-go past the cap is available on the higher plans with a spending limit you set.

---

If your work is fetching a known list of URLs and getting clean HTML or JSON back, ScraperAPI is still the right tool and the decision is purely which allowance to buy: entry tier for low volume, Startup at $149 for a million credits, Business at $299 once rendering pushes you past that. If two or more of your requirements are crawl, screenshots, managed delivery or typed rows, switch, because you are paying for a fetch API and building the rest yourself.

Either way, start inside the 7-day trial with your hardest URLs, price them with the Domain Cost Estimator, and only then pick a tier. 👉 [Start the 5,000-credit trial and pick your plan](https://www.scraperapi.com/?fp_ref=coupons)
