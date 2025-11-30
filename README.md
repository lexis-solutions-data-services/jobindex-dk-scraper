# Jobindex.dk Scraper

![banner](https://i.imgur.com/82kMocZ.png)

Welcome to the Jobindex.dk Scraper! This actor extracts job listings and details from Jobindex.dk, Denmark’s leading job portal. Use it to collect fresh postings including titles, company info, locations, and metadata such as application links and company ratings.

<p align="center">
  <img src="https://apify-image-uploads-prod.s3.us-east-1.amazonaws.com/DevbkY3adMTBuoECt-actor-3TyLksAsGspYJPKj8-Y9r1IJjJas-Screenshot_2025-11-18_at_10.22.01.png" alt="Jobindex.dk Scraper" style="height: 60px; margin-right: 15px;" /><a href="https://apify.com/lexis-solutions/jobindex-dk-scraper" target="_blank">
    <img src="https://img.shields.io/badge/Try%20it%20on-Apify-0066FF?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNDA4IiBoZWlnaHQ9IjQwOCIgdmlld0JveD0iMCAwIDQwOCA0MDgiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxnIGNsaXAtcGF0aD0idXJsKCNjbGlwMF8zNDFfNDE1NykiPgo8cGF0aCBkPSJNMjE4LjY5NSAxMDRIMzAwLjk3QzMwMi42NDMgMTA0IDMwNCAxMDUuMzU3IDMwNCAxMDcuMDNWMjMyLjc2NkMzMDQgMjM1Ljc3OCAzMDAuMDgzIDIzNi45NDUgMjk4LjQzNCAyMzQuNDI1TDIxNi4xNTkgMTA4LjY5QzIxNC44NDEgMTA2LjY3NCAyMTYuMjg3IDEwNCAyMTguNjk1IDEwNFoiIGZpbGw9IndoaXRlIi8+CjxwYXRoIGQ9Ik0xODkuMzA1IDEwNEgxMDcuMDNDMTA1LjM1NyAxMDQgMTA0IDEwNS4zNTcgMTA0IDEwNy4wM1YyMzIuNzY2QzEwNCAyMzUuNzc4IDEwNy45MTcgMjM2Ljk0NSAxMDkuNTY2IDIzNC40MjVMMTkxLjg0IDEwOC42OUMxOTMuMTU5IDEwNi42NzQgMTkxLjcxMyAxMDQgMTg5LjMwNSAxMDRaIiBmaWxsPSJ3aGl0ZSIvPgo8cGF0aCBkPSJNMjAyLjU5MSAyMDQuNjY4TDEwOS4xMjcgMjk4LjgzNUMxMDcuMjI5IDMwMC43NDcgMTA4LjU4MyAzMDQgMTExLjI3OCAzMDRIMjk2LjhDMjk5LjQ4MyAzMDQgMzAwLjg0MiAzMDAuNzcgMjk4Ljk2NyAyOTguODUyTDIwNi45MDggMjA0LjY4NUMyMDUuNzI2IDIwMy40NzUgMjAzLjc4MiAyMDMuNDY4IDIwMi41OTEgMjA0LjY2OFoiIGZpbGw9IndoaXRlIi8+CjwvZz4KPGRlZnM+CjxjbGlwUGF0aCBpZD0iY2xpcDBfMzQxXzQxNTciPgo8cmVjdCB3aWR0aD0iMjAwIiBoZWlnaHQ9IjIwMCIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEwNCAxMDQpIi8+CjwvY2xpcFBhdGg+CjwvZGVmcz4KPC9zdmc+Cg==&logoColor=white" alt="Try it on Apify" style="border-radius: 12px; height: 60px;" />
  </a>
</p>


## Introduction

## 📊 Actor Stats

| Stat | Value |
|------|-------|
| **Version** | `0.0.1` |
| **Last Update** | Nov 30, 2025 |

---



The Jobindex.dk scraper crawls Danish job listings. Supply listing URLs from Jobindex search pages and it will paginate through results, capturing structured job data and basic company metrics.

## Use Cases

- **Job Market Research**: Analyze roles and hiring trends across Denmark.
- **Recruitment Enrichment**: Feed ATS/CRMs with structured postings.
- **Competitor Monitoring**: Track company hiring activity by location or sector.
- **Data Aggregation**: Build dashboards for geography, posting dates, or employer activity.

## Input 😎

Provide the following fields:

- `startUrls` (array, required): Jobindex listing URLs to start from. Example: `{ "url": "https://www.jobindex.dk/jobsoegning/undervisning/paedagog/nordsjaelland" }`
- `maxItems` (integer, required): Maximum number of items to extract (default: 10).
- `proxyConfiguration` (object, optional): Apify proxy configuration. Example: `{ "useApifyProxy": false }`

Notes:

- Use Jobindex search/listing URLs. Links outside the domain are skipped.
- The crawler stops when `maxItems` is reached or no more results are available.
- Data is collected only from search/list pages; individual job detail pages lead to external domains and are not scraped.
- Start URLs pointing directly to a job detail page are ignored—use search/listing URLs instead.

## Input Example

```json
{
  "startUrls": [
    {
      "url": "https://www.jobindex.dk/jobsoegning/undervisning/paedagog/nordsjaelland"
    }
  ],
  "maxItems": 25,
  "proxyConfiguration": {
    "useApifyProxy": false
  }
}
```

## Output 😎

Each dataset item contains fields like:

```json
{
  "title": "Erfaren pædagogmedhjælper til vuggestuen i naturskønne Farum Vejgaard",
  "url": "https://www.jobindex.dk/c?t=h1613745&ctx=w&jobsearch_position=1&jobsearchid=963426864",
  "originalUrl": "https://furesoe-1.career.emply.com/ad/erfaren-paedagogmedhjaelper-til-vuggestuen-i-naturskonne-farum-vejgaard/pb55f6/da",
  "city": "Farum",
  "adressLine": "Stavnsholtvej 170A",
  "zipcode": "3520",
  "fullAddress": "Farum Vejgård, Stavnsholtvej 170A, 3520 Farum",
  "appApplyUrl": "https://furesoe-1.career.emply.com/apply/erfaren-paedagogmedhjaelper-til-vuggestuen-i-naturskonne-farum-vejgaard/pb55f6#jobdk",
  "applyDeadlineAsap": false,
  "applyUrl": "https://www.jobindex.dk/c?t=e5912055&ctx=w&u=22272070&f=jobdk",
  "area": "Farum",
  "companyName": "Furesø Kommune",
  "companyUrl": "https://www.jobindex.dk/virksomhed/28191/furesoe-kommune#om-virksomhed",
  "companyFollower": 825,
  "distance": null,
  "firstdate": "2025-11-14",
  "lastdate": "2025-11-27",
  "isArchived": false,
  "hasSpo": false,
  "homeWorkPlace": false,
  "isLocal": false,
  "listlogoUrl": "https://www.jobindex.dk/img/logo/furesoekommune.jpg",
  "quickapplyClientId": 2,
  "rating": 211,
  "score": 4,
  "shareUrl": "https://www.jobindex.dk/vis-job/h1613745",
  "tid": "h1613745",
  "description": "Vi søger en ny pædagogmedhjælper til vores charmerende og hyggelige vuggestue..."
}
```

The scraper paginates through results and stops when there are no more jobs or when `maxItems` is reached.

## Why use the Jobindex.dk Scraper?

- 🚀 **Fast**: Efficient crawling with smart pagination.
- 😀 **Easy to use**: Start from listing URLs—no extra setup.
- 💪 **Reliable**: Built on Apify Actors and Crawlee (Cheerio).
- 🧭 **Flexible**: Works with any Jobindex search URL.
- 🧠 **Comprehensive**: Captures links, company metrics, and descriptions.
- 🇩🇰 **Denmark-focused**: Optimized for the Danish job market.

## FAQ 🙋

- **How many jobs can it extract?**  
  Set `maxItems` to limit results; the scraper will attempt to fetch all available jobs until the limit or list ends.

- **What if the website changes?**  
  Site changes may require updates. Please report issues or request updates.

- **Does it support proxies?**  
  Yes. Configure `proxyConfiguration` to route traffic through your preferred proxies.

- **Which URLs should I use?**  
  Provide Jobindex search/listing URLs (e.g., `/jobsoegning/...`). Off-domain links are ignored.

## Need to scrape other job platforms?

Check out our other job scrapers on Apify:

- [Jobs.ch Scraper](https://apify.com/lexis-solutions/jobs-ch-scraper)
- [Jobs.cz Scraper](https://apify.com/lexis-solutions/jobs-cz-scraper)
- [VDAB.be Scraper](https://apify.com/lexis-solutions/vdab-be-scraper)
- [Jobs Ireland Scraper](https://apify.com/lexis-solutions/jobs-ireland-ie-scraper)
- [Job Jobnet DK Scraper](https://apify.com/lexis-solutions/job-jobnet-dk-scraper)
- [Tyomarkkinatori.fi Scraper](https://apify.com/lexis-solutions/tyomarkkinatori-fi-scraper)
- [AMS Austria Jobs Scraper](https://apify.com/lexis-solutions/jobs-ams-at-scraper)

---

🤝 **Need help or want a custom solution?**

Lexis Solutions is a certified Apify Partner. We can help with custom data extraction projects.

Contact us over [Email](mailto:scraping@lexis.solutions) or [LinkedIn](https://www.linkedin.com/company/lexis-solutions)

## Support Our Work 🙏

If you're happy with our work and scrapers, you're welcome to leave us a company review [here](https://apify.com/partners/find/lexis-solutions/review) and leave a review for the scrapers you're subscribed to. It will take you less than a minute but it will mean a lot to us!
