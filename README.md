# DiscourseDB v2.0 — Latin American Presidential Discourses

**DiscourseDB** is a curated corpus of presidential discourses from Latin American heads of government, covering 19 countries from 2000 to 2025.

---

## Coverage

| | |
|---|---|
| **Countries** | 19 |
| **Leaders** | 105 heads of government |
| **Period** | 2000–2025 |
| **Discourses** | 48,256 |

Countries: Argentina, Bolivia, Brazil, Chile, Colombia, Costa Rica, Cuba, Dominican Republic, Ecuador, Guatemala, Honduras, Mexico, Nicaragua, Panama, Paraguay, Peru, El Salvador, Uruguay, Venezuela.

### Discourse types

| Type | Description |
|------|-------------|
| `SPEECH` | Official presidential speech |
| `PRESS_RELEASE` | Government press release |
| `INTERVIEW` | Media interview |
| `COMMUNIQUE` | Formal communique |
| `DECREE` | Presidential decree |
| `LETTER` | Official letter |

---

## Dataset

The full corpus is distributed as a Parquet file via GitHub Releases:

📥 **[Download DiscourseDB_v2.0.parquet (~224 MB)](https://github.com/andrepyles/DiscourseDB/releases/tag/v2.0)**

### Schema

| Column | Type | Description |
|--------|------|-------------|
| `id` | string | SHA-256 hash — unique discourse identifier |
| `iso3` | string | ISO 3166-1 alpha-3 country code |
| `leader_name` | string | Full name of the head of government |
| `discourse_year` | integer | Year of the discourse |
| `discourse_date` | date | Date of the discourse (when available) |
| `discourse_place` | string | Location (when available) |
| `dtype` | string | Discourse type (see above) |
| `language` | string | Language of the discourse |
| `source` | string | Source URL or archive reference |
| `word_count` | integer | Length in words |
| `text` | string | Full discourse text |
| `ingested_at` | timestamp | Ingestion timestamp |

### Loading

```python
import pandas as pd
df = pd.read_parquet("DiscourseDB_v2.0.parquet")
```

---

## Changelog

| Version | Discourses | Notes |
|---------|-----------|-------|
| v2.0 | 48,256 | Added Cuba; extended to 2025; new discourse types |
| v1.0 | 44,719 | Initial release; 18 countries; speeches only |

---

## Citation

If you use DiscourseDB in academic work, please cite:

> Siqueira, André Pyles (2026). *Populismo em números: construção de um índice para mensurar a retórica populista na América Latina no século XXI*. Master's thesis, Universidade Presbiteriana Mackenzie. Data (DiscourseDB v2.0) available at: https://github.com/andrepyles/DiscourseDB