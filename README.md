# Myanmar Administrative Divisions / မြန်မာ

Open dataset of Myanmar's complete administrative hierarchy — from states and regions down to wards and village tracts. This repository provides structured, bilingual (Myanmar + English) reference data for all four levels of Myanmar's administrative divisions, including geographic coordinates at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| State/Region | 15 |
| District | 77 |
| Township | 491 |
| Ward/Village Tract | 17,043 |
| Coordinates | ✅ Included (all levels) |
| Postal Codes | ✅ Included (ward/village tract level) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-05-12 |

## Browse by State/Region

| # | State/Region | Districts | Townships | Ward/Village Tracts | Link |
|---|----|----|----|----|------|
| 1 | ကချင်ပြည်နယ် (Kachin) | 4 | 33 | 780 | [Browse](divisions/kachin-MMR001/) |
| 2 | ကယားပြည်နယ် (Kayah) | 2 | 10 | 124 | [Browse](divisions/kayah-MMR002/) |
| 3 | ကရင်ပြည်နယ် (Kayin) | 4 | 18 | 463 | [Browse](divisions/kayin-MMR003/) |
| 4 | ချင်းပြည်နယ် (Chin) | 4 | 20 | 543 | [Browse](divisions/chin-MMR004/) |
| 5 | စစ်ကိုင်းတိုင်းဒေသကြီး (Sagaing) | 11 | 42 | 1,889 | [Browse](divisions/sagaing-MMR005/) |
| 6 | တနင်္သာရီတိုင်းဒေသကြီး (Tanintharyi) | 3 | 18 | 358 | [Browse](divisions/tanintharyi-MMR006/) |
| 7 | ပဲခူးတိုင်းဒေသကြီး (Bago) | 4 | 51 | 1,804 | [Browse](divisions/bago-MMR007/) |
| 8 | မကွေးတိုင်းဒေသကြီး (Magway) | 5 | 32 | 1,677 | [Browse](divisions/magway-MMR009/) |
| 9 | မန္တလေးတိုင်းဒေသကြီး (Mandalay) | 7 | 34 | 1,703 | [Browse](divisions/mandalay-MMR010/) |
| 10 | မွန်ပြည်နယ် (Mon) | 2 | 17 | 494 | [Browse](divisions/mon-MMR011/) |
| 11 | ရခိုင်ပြည်နယ် (Rakhine) | 5 | 28 | 1,245 | [Browse](divisions/rakhine-MMR012/) |
| 12 | ရန်ကုန်တိုင်းဒေသကြီး (Yangon) | 4 | 49 | 1,408 | [Browse](divisions/yangon-MMR013/) |
| 13 | ရှမ်းပြည်နယ် (Shan) | 14 | 86 | 2,077 | [Browse](divisions/shan-MMR014/) |
| 14 | ဧရာဝတီတိုင်းဒေသကြီး (Ayeyarwady) | 6 | 45 | 2,230 | [Browse](divisions/ayeyarwady-MMR017/) |
| 15 | နေပြည်တော် (Nay Pyi Taw) | 2 | 8 | 248 | [Browse](divisions/nay-pyi-taw-MMR018/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-region.json](data/all-region.json) | JSON | All 15 state/region records |
| [all-district.json](data/all-district.json) | JSON | All 77 district records |
| [all-township.json](data/all-township.json) | JSON | All 491 township records |
| [ward-by-region/](data/ward-by-region/) | JSON | 17,043 ward/village tracts split by state/region |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-3 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-region.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-region.json", "utf-8"));
console.log(`Total: ${data.length} state/regions`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=state/region, 2=district, 3=township, 4=ward/village tract |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{region-slug}/
divisions/{region-slug}/{district-slug}/
divisions/{region-slug}/{district-slug}/{township-slug}/
```

Ward/Village Tracts are listed inline in each township's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-state/region links
- [Per-state/region data](docs/llms-full/) — Full data by state/region

## Citation

```
Myanmar Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/myanmar-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [ListBase](https://www.listbase.org) — Structured reference data for every country
- [open-admin-data](https://github.com/open-admin-data) — Open administrative data for ASEAN countries
- [thailand-administrative-divisions](https://github.com/open-admin-data/thailand-administrative-divisions) — Thailand dataset
