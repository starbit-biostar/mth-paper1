# Maternal Timeline Harmonics — Analysis Repository

**Transgenerational reproductive timing analysis across 1,366 families and 17 cultural groups.**

Pre-registered study ([OSF: osf.io/7njxr](https://osf.io/7njxr)) showing 37% clustering in the [55, 65]-year transgenerational window vs 13% expected (χ² = 673.6, p < 0.001, Cohen's h = 0.56).

## Citation

> Angulo, U. & Sheretova, M. (2026). Cross-Cultural Invariance of Transgenerational Reproductive Timing: Analysis of 1,366 Families Across 17 Cultural Groups. *[Preprint on Research Square]*.

**ORCID:** [0009-0003-7204-7094](https://orcid.org/0009-0003-7204-7094)

## What This Study Found

Using maternal age at childbirth across three consecutive generations (grandmother → mother → subject), we find that the combined **transgenerational window** (TW = T₀ + T₁) clusters significantly within the [55, 65] year range across all 17 cultural groups examined.

| Key Result | Value |
|-----------|-------|
| Observed clustering | 37.0% (95% CI: 34.4–39.5%) |
| Expected (null) | 13.2% |
| Effect size | Cohen's h = 0.56 (medium-to-large) |
| Cultural groups | 17, all above null expectation |
| Sample | N = 1,366 verified families |
| Time span | 1500–2000 CE |

The clustering emerges from a remarkably conserved **population-level reproductive attractor** at ~27.5 years maternal age (T₀/T₁ ≈ 1.0 across all cultures), rather than from within-family intergenerational coupling (permutation p = 0.77).

## Repository Structure

```
├── data/
│   ├── mth_dataset_anonymized.csv    # Anonymized dataset (N=1,366)
│   └── DATA_DICTIONARY.md            # Variable definitions
├── analysis/
│   ├── 01_clustering_analysis.py     # Primary clustering + permutation tests
│   ├── 02_cross_cultural.py          # Cross-cultural replication
│   ├── 03_era_analysis.py            # Historical era effects
│   ├── 04_ml_ablation.py             # Machine learning feature importance
│   └── 05_figures.py                 # Figure generation
├── figures/                          # Generated figures (PNG + PDF)
├── paper/
│   └── manuscript.md                 # Current manuscript draft
└── LICENSE
```

## Quick Start

```bash
pip install numpy scipy scikit-learn matplotlib pandas
python analysis/01_clustering_analysis.py
```

## Data Sources

- [WikiTree](https://www.wikitree.com) collaborative genealogical database
- [Wikidata](https://www.wikidata.org) SPARQL queries
- Curated GEDCOM archives (Royal92, Presidents2020)
- Russian-language genealogical databases (VGD.ru, Geni.com)

## Pre-Registration

This study was pre-registered on the Open Science Framework on February 19, 2026:
**[https://osf.io/7njxr](https://osf.io/7njxr)**

Hypotheses, variables, clustering window [55, 65], and analytical methods were specified prior to data analysis. The expansion from pilot N=85 to N=1,366 used identical methodology.

## License

Code: [MIT License](LICENSE)
Data: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

## Use of AI Tools

SPARQL query generation, Python scripting, and manuscript editing were assisted by large language models (Claude, Anthropic). All research questions, hypotheses, methodology, and scientific conclusions are exclusively the work of the human authors.
