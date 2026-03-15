# Data Dictionary

## mth_dataset_anonymized.csv

| Variable | Type | Description |
|----------|------|-------------|
| family_id | string | Unique family identifier |
| T0 | float | Mother's age at subject's birth (years) |
| T1 | float | Grandmother's age at mother's birth (years) |
| TW | float | Transgenerational window: T0 + T1 (years) |
| BP | float | Beat period: (T0 × T1) / \|T0 − T1\| (years) |
| dissonance_coefficient | float | DC = 1/BP (inverse beat period) |
| sibling_count | int | Number of siblings of the subject |
| subject_birth_decade | int | Decade of subject's birth (e.g., 1890) |
| data_source | string | Original data source (WikiTree, Wikidata, GEDCOM, etc.) |
| cultural_group | string | Cultural-geographic group assignment |

## Key Definitions

- **Transgenerational Window (TW):** The sum of maternal ages across two consecutive generations. Represents the elapsed time between grandmother giving birth to mother and mother giving birth to subject.
- **Clustering Window:** [55, 65] years — pre-specified in OSF registration (osf.io/7njxr)
- **Null Expectation:** 13.2% under uniform distribution across theoretical TW range [24, 100]
- **Dissonance Coefficient:** Measures deviation from perfect intergenerational timing symmetry. Lower values indicate more synchronized timing across generations.

## Data Sources

1. **WikiTree** (wikitree.com) — collaborative genealogical database, systematic sampling
2. **Wikidata** — SPARQL queries targeting 12 geographic regions
3. **GEDCOM archives** — Royal92, Presidents2020 curated collections
4. **Russian databases** — VGD.ru, Geni.com, manual collection

## Privacy

All personally identifiable information (names, exact birth dates, locations) has been removed. Only statistical variables necessary for reproducing the analysis are included. All original data derive from public genealogical records of historical (deceased) persons.
