# DiscourseDB v2.1

## Latin American presidential discourse corpus

DiscourseDB is an open, structured corpus of presidential and executive political discourse from Latin America. The `main` branch contains the country-level text files used to build the POPIN index, together with the catalog for the original corpus.

- Repository: [github.com/andrepyles/DiscourseDB](https://github.com/andrepyles/DiscourseDB)
- Release: [DiscourseDB v2.1.0](https://github.com/andrepyles/DiscourseDB/releases/tag/v2.1.0)
- Related project: [POPIN](https://github.com/andrepyles/POPIN)

## Coverage

The repository contains 19 country folders, covering presidential discourse from 2000 to 2025:

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

The original catalog contains 44,719 records from 18 countries. This release adds 561 Cuban text files to the `CUB/` folder, for 45,280 raw text files present in the repository. Cuba is explicitly identified as a supplemental corpus because its files are not yet represented as rows in the original `CATALOG.xlsx` metadata workbook.

## File convention

Country folders contain UTF-8 plain-text files named as:

```text
ISO3_YEAR_SEQUENCE.txt
```

For example, `BRA_2019_128.txt` identifies a Brazilian document from 2019. The filename is a stable corpus identifier and should be joined to the catalog through `FILENAME`.

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

The Cuban files are distributed as raw text in this release. They should be added to a future catalog revision only after their leader, date, language, and source metadata have been checked.

## Consolidated data

For analysis, the country files can be combined into a tabular or Parquet dataset. The consolidated DiscourseDB v2.0 file is distributed through the [GitHub Releases page](https://github.com/andrepyles/DiscourseDB/releases). Raw text and derived tabular releases are kept conceptually separate so that users can reproduce or audit the ingestion step.

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
| v2.1.0 | Complete 19-country text tree in `main`; Cuba added; catalog limitation documented |
| v2.0 | 19-country project metadata and consolidated release reference |
| v1.0 | Original 18-country corpus and catalog |

## Citation

Please cite the release used in your analysis and report whether you used the raw country files or a consolidated Parquet artifact:

> Siqueira, André Pyles. *DiscourseDB v2.1.0: Latin American Presidential Discourse Corpus*. 2026. https://github.com/andrepyles/DiscourseDB
