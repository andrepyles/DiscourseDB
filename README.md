# DiscourseDB v2.2

## Latin American presidential discourse corpus

DiscourseDB is an open, structured corpus of presidential and executive political discourse from Latin America. The `main` branch contains the country-level text files used to build the POPIN index, together with the metadata catalog available for the historical corpus.

- Repository: [github.com/andrepyles/DiscourseDB](https://github.com/andrepyles/DiscourseDB)
- Release: [DiscourseDB v2.2.0](https://github.com/andrepyles/DiscourseDB/releases/tag/v2.2.0)
- Related project: [POPIN](https://github.com/andrepyles/POPIN)

## Coverage

The repository contains 19 country folders and 48,878 UTF-8 plain-text files:

| ISO3 | Country |
|---|---|
| ARG | Argentina |
| BOL | Bolivia |
| BRA | Brazil |
| CHL | Chile |
| COL | Colombia |
| CRI | Costa Rica |
| CUB | Cuba |
| DOM | Dominican Republic |
| ECU | Ecuador |
| GTM | Guatemala |
| HND | Honduras |
| MEX | Mexico |
| NIC | Nicaragua |
| PAN | Panama |
| PER | Peru |
| PRY | Paraguay |
| SLV | El Salvador |
| URY | Uruguay |
| VEN | Venezuela |

The current `main` tree is the complete raw-text expansion available in the project source. It includes the original historical corpus, the Cuban text collection, and subsequent country-level additions through the latest source snapshot.

`CATALOG.xlsx` remains the historical metadata workbook with 44,719 records from the original 18-country corpus. It does not yet enumerate every file in the expanded 48,878-file tree. The additional raw files are therefore intentionally published as text files first; their leader, date, language, document type, and source metadata should be checked before a future catalog revision.

## File convention

Country folders contain UTF-8 plain-text files named as:

```text
ISO3_YEAR_SEQUENCE.txt
```

For example, `BRA_2019_128.txt` identifies a Brazilian document from 2019. The filename is a stable corpus identifier and should be joined to the catalog through `FILENAME` when a catalog row is available.

## Catalog

`CATALOG.xlsx` is the metadata workbook for the original 18-country corpus. Its fields include:

| Field | Description |
|---|---|
| `COUNTRY_NAME` | country name |
| `ISO3` | ISO 3166-1 alpha-3 code |
| `DISCOURSE_YEAR` | year of the document |
| `LEADER_NAME` | leader associated with the document |
| `FILENAME` | corresponding text filename |
| `LANGUAGE` | original language |
| `DISCOURSE_PLACE` | location, when available |
| `DISCOURSE_DATE` | date, when available |
| `EXTRACTION_DATE` | extraction/access date |
| `SOURCE` | source URL or archive reference |

Because the expanded text tree is larger than the workbook, analyses requiring metadata should report whether they use cataloged records only or the full raw-text tree.

## Consolidated data

For analysis, the country files can be combined into a tabular or Parquet dataset. The consolidated DiscourseDB v2.0 file is distributed through the [GitHub Releases page](https://github.com/andrepyles/DiscourseDB). Raw text and derived tabular releases are kept conceptually separate so that users can reproduce or audit the ingestion step.

Example loading of a consolidated Parquet release:

```python
import pandas as pd

df = pd.read_parquet("DiscourseDB_v2.0.parquet")
print(df.shape)
print(df[["iso3", "discourse_year", "dtype"]].head())
```

## Relationship with POPIN

POPIN uses DiscourseDB as its discourse corpus. The POPIN pipeline classifies document type, excludes records marked `INVALID`, and scores eligible texts on six dimensions of populist rhetoric. DiscourseDB itself is source data: it does not contain a populism score.

## Version history

| Version | Contents |
|---|---|
| v2.2.0 | Full 19-country raw-text expansion: 48,878 files; catalog coverage limitation documented |
| v2.1.0 | 45,280 raw texts in `main`; Cuba added; catalog limitation documented |
| v2.0 | 19-country project metadata and consolidated release reference |
| v1.0 | Original 18-country corpus and catalog |

## Citation

Please cite the release used in your analysis and report whether you used the raw country files or a consolidated Parquet artifact:

> Siqueira, André Pyles. *DiscourseDB v2.2.0: Latin American Presidential Discourse Corpus*. 2026. https://github.com/andrepyles/DiscourseDB
