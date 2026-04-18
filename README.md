# FINN.no Torget Scraper

Extract structured data from [FINN.no](https://FINN.no) — classified listings from FINN.no Torget — Norway's largest marketplace. Extract prices, condition, seller info, images, locations, and full descriptions from 11 categories across all Norwegian counties.

**[Finn Torget Scraper - Norwegian Marketplace on Apify →](https://apify.com/blackfalcondata/finn-torget-scraper?fpr=1h3gvi)**

---

## Key features





**Search with filters** — Search by keyword and location. Filter by category, condition, region, and more.

**Detail enrichment** — Fetch full job descriptions, structured metadata for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 5.000). Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases





**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from finn.no on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from finn.no.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "query": "iPhone",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Search keywords (e.g. 'iPhone', 'sofa', 'sykkel'). |
| `category` | enum | `"all"` | Filter by FINN.no Torget category. |
| `condition` | enum | `"all"` | Filter by item condition. |
| `region` | enum | `"all"` | Filter by Norwegian county (fylke). |
| `priceMin` | integer | `0` | Minimum price filter. |
| `priceMax` | integer | `0` | Maximum price filter. 0 = no limit. |
| `sellerType` | enum | `""` | Filter by seller type. |
| `sortBy` | enum | `"relevance"` | Sort order for results. |
| `maxResults` | integer | `50` | Maximum total results to return. 0 = unlimited. |
| `includeDetails` | boolean | `true` | Fetch full listing details (description, images, category, attributes). Slower but more complete. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N chars. 0 = no truncation. |
| `compact` | boolean | `false` | Core fields only (for AI-agent/MCP workflows). |
| `incrementalMode` | boolean | `false` | Only return new/changed listings compared to previous run. |
| `stateKey` | string | — | Stable identifier for tracked listing universe (e.g. 'iphone-oslo'). |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape FINN.no?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->


## Output fields

Every listing returns the same 35-field schema. Missing values are `null` — never omitted.

- `listingId`
- `title`
- `description`
- `price`
- `currency`
- `condition`
- `conditionDetails`
- `brand`
- `model`
- `category`
- `categoryPath`
- `location`
- `zipCode`
- `latitude`
- `longitude`
- `imageUrl`
- `imageUrls`
- `imageCount`
- `sellerName`
- `sellerType`
- `tradeType`
- `postedAt`
- `editedAt`
- `url`
- `portalUrl`
- `sellerId`
- `isPromoted`
- `shippingAvailable`
- `freeShipping`
- `buyNowAvailable`
- `disposed`
- `isWebstore`
- `attributes`
- `scrapedAt`
- `source`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "listingId": "315dbc192dddb506799c447db1a70f6f9e2221210ed1616ce3d802bd49a01bff",
  "title": "iPhone 6S  64GB",
  "description": "iPhone 6S\n\n64GB\nBatteri kapasitet: 77\nlommebokdeksel",
  "price": 400,
  "currency": "NOK",
  "condition": "good",
  "conditionDetails": "Pent brukt - I god stand",
  "brand": "Apple",
  "model": "iPhone 2G-11",
  "category": "Mobiltelefoner",
  "categoryPath": "Elektronikk og hvitevarer > Telefoner og tilbehør > Mobiltelefoner",
  "location": "4708 Vennesla"
}
```

*Truncated — full records contain 35 fields. See Output fields for the complete schema.*


**[Try Finn Torget Scraper - Norwegian Marketplace now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/finn-torget-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/finn-torget-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data





- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal


## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---
---

*Last updated: 2026 03*
