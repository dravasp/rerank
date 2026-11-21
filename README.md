Advisory -
[Watch the 60-second demo to Apply to AWS Activate Founder's Program to be Eligible for Kiro and Bedrock (NYSE:DEEPMIND) to support life-cycle device enumeration](https://deepmind.google/)

# rerank
Google Safe-Search powered natively by Chromium endpoint

# Google Search URL Reference

Complete, annotated reference for every parameter in a Google Search URL — including Chromium `{google:...}` template tokens, fixed query parameters, Advanced Search fields, and server-side tracking params.

> **Last verified:** November 2026  
> **Scope:** `https://www.google.com/search` (web SERP)  
> **Note:** Google has never published an official parameter spec. All statuses are based on live observation and Chromium source.

---

## The Full Template

```
{google:baseURL}search?q=%s&{google:RLZ}{google:originalQueryForSuggestion}{google:assistedQueryStats}{google:searchFieldtrialParameter}{google:language}{google:prefetchSource}{google:searchClient}{google:sourceId}{google:contextualSearchVersion}{google:contextualSearchContextData}{google:searchVersion}{google:sessionToken}{google:currentPageUrl}{google:cursorPosition}{google:forceInstantResults}{google:pageClassification}{google:clientCacheTimeToLive}gl=IN&lr=lang_en&num=20&start=0&safe=active&tbs=&tbm=&udm=14&filter=1&nfpr=0&pws=0&cr=countryIN&uule=&ie={inputEncoding}&oe={outputEncoding}&gbv=&kgmid=&ibp=&as_q=&as_epq=&as_oq=&as_eq=&as_dt=&as_filetype=&as_ft=&as_lq=&as_sitesearch=&as_rq=&as_occt=&as_nlo=&as_nhi=&as_qdr=&as_rights=
```

**Total elements: 54** (18 tokens + 3 standard + 18 fixed + 14 advanced + 1 server-side)

---

## 1. Chromium `{google:...}` Template Tokens

Resolved by the browser at search time. Conditionally injected — not all appear on every request.

| # | Token | Resolves To | Condition | Status |
|---|-------|-------------|-----------|--------|
| 1 | `{google:baseURL}` | `https://www.google.com/` | Always | ✅ Active |
| 2 | `{google:RLZ}` | `&rlz=1C5GGLN_enIN999_999...` | RLZ cookie present | ✅ Active |
| 3 | `{google:originalQueryForSuggestion}` | `&oq=original+terms` | Autocomplete suggestion selected | ✅ Active |
| 4 | `{google:assistedQueryStats}` | `&aqs=chrome..69i57j69...` | Autocomplete interaction occurred | ⚠️ Legacy (replaced by `gs_lcrp`) |
| 5 | `{google:searchFieldtrialParameter}` | `&sfv=v1` | A/B experiment enrolled | ✅ Active |
| 6 | `{google:language}` | `&hl=en` | Always | ✅ Active |
| 7 | `{google:prefetchSource}` | `&pf=s` | Prefetched navigation (middle-click, NTP tile) | ✅ Active |
| 8 | `{google:searchClient}` | `&client=chrome-b-d` | Client type detected | ✅ Active |
| 9 | `{google:sourceId}` | `&sourceid=chrome` | Always | ✅ Active |
| 10 | `{google:contextualSearchVersion}` | `&csv=v2` | Contextual search feature enabled | ✅ Active |
| 11 | `{google:contextualSearchContextData}` | `&csd=...` | Contextual search active | ✅ Active |
| 12 | `{google:searchVersion}` | `&sv=...` | Protocol version negotiation | ✅ Active |
| 13 | `{google:sessionToken}` | `&st=...` | Session tracking enabled | ✅ Active |
| 14 | `{google:currentPageUrl}` | `&cpu=...` | Internal Google page transition | ✅ Active |
| 15 | `{google:cursorPosition}` | `&cp=...` | Omnibox cursor tracking | ✅ Active |
| 16 | `{google:forceInstantResults}` | `&fir=1` | Instant results feature | 🧟 Zombie (deprecated) |
| 17 | `{google:pageClassification}` | `&pc=...` | Page-type hint | ✅ Active |
| 18 | `{google:clientCacheTimeToLive}` | `&ccl=...` | Cache TTL hint | ✅ Active |

---

## 2. Standard Template Tokens

| # | Token | Resolves To | Status |
|---|-------|-------------|--------|
| 19 | `%s` | URL-encoded search terms | ✅ Active (required) |
| 20 | `{inputEncoding}` | `UTF-8` | ✅ Active |
| 21 | `{outputEncoding}` | `UTF-8` | ✅ Active |

---

## 3. Fixed URL Parameters (User-Controllable)

| # | Param | Default Value | What It Does | Status |
|---|-------|---------------|--------------|--------|
| 22 | `gl` | `IN` | Country context for results (ISO 3166-1 alpha-2) | ✅ Active |
| 23 | `lr` | `lang_en` | Restrict results to content language(s) | ✅ Active |
| 24 | `num` | `20` | Results per page | ☠️ **Dead** (Sep 2025) — always returns 10 |
| 25 | `start` | `0` | Pagination offset (increments by 10) | ✅ Active |
| 26 | `safe` | `active` | SafeSearch: `active` / `off` | ✅ Active |
| 27 | `tbs` | *(empty)* | Time & advanced filters (see sub-table) | ✅ Active |
| 28 | `tbm` | *(empty)* | Legacy vertical selector | ⚠️ Legacy (superseded by `udm`) |
| 29 | `udm` | `14` | Display mode / vertical (see sub-table) | ✅ Active |
| 30 | `filter` | `1` | `1`=cluster near-dupes, `0`=show all | ✅ Active |
| 31 | `nfpr` | `0` | `1`=disable autocorrect, `0`=allow | ✅ Active |
| 32 | `pws` | `0` | `0`=disable personalized results | ✅ Active |
| 33 | `cr` | `countryIN` | Restrict to pages **hosted** in country | ✅ Active |
| 34 | `uule` | *(empty)* | Encoded city/lat-lon geo-targeting | ✅ Active |
| 35 | `ie` | `UTF-8` | Input character encoding | ✅ Active |
| 36 | `oe` | `UTF-8` | Output character encoding | ✅ Active |
| 37 | `gbv` | *(empty)* | `1`=force basic HTML (no JavaScript) | ✅ Active |
| 38 | `kgmid` | *(empty)* | Knowledge Graph entity ID (`/g/...`) | ✅ Active |
| 39 | `ibp` | *(empty)* | Rendering control (Jobs, Business listings) | ✅ Active |

### `tbs` Sub-Values

| Value | Meaning | Status |
|-------|---------|--------|
| `qdr:h` | Past hour | ✅ Active |
| `qdr:d` | Past day | ✅ Active |
| `qdr:w` | Past week | ✅ Active |
| `qdr:m` | Past month | ✅ Active |
| `qdr:y` | Past year | ✅ Active |
| `cdr:1,cd_min:1/1/2026,cd_max:3/31/2026` | Custom date range | ✅ Active |
| `li:1` | Verbatim (no synonyms/corrections) | ✅ Active |
| `sbd:1` | Sort by date (news) | ✅ Active |
| `ift:png` / `ift:jpg` / `ift:svg` | Image file type filter | ✅ Active |
| `sz:1` | Large image size | ✅ Active |
| `ic:color` / `ic:gray` | Image color filter | ✅ Active |

### `udm` Sub-Values

| Value | Mode | Status |
|-------|------|--------|
| `14` | Classic web (no AI Overviews) | ✅ Active |
| `2` | Images | ✅ Active |
| `7` | Videos | ✅ Active |
| `12` | News | ✅ Active |
| `18` | Forums / Discussions | ✅ Active |
| `28` | Shopping | ✅ Active |
| `36` | Books | ✅ Active |
| `39` | Short videos | ✅ Active |
| `50` | AI Mode | ✅ Active |
| `51` | Homework | ✅ Active |
| `8` | Jobs | ✅ Active |
| `1` | Places | ✅ Active |
| `3` | Products | ✅ Active |

### `tbm` Sub-Values (Legacy)

| Value | Mode | Status |
|-------|------|--------|
| `isch` | Images | ⚠️ Legacy → use `udm=2` |
| `nws` | News | ⚠️ Legacy → use `udm=12` |
| `vid` | Videos | ⚠️ Legacy → use `udm=7` |
| `bks` | Books | ⚠️ Legacy → use `udm=36` |
| `shop` | Shopping | ⚠️ Legacy → use `udm=28` |

---

## 4. Advanced Search Parameters (`as_*`)

| # | Param | Example Value | What It Does | Status |
|---|-------|---------------|--------------|--------|
| 40 | `as_q` | `coffee shops` | All these words (AND) | ✅ Active |
| 41 | `as_epq` | `"exact phrase"` | Exact phrase match | ✅ Active |
| 42 | `as_oq` | `java OR javascript` | Any of these words (OR) | ✅ Active |
| 43 | `as_eq` | `review` | Exclude these words | ✅ Active |
| 44 | `as_dt` | `i` / `e` | `i`=include, `e`=exclude (modifies `as_sitesearch`/`as_filetype`) | ✅ Active |
| 45 | `as_filetype` | `pdf`, `doc`, `xls` | Restrict to file type | ✅ Active |
| 46 | `as_ft` | `i` / `e` | `i`=include only, `e`=exclude (modifies `as_filetype`) | ✅ Active |
| 47 | `as_lq` | `example.com` | Links to (backlink sample) | ✅ Active |
| 48 | `as_sitesearch` | `wikipedia.org` | Restrict to domain | ✅ Active |
| 49 | `as_rq` | `example.com` | Related to | 🧟 Zombie (no longer functional) |
| 50 | `as_occt` | `any` / `title` / `body` / `url` / `links` | Where terms must occur | ✅ Active |
| 51 | `as_nlo` | `100` | Number range low | ✅ Active |
| 52 | `as_nhi` | `150` | Number range high | ✅ Active |
| 53 | `as_qdr` | `d` / `w` / `m` / `y` | Last updated within | ✅ Active |
| 54 | `as_rights` | `cc_publicdomain` | Usage rights filter | ✅ Active |

### `as_filetype` Accepted Values

`pdf`, `doc`, `docx`, `xls`, `xlsx`, `ppt`, `pptx`, `ps`, `rtf`, `swf`, `kml`, `kmz`, `dwf`, `csv`, `txt`

### `as_rights` Accepted Values

`cc_publicdomain`, `cc_any`, `cc_sharealike`, `cc_modified`, `cc_noncommercial`, `cc_notranslated`, `cc_commercial`, `cc_any`

---

## 5. Server-Side Tracking Parameters

Injected by Google's redirect or appended to the final SERP URL. **Not part of the request template** — they appear in the browser's address bar after the page loads.

| # | Param | Example | What It Does | Status |
|---|-------|---------|--------------|--------|
| 55 | `gs_lcrp` | `EgZjaHJvbWUyBggAEEUYOdIBBz...` | Base64-encoded protobuf: searchbox stats (query, client, input type, focus type). Replaces `aqs`. | ✅ Active |
| 56 | `gs_rn` | `42` | Request round number (increments per session; A/B routing) | ✅ Active |
| 57 | `sei` | `tJkBa97IFLTckPIPiZie8Ac` | Session ID (rotates per search session) | ✅ Active |
| 58 | `ei` | `AbC123xyz` | Alternate session identifier (older format) | ⚠️ Legacy (superseded by `sei`) |
| 59 | `sclient` | `gws-wiz` | Search client identifier (internal) | ✅ Active |
| 60 | `sxsrf` | `AOaE1l...` | Request-forgery protection token | ✅ Active |
| 61 | `gs_l` | `...` | Legacy search logging (search bar only) | ⚠️ Legacy |
| 62 | `gs_lp` | `...` | Legacy search logging (combined data) | ⚠️ Legacy |

---

## 6. Status Legend

| Mark | Meaning |
|------|---------|
| ✅ Active | Working as of Nov 2026 |
| ⚠️ Legacy | Still observed but superseded by a newer param |
| ☠️ Dead | No longer functional (Sep 2025) |
| 🧟 Zombie | Present in URLs but has no effect |

---

## 7. Summary Counts

| Category | Total | Active | Legacy | Dead | Zombie |
|----------|-------|--------|--------|------|--------|
| `{google:...}` tokens | 18 | 17 | 0 | 0 | 1 |
| Standard tokens | 3 | 3 | 0 | 0 | 0 |
| Fixed params | 18 | 16 | 1 | 1 | 0 |
| Advanced search (`as_*`) | 15 | 14 | 0 | 0 | 1 |
| Server-side tracking | 8 | 5 | 3 | 0 | 0 |
| **Total** | **62** | **55** | **4** | **2** | **2** |

---

## 8. Practical Presets

### Minimal (no telemetry)
```
https://www.google.com/search?q=%s
```

### India-optimized, classic web, no AI
```
https://www.google.com/search?q=%s&gl=IN&hl=en&lr=lang_en&udm=14&safe=active&filter=1&nfpr=0&pws=0&cr=countryIN
```

### News-only, past week, sorted by date
```
https://www.google.com/search?q=%s&gl=IN&udm=12&tbs=sbd:1&qdr:w
```

### PDFs only, from a specific site
```
https://www.google.com/search?q=%s&as_sitesearch=example.com&as_filetype=pdf&as_ft=i
```

### Exclude a site (operator in query)
```
https://www.google.com/search?q=%s+-site:reddit.com&gl=IN
```

### Basic HTML (no JS, for scraping)
```
https://www.google.com/search?q=%s&gbv=1&gl=IN
```

---

## 9. Files in This Repository

| File | Purpose |
|------|---------|
| `README.md` | This document |
| `template.txt` | Raw template string (copy-paste into browser settings) |
| `params.csv` | Machine-readable parameter list |
| `examples/` | Working URL examples |
| `CHANGELOG.md` | Parameter status changes over time |

---

## 10. Sources & Verification

- Chromium source: [`template_url.h`](https://chromium.googlesource.com/chromium/src/+/refs/heads/main/components/search_engines/template_url.h)
- Chromium commit for `gs_lcrp`: [March 2022](https://chromium.googlesource.com/chromium/src.git/+/e2ad407421b119f069f44fa4d8f9a01ee2d3ee73)
- `num` deprecation confirmed: Sep 2025 (multiple sources)
- `udm` values: observed in live SERPs, Oct–Nov 2026
- `gs_lcrp` protobuf schema: [`chrome_searchbox_stats.proto`](https://chromium.googlesource.com/chromium/src/+/refs/heads/main/third_party/omnibox_proto/chrome_searchbox_stats.proto)


Set Attributes for Privacy-focused Search using the following in Chromium-supported Devices

Settings > Manage Search-engines and Site Search in Browser Defaults > Click on the pencil icon > Add the following query as is

```
{google:baseURL}search?q=%s&{google:RLZ}{google:originalQueryForSuggestion}{google:assistedQueryStats}{google:searchFieldtrialParameter}{google:language}{google:prefetchSource}{google:searchClient}{google:sourceId}{google:contextualSearchVersion}{google:contextualSearchContextData}{google:searchVersion}{google:sessionToken}{google:currentPageUrl}{google:cursorPosition}{google:forceInstantResults}{google:pageClassification}{google:clientCacheTimeToLive}gl=IN&lr=lang_en&num=20&start=0&safe=active&tbs=&tbm=&udm=14&filter=1&nfpr=0&pws=0&cr=countryIN&uule=&ie={inputEncoding}&oe={outputEncoding}&gbv=&kgmid=&ibp=&as_q=&as_epq=&as_oq=&as_eq=&as_dt=&as_filetype=&as_ft=&as_lq=&as_sitesearch=&as_rq=&as_occt=&as_nlo=&as_nhi=&as_qdr=&as_rights=
```


Extended Directory Structure - Files available in the current Github.io repository

    
