# FINN.no Torget Scraper

Extract structured data from [FINN.no](https://FINN.no) — classified listings from FINN.no Torget — Norway's largest marketplace. Extract prices, condition, seller info, images, locations, and full descriptions from 11 categories across all Norwegian counties.

**[Finn Torget Scraper - Norwegian Marketplace on Apify →](https://apify.com/blackfalcondata/finn-torget-scraper)**

---

## Key features




**Search with filters** — Search by keyword and location. Filter by category, condition, region, and more.

**Detail enrichment** — Fetch full job descriptions, structured metadata for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases




**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from finn.no on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from finn.no.

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

---

## Related products by Black Falcon Data




- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 03*
