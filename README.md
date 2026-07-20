# SERP Scraping API Complete Guide: How to Scrape Google Search Results Without Getting Blocked — Structured Endpoints, Credit Math, Real Use Cases, and the Right Plan for Every Budget

So you want to pull Google search results into your app, your dashboard, your SEO tool — whatever the project is. You try `requests` in Python, get an HTTP 429 after about 40 queries, and suddenly realize why people keep talking about SERP scraping APIs.

Here's the thing nobody tells you upfront: building your own Google scraper isn't really the hard part. *Keeping* it working is. Google's layout shifts constantly, CAPTCHAs kick in after a handful of requests from the same IP, and the moment you add JavaScript rendering to catch AI Overviews and People Also Ask boxes, you're basically maintaining a second job just to keep data flowing.

That's where a SERP scraping API earns its keep. And if you're evaluating options right now, ScraperAPI is one of the most discussed names in this space — not because of marketing, but because it covers a lot of ground at a price point that doesn't require a VC's blessing to justify.

Let's walk through how SERP API scraping actually works, what the real costs look like, and whether ScraperAPI's structured Google endpoints fit your workflow.

---

## **What a SERP Scraping API Actually Does (And Why You Need One)**

At its core, a SERP scraping API is infrastructure you rent instead of building. You send it a search query, it fires the request through a rotating proxy pool, solves whatever CAPTCHA Google throws at it, renders the JavaScript if needed, parses the HTML, and hands you back clean JSON.

The alternative is managing all of that yourself:

- **Proxy rotation**: A pool of IPs that cycles automatically so Google doesn't flag your requests
- **CAPTCHA solving**: Either a third-party solver service or a headless browser approach
- **JavaScript rendering**: A headless Chrome instance to catch dynamically loaded content
- **Parser maintenance**: Your CSS selectors break every time Google updates its layout

Google removed the `num=100` parameter in September 2025, which means every scraper now has to paginate through 10 results at a time to reach deeper positions. AI Overviews are now appearing on roughly half of all tracked queries. And Google's official Custom Search JSON API is being sunset by January 2027. The infrastructure problem got harder, not easier.

A good SERP scraping API handles all of that under the hood. You call a URL, you get data.

> **Why ScraperAPI specifically?** It's one of the few services that includes structured Google endpoints — returning parsed JSON with organic results, ads, featured snippets, knowledge panels, related questions, and pagination — on every plan with no extra fees. The proxy pool is 40M+ IPs across 50+ countries with a 99.9% uptime SLA.

👉 [Start a free 7-day trial — 5,000 credits, no card required](https://www.scraperapi.com/?fp_ref=coupons)

---

## **ScraperAPI's Google SERP Endpoint: How It Works in Practice**

ScraperAPI exposes a dedicated structured endpoint for Google Search data:


GET https://api.scraperapi.com/structured/google/search


The response is clean JSON — organic results, knowledge graph, PAA, related searches, video results, pagination — all parsed and ready to use. Here's what a basic call looks like across the main languages:

**Python:**
python
import requests

payload = {
    "api_key": "YOUR_API_KEY",
    "query": "best running shoes 2026",
    "country_code": "us",
    "tld": "com"
}

response = requests.get(
    'https://api.scraperapi.com/structured/google/search',
    params=payload
)
print(response.json())


**Node.js:**
javascript
import fetch from 'node-fetch';

fetch(`https://api.scraperapi.com/structured/google/search?api_key=YOUR_API_KEY&query=best+running+shoes+2026&country_code=us&tld=com`)
  .then(res => res.json())
  .then(data => console.log(data));


**cURL:**
bash
curl --request GET \
  --url "https://api.scraperapi.com/structured/google/search?api_key=YOUR_API_KEY&query=best+running+shoes+2026&country_code=us&tld=com"


The response includes an `organic_results` array with position, title, snippet, and link — plus `related_questions`, `knowledge_graph`, `videos`, and `pagination` objects when they're present on the page.

### **Supported Parameters**

ScraperAPI's Google SERP endpoint gives you serious targeting flexibility:

| Parameter | What It Does | Example Value |
|---|---|---|
| `query` | Your search query | `"best SERP API 2026"` |
| `country_code` | Geotarget the results | `us`, `gb`, `de`, `au` |
| `tld` | Which Google domain to scrape | `com`, `co.uk`, `de`, `com.br` |
| `uule` | Region-level targeting | UULE-encoded location string |
| `hl` | Host/interface language | `en`, `de`, `fr` |
| `gl` | Country boost for results | `us`, `gb` |
| `tbs` | Time filter | `d` (day), `w` (week), `m` (month) |
| `start` | Pagination offset | `10` for page 2, `20` for page 3 |
| `output_format` | Response format | `json` (default) or `csv` |

Supported Google TLDs include `.com`, `.co.uk`, `.ca`, `.de`, `.es`, `.fr`, `.it`, `.co.jp`, `.in`, `.cn`, `.com.sg`, `.com.mx`, `.ae`, `.com.br`, `.nl`, `.com.au`, `.com.tr`, `.sa`, `.se`, and `.pl` — covering the major search markets.

---

## **Understanding the Credit System: The Math That Actually Matters**

Here's where a lot of people get caught off guard. ScraperAPI's pricing page shows credits per month. But *how many credits does a Google SERP request actually cost?*

The answer: **25 credits per Google Search request.**

This is the single most important number to know before choosing a plan. A "100,000 credits" plan gets you roughly **4,000 Google SERP calls**, not 100,000. That's a huge difference in planning.

Here's the full credit multiplier breakdown:

| Target Type | Credits Per Request |
|---|---|
| Standard (unprotected HTML) | 1 |
| E-commerce (Amazon, Walmart, etc.) | 5 |
| Google / Bing / Search Engines | **25** |
| LinkedIn | 30 |
| Cloudflare/DDoS-protected sites (extra) | +10 |

Optional parameters add on top of the base cost:

| Parameter | Additional Credits |
|---|---|
| `premium=true` | +10 |
| `render=true` (JS rendering) | +10 |
| `ultra_premium=true` | +30 |
| `screenshot=true` | +10 |

One genuinely good thing: **you only pay for successful requests**. Failed scrapes (anything that doesn't return a 200 or 404) don't burn credits. That's a meaningful protection on difficult targets.

For SERP-specific work, here's what you can realistically expect per plan per month:

| Plan | Credits/Month | Google SERP Requests/Month |
|---|---|---|
| Hobby | 100,000 | ~4,000 |
| Startup | 1,000,000 | ~40,000 |
| Business | 3,000,000 | ~120,000 |
| Scaling | 5,000,000 | ~200,000 |
| Professional | 10,500,000 | ~420,000 |
| Advanced | 21,500,000 | ~860,000 |

Run your own math against those numbers before picking a plan. The dashboard includes a Domain Cost Estimator that shows the credit cost for any specific URL before you commit.

---

## **ScraperAPI Plans: Full Comparison Table**

Here's the complete current lineup. All plans include JS rendering, CAPTCHA bypass, automatic retries, rotating proxies, unlimited bandwidth, and a 99.9% uptime guarantee. The differences are volume, concurrency, and geotargeting scope.

| Plan | Monthly Price | Annual Price | Credits/Month | Concurrent Threads | Geotargeting | Purchase |
|---|---|---|---|---|---|---|
| **Free Trial** | $0 (7 days) | — | 5,000 | 5 | Limited |  [Start Free Trial](https://www.scraperapi.com/?fp_ref=coupons) |
| **Hobby** | $49/mo | $44.10/mo | 100,000 | 20 | US & EU only |  [Get Hobby Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Startup** | $149/mo | $134.10/mo | 1,000,000 | 50 | US & EU only |  [Get Startup Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Business** | $299/mo | $269.10/mo | 3,000,000 | 100 | Global |  [Get Business Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Scaling** *(Most Popular)* | $475/mo | $427.50/mo | 5,000,000 | 200 | Global |  [Get Scaling Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Professional** | $975/mo | $877.50/mo | 10,500,000 | 300 | Global |  [Get Professional Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Advanced** | $1,975/mo | $1,777.50/mo | 21,500,000 | 500 | Global |  [Get Advanced Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Enterprise** | Custom | Custom | 22M+ | 500+ | Global |  [Contact Sales](https://www.scraperapi.com/?fp_ref=coupons) |

**Things worth noting that aren't obvious from the numbers:**

- **Geotargeting is gated.** Hobby and Startup are US & EU proxies only. If your SERP work requires location-specific results in APAC, Latin America, or the Middle East, you need Business or higher.
- **Pay-as-you-go overflow** is only available on Scaling, Professional, Advanced, and Enterprise. On lower tiers, hitting your credit ceiling mid-month means upgrading or waiting — no soft overflow.
- **Credits don't roll over.** Use them or lose them at each renewal cycle.
- **Analytics history**: Hobby and Startup are capped at 30 days. Business and above get unlimited history.
- **May 2026 update**: ScraperAPI introduced Professional and Advanced as "Growth" plans with bonus credits — Professional includes 250K bonus credits and Advanced includes 500K bonus credits as a limited-time offer.

Annual billing saves 10% across all plans — no code needed, applied automatically at checkout.

---

## **Real Use Cases: What People Actually Use SERP Scraping APIs For**

The abstract "collect search data" pitch doesn't tell you much. Here are the concrete workflows where a SERP scraping API like ScraperAPI actually moves the needle:

**SEO rank tracking at scale.** Instead of logging into a tool manually or paying per-keyword fees to a rank tracker SaaS, teams use the SERP API to pull positions for their entire keyword set on a schedule. At 200,000+ SERP requests per month on the Scaling plan, that's a lot of keyword/location combinations you can monitor in-house.

**Competitive intelligence.** Which paid ads is your competitor running? What's their organic snippet copy? Are they picking up featured snippets you're not? The SERP API's structured JSON includes ad data, featured snippets, and People Also Ask boxes — not just organic ten-blue-links.

**AI agent grounding.** Increasingly, teams building LLM-powered tools need to give their agents real-time search context. A SERP scraping API becomes the "browse" capability — fire a query, get structured results, pass them to the model. The async scraper handles millions of such requests without blocking.

**Local SERP monitoring.** For multi-location businesses or agencies managing local SEO, the `country_code` and `uule` parameters let you pull genuinely localized results — what a searcher in Munich actually sees vs. what someone in Berlin sees, for the same query.

**Content gap analysis.** Pull the top 10 results for a target keyword, scrape the "related questions" and "people also ask" arrays from the JSON, and you've got a ready-made content brief without clicking through each result manually.

---

## **Hobby vs. Startup vs. Business: Which Plan Should You Pick?**

The honest answer depends on what you're actually scraping and how often. Here's a practical breakdown:

**Pick Hobby ($49/mo) if:** You're running a personal project, testing a new tool idea, or doing occasional SERP checks — maybe 50–100 keyword rank checks per day. At 25 credits per SERP request, your 100K credits get you roughly 4,000 Google queries per month. For a solo developer or a small side project, that's workable.

**Pick Startup ($149/mo) if:** You're building a real product — maybe a small SaaS rank tracker, or an agency doing SEO audits for a handful of clients. 40,000 SERP requests per month with 50 concurrent threads is enough to run meaningful tracking workflows. Just note the US/EU geotargeting cap.

**Pick Business ($299/mo) if:** You need global geotargeting — that's the unlock. Any SERP work requiring country-specific results outside the US and EU requires this tier or above. You also get 120,000 SERP requests per month and 100 concurrent threads, which covers serious production workloads.

**Pick Scaling or above if:** You're past the "which plan" question and into the "how do we scale this without surprising bills" question. The pay-as-you-go overflow on Scaling ensures you never get hard-capped mid-month.

> Starting out? ScraperAPI's 7-day free trial gives you 5,000 credits — enough to fire real SERP requests at actual targets and see what your credit consumption rate looks like before committing to anything.

👉 [Claim your free trial here — no credit card needed](https://www.scraperapi.com/?fp_ref=coupons)

---

## **ScraperAPI vs. Other SERP Scraping APIs: Honest Comparison**

The market has real alternatives. Here's how they stack up for SERP-focused work:

| Tool | Best For | SERP Pricing | Free Trial |
|---|---|---|---|
| **ScraperAPI** | Structured Google endpoints + full scraping toolkit | $49/mo (25 credits/SERP) | 5,000 credits, 7-day |
| **SerpApi** | Widest engine coverage (80+ engines) | $75/mo (~$15/1k SERPs) | 250 searches/mo |
| **Serper** | Fast, cheap Google for AI agents | ~$0.30–$1/1k SERPs | 2,500 searches |
| **DataForSEO** | Bulk SERP at lowest base rate | $0.60–$2/1k | $1 credit |
| **Bright Data** | Enterprise multi-engine reliability | $1.00–$1.50/1k | $5 credit |
| **Scrapingdog** | Budget all-rounder, fast | $40/mo | 1,000 credits |
| **Decodo** | Cheap Google + Bing | $19/mo | $1/14-day |

**Where ScraperAPI wins:** You're not just buying a SERP API — you're buying a full scraping stack. The same plan that handles your Google SERP queries also handles Amazon product pages, Bing, Walmart, LinkedIn, and practically any other URL you throw at it. If your workflow mixes SERP data with e-commerce or general web scraping, that consolidation has real value.

**Where competitors may win:** If you need engines beyond Google (Yandex, Baidu, Yahoo, Bing in depth), SerpApi's catalog is broader. If your budget is tight and you *only* need plain Google organic results, Serper or Decodo undercut ScraperAPI's effective per-SERP cost. For true pay-as-you-go without any monthly commitment, DataForSEO offers the lowest base rate.

The honest take: ScraperAPI makes the most sense for teams doing a mix of SERP work alongside broader scraping — or for developers who want one integration that covers everything without managing multiple vendors.

---

## **Getting Started: Step-by-Step from Zero to First SERP Result**

If you've decided to try it, here's the fastest path from signup to data:

**Step 1: Start the free trial.** Sign up at ScraperAPI — no credit card required. You'll land in the dashboard with your API key and 5,000 trial credits.

**Step 2: Find your API key.** It's on the dashboard home page. Copy it.

**Step 3: Fire a test request.** Drop this into your terminal, swapping in your API key and query:

bash
curl "https://api.scraperapi.com/structured/google/search?api_key=YOUR_KEY&query=serp+scraping+api&country_code=us&tld=com"


**Step 4: Check the response.** You'll see a JSON object with `organic_results`, `related_questions`, `knowledge_graph`, and `pagination`. That's real Google SERP data, structured and ready.

**Step 5: Check your credit usage.** The dashboard shows a running credit total. For a Google SERP request, you'll see 25 credits deducted per successful call.

**Step 6: Use the Domain Cost Estimator.** Before scaling up, plug your target URLs into the cost estimator in the dashboard to calculate your real per-request cost. This prevents the mid-month surprise.

**Step 7: Choose a plan.** Based on your trial consumption rate, pick the tier that matches your actual monthly volume — not your theoretical max.

---

## **Common Questions About SERP Scraping APIs**

**Is scraping Google search results legal?**
Public search results are publicly accessible. Most SERP APIs — including ScraperAPI — are built to scrape public-facing data. ScraperAPI is GDPR and CCPA compliant and does not scrape behind authentication or target private data.

**Why did my Google request cost more than 25 credits?**
If you added parameters like `render=true` (+10) or `premium=true` (+10), those stack on top of the base 25. Always check the credit estimator before running large batches.

**What happens when I run out of credits mid-month?**
On Hobby, Startup, and Business plans: requests stop until you upgrade or the cycle renews. On Scaling, Professional, Advanced, and Enterprise: pay-as-you-go overflow kicks in at a fixed rate so your pipeline keeps running.

**Can I get country-specific Google results?**
Yes — with the `country_code` and `tld` parameters. For example, `country_code=de&tld=de` gives you results as seen from Germany on google.de. Global geotargeting requires the Business plan or higher.

**Is there a discount?**
Annual billing automatically applies a 10% discount — no coupon code needed. That drops the Hobby plan from $49 to $44.10/month, and Scaling from $475 to $427.50/month.

---

## **The Bottom Line**

If you're building anything that depends on Google search data — rank tracking, competitive intelligence, content research, AI agent grounding, lead generation — a SERP scraping API is the only sane approach at anything beyond a hobby-project scale.

ScraperAPI's structured Google SERP endpoint delivers clean, parsed JSON for every query, with geotargeting, pagination control, and time filters built in. The 25-credit-per-request cost is the number to plan around — once you've run the math against your monthly query volume, the right plan becomes obvious.

The free trial is the easiest starting point. Five thousand credits, seven days, no credit card. Point it at your actual targets, watch what the credit meter does, and you'll have a much clearer picture of what you actually need before spending a dollar.

👉 [Start your free ScraperAPI trial — 5,000 credits, no card required](https://www.scraperapi.com/?fp_ref=coupons)
