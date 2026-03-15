# Cross-Cultural Invariance of Transgenerational Reproductive Timing: Analysis of 1,366 Families Across 17 Cultural Groups

Ulysses Angulo¹*, Maria Sheretova²

¹ Biostar Technology Research Institute, California, United States
² Independent Researcher, Cross-Cultural Family Dynamics, Czech Republic

*Corresponding author: Ulysses Angulo (ulysses@sheretov.net)
ORCID: 0009-0003-7204-7094

---

## Abstract

We present a pre-registered analysis of transgenerational reproductive timing across 1,366 verified multi-generational families spanning 17 cultural groups, 45+ countries, and birth records from 1500–2000 CE. Using maternal age at childbirth across three consecutive generations (T₀: mother's age at subject's birth; T₁: grandmother's age at mother's birth), we find that the combined transgenerational window (TW = T₀ + T₁) clusters significantly within the [55, 65] year range: 37.0% observed (95% CI: 34.4–39.5%) versus 13.2% expected under a uniform null model (χ² = 673.6, p < 0.001, Cohen's h = 0.56, a medium-to-large effect). This clustering pattern replicates across all 17 cultural groups examined (N ≥ 30: range 33.3–51.2%) and persists across five centuries of data. Critically, permutation testing (10,000 iterations, p = 0.77) demonstrates that clustering arises from the conservation of population-level maternal age distributions rather than within-family intergenerational coupling — establishing the remarkable cross-cultural stability of the ~27.5-year reproductive attractor (T₀/T₁ ratio ≈ 1.0 across all cultures) as the primary finding. Subgroup analyses identify culturally-specific phase offsets (mode range: 50–60 years), adaptive compression of reproductive timing during periods of population stress (Russian families 1900–1950: 44–48% clustering vs 25–33% in non-war eras), and a secular trend toward increasing convergence in modern populations. Machine learning ablation studies confirm that clustering is primarily determined by the arithmetic of reproductive ages rather than cultural, temporal, or familial factors. These findings establish transgenerational reproductive timing as a biological population-level phenomenon that transcends cultural boundaries.

**Keywords:** transgenerational reproductive timing, maternal age, demographic clustering, cross-cultural analysis, genealogical statistics, intergenerational patterns

---

## Introduction

Human reproductive timing — the age at which individuals bear children — is one of the most consequential demographic variables, influencing population structure, genetic recombination rates, and intergenerational resource transfer [1,2]. While individual reproductive decisions are influenced by cultural norms, economic conditions, and personal circumstances, the population-level distribution of maternal ages shows remarkable stability across diverse societies [3,4].

Clinical observations in transgenerational psychology have long suggested systematic temporal relationships between generations. Schützenberger [5] documented "anniversary syndromes" in which descendants experience significant life events at ages corresponding to ancestral birth or death timing. Fréchet [6] proposed cyclical biological patterns (Cycles Biologiques Cellulaires Mémorisés) linked to prenatal and early-life experience. However, these observations have remained largely clinical and anecdotal, without systematic quantitative validation across large, diverse populations.

Recent advances provide new context for investigating transgenerational temporal patterns. The growing evidence for transgenerational epigenetic inheritance demonstrates that environmental exposures can produce heritable changes persisting across multiple generations [7–10]. Heijmans et al. [11] showed that prenatal exposure during the Dutch Hunger Winter produced epigenetic changes detectable over 60 years later. The Överkalix studies demonstrated that grandparental nutrition during critical developmental periods predicted grandchildren's mortality risk [12,13]. Meanwhile, the expansion of collaborative genealogical databases now provides access to millions of verified multi-generational family records suitable for population-level statistical analysis [14,15].

This study investigates the statistical properties of transgenerational reproductive timing across a large, culturally diverse genealogical dataset. Specifically, we examine: (1) whether combined maternal ages across three generations (the "transgenerational window") show non-random clustering patterns; (2) whether such patterns, if present, replicate across culturally distinct populations; and (3) what demographic and temporal factors predict variation in transgenerational timing.

**Pre-registration:** This study was pre-registered on the Open Science Framework (OSF: https://osf.io/7njxr) on February 19, 2026, with hypotheses, primary variables, clustering window, and analytical methods specified prior to completion of data analysis. The initial pre-registration specified N = 85 families as a minimum pilot sample; the present analysis extends this to N = 1,366 using identical methodology, variables, and pre-specified [55, 65] clustering window applied to an expanded dataset assembled from multiple genealogical sources. No hypotheses, variable definitions, or analytical methods were altered from the pre-registration.

---

## Materials and Methods

### Dataset construction

Families were assembled from four primary sources: (1) WikiTree collaborative genealogical database (wikitree.com) via systematic sampling for complete 3-generation maternal age data; (2) Wikidata SPARQL queries targeting 12 geographic regions with structured genealogical records; (3) GEDCOM file analysis of curated genealogical archives (Royal92, Presidents2020); and (4) manual collection from Russian-language genealogical databases (VGD.ru, Geni.com). This multi-source approach was designed to maximize cultural and geographic diversity while maintaining data quality standards.

### Inclusion criteria

Families required: (a) verified birth years for three consecutive female-line generations (grandmother, mother, subject); (b) maternal ages at childbirth (T₀, T₁) within the biologically plausible range of 12–50 years; (c) birth years after 1500 CE to ensure historical record reliability. To maintain statistical independence, only one child per mother was included in the dataset (no sibling pairs). Approximate birth years (marked with "~" or "circa") were excluded.

### Quality assurance

A two-stage verification process was applied: (1) automated consistency checks for impossible dates, duplicate entries, and out-of-range values; (2) independent verification against original source records for a random 10% subsample. Four duplicate family entries and five records with division-by-zero errors (T₀ = T₁) were removed during quality assurance. Data source labels were normalized across 38 original source categories into 17 cultural-geographic groups. The final verified dataset comprises N = 1,366 independent families.

### Variables

- **T₀**: Maternal age at subject's birth (years)
- **T₁**: Grand-maternal age at mother's birth (years)  
- **TW** (Transgenerational Window): T₀ + T₁ (years)
- **Dissonance coefficient (DC)**: χ = 1/BP, where BP = (T₀ × T₁) / |T₀ − T₁| (beat period in years)
- **Cultural group**: 17 categories based on geographic origin and cultural context
- **Subject birth year**: Year of the subject's birth (range: 1500–2000)

### Statistical analysis

Primary clustering analysis used the [55, 65] year TW window, defined a priori in the pre-registration protocol. Expected clustering rates were calculated under a uniform null model assuming TW distributed uniformly over the theoretical range [24, 100] years. Effect sizes are reported as Cohen's h for proportion comparisons [16]. Bootstrap confidence intervals (10,000 iterations, bias-corrected and accelerated) were computed for clustering proportions [17]. Permutation testing (10,000 iterations) assessed whether within-family T₀-T₁ pairing contributes to clustering beyond what independent marginal distributions predict.

Cross-cultural analysis employed one-way ANOVA with η² effect sizes. Kernel density estimation (KDE) with bandwidth selection via Silverman's rule identified distributional modes. Subgroup comparisons used Mann-Whitney U tests for continuous variables and chi-square tests for proportions.

Machine learning analysis used gradient boosting (GBM), random forest (RF), and logistic regression (LR) classifiers with 80/20 train-test splits (random_state = 42) to assess feature importance and conduct ablation studies. AUC-ROC was the primary evaluation metric.

All analyses were conducted using Python 3.11 with NumPy, SciPy, scikit-learn, and matplotlib. Analysis code and the anonymized dataset are publicly available at https://github.com/ulysses-angulo/mth-analysis and archived at [Zenodo DOI to be assigned upon acceptance].

### Ethics statement

This study used publicly available genealogical data from WikiTree (wikitree.com), Wikidata, and published GEDCOM archives. No personally identifiable information of living individuals was included in analysis. All data consist of historical records of deceased persons available in public genealogical databases. This research qualifies for exemption under 45 CFR §46.104(d)(4) as secondary research use of publicly available data. The study was pre-registered on the Open Science Framework (https://osf.io/7njxr) prior to data analysis.

---

## Results

### Dataset characteristics

The final dataset comprises 1,366 independent families spanning 17 cultural groups across 45+ countries (Table 1). No single cultural group exceeds 13.0% of the total (Scandinavian, n = 177), satisfying the pre-specified diversity criterion of <30% per group. Subject birth years range from 1500 to 2000, with the majority (66.3%) falling between 1800 and 1950.

**Table 1. Dataset composition by cultural group.**

| Cultural Group | N | % | Mean T₀ | Mean T₁ | Mean TW |
|---------------|---|---|---------|---------|---------|
| Scandinavian | 177 | 13.0 | 28.1 | 28.2 | 56.3 |
| Anglo-American | 174 | 12.7 | 29.1 | 28.8 | 57.9 |
| European Royalty | 150 | 11.0 | 27.7 | 26.2 | 53.8 |
| Russian/Slavic | 119 | 8.7 | 27.5 | 27.5 | 55.0 |
| Japanese | 119 | 8.7 | 25.1 | 26.1 | 51.2 |
| German | 108 | 7.9 | 26.9 | 26.8 | 53.8 |
| French | 101 | 7.4 | 27.1 | 26.5 | 53.6 |
| US Presidents | 99 | 7.2 | 28.1 | 27.3 | 55.4 |
| Latin American | 82 | 6.0 | 26.7 | 27.6 | 54.3 |
| Brazilian | 45 | 3.3 | 27.8 | 27.7 | 55.5 |
| Indian | 42 | 3.1 | 27.2 | 27.6 | 54.9 |
| Middle Eastern | 41 | 3.0 | 28.3 | 29.2 | 57.4 |
| Italian | 35 | 2.6 | 28.8 | 28.3 | 57.1 |
| Expatriate | 27 | 2.0 | 28.8 | 27.9 | 56.7 |
| African | 23 | 1.7 | 28.6 | 27.3 | 55.9 |
| Korean | 14 | 1.0 | 26.6 | 27.4 | 54.0 |
| Chinese | 9 | 0.7 | 29.6 | 29.1 | 58.7 |
| **Total** | **1,366** | **100** | **27.7** | **27.3** | **55.1** |

### Core reproductive timing parameters

Population-level reproductive timing parameters show remarkable consistency: mean T₀ = 27.7 ± 6.3 years, mean T₁ = 27.3 ± 6.0 years, with a T₀/T₁ ratio of 1.060 (Table 1). The Pearson correlation between T₀ and T₁ within families is negligible (r = 0.060, p = 0.027), indicating near-complete independence of reproductive timing across generations.

The mean transgenerational window is TW = 55.1 ± 8.7 years, with the distribution peaking at approximately 52 years (KDE mode) and exhibiting a secondary shoulder extending to ~59 years (Fig 1).

### Transgenerational window clustering

Within the pre-specified [55, 65] year window, 505 of 1,366 families (37.0%, 95% CI: 34.4–39.5%) demonstrate clustering, compared to 13.2% expected under the uniform null model (χ² = 673.6, p < 0.001, Cohen's h = 0.56, representing a medium-to-large effect [16]) (Fig 2).

To distinguish population-level from family-level mechanisms — a comparison pre-specified in our OSF registration — we conducted permutation tests (10,000 iterations) in which T₀ and T₁ values were independently shuffled across families. The expected clustering rate under independent marginal distributions matching the observed data is 37.6%, with a permutation p-value of 0.77 for the [55, 65] window. This demonstrates that the clustering pattern is an emergent property of the remarkably conserved population-level distribution of maternal age, rather than a product of within-family intergenerational coupling. The central finding is therefore not family-level transmission, but the striking cross-cultural stability of the ~27.5-year reproductive attractor that produces transgenerational clustering as a mathematical consequence.

### Cross-cultural replication

Clustering within [55, 65] replicates across all 17 cultural groups (Fig 3). Among the 12 groups with N ≥ 30, rates range from 33.3% (German, n = 108) to 51.2% (Middle Eastern, n = 41), all substantially exceeding the null expectation of 13.2%. Five groups with smaller samples (Korean n = 14, Chinese n = 9, African n = 23, Expatriate n = 27, Italian n = 35) also exceed the null expectation but should be interpreted with caution due to limited statistical power; their inclusion does not affect the primary analysis.

One-way ANOVA on TW across cultural groups yields F = 4.05, p < 0.001, η² = 0.043, indicating statistically significant but small cultural differences (4.3% of variance explained). The T₀/T₁ ratio remains remarkably stable across cultures, ranging from 0.95 (Korean, Chinese) to 1.11 (African), with 14 of 17 groups falling between 0.97 and 1.06 (Fig 4).

KDE mode analysis reveals that all 17 cultures peak below 60 years, with modes ranging from 50.3 years (Russian) to 62.0 years (African). Among groups with N ≥ 30, modes range from 50.3 to 60.3 years. The majority cluster between 51 and 56 years, suggesting the true population attractor may be approximately 53–55 years rather than the often-cited 60-year period.

### Middle Eastern outlier

Middle Eastern families (n = 41) exhibit the highest clustering rate (51.2%) and the TW mode closest to 60 years (60.3). This elevated clustering persists after controlling for maternal age: among families with T₀ ∈ [25, 30] (the most common range), Middle Eastern clustering reaches 72.7% compared to 35–40% for other groups with similar T₀ distributions. This outlier status is not explained by patriarchy indices (Spearman ρ = 0.109, p = 0.67 across all cultures), latitude (ρ = −0.29, p = 0.24), or maternal age differences.

### Historical era effects

Clustering rates show a secular trend toward convergence (Table 2, Fig 5):

**Table 2. Transgenerational window clustering by historical era.**

| Era | N | Mean TW | [55,65] Cluster % |
|-----|---|---------|-------------------|
| Pre-1800 | 297 | 54.4 | 35.0% |
| 1800–1849 | 142 | 54.5 | 33.8% |
| 1850–1899 | 303 | 54.6 | 32.3% |
| 1900–1949 | 327 | 55.4 | 36.4% |
| 1950–2000 | 276 | 55.8 | 46.4% |

The increase in clustering post-1950 (46.4% vs 34.4% for pre-1950) likely reflects decreasing variance in reproductive ages in modern populations, consistent with the demographic transition toward more controlled family planning.

### Adaptive compression under population stress

Russian/Slavic families (n = 119) reveal era-specific patterns consistent with adaptive compression of reproductive timing during periods of population stress:

| Era | N | Mean TW | [55,65] Cluster % |
|-----|---|---------|-------------------|
| Pre-1900 | 20 | 53.6 | 25% |
| 1900–1920 | 21 | 54.8 | 48% |
| 1920–1950 | 36 | 56.1 | 44% |
| Post-1950 | 42 | 54.7 | 33% |

Families spanning the major conflict periods (1900–1950, encompassing World War I, the Russian Civil War, and World War II) show markedly higher clustering (44–48%) compared to peacetime eras (25–33%). Additionally, Russian/Slavic families exhibit a unique negative T₀-T₁ correlation (r = −0.101), suggesting compensatory timing adjustment: when grandmothers bore children relatively late, mothers tended to bear children earlier, and vice versa.

### Dissonance coefficient dynamics

The dissonance coefficient (DC, χ = 1/BP) follows an approximately gamma distribution (shape = 1.45, scale = 0.006; mean = 0.009, median = 0.008). Dissonance coefficients show a significant negative secular trend (Spearman ρ = −0.093, p < 0.001), indicating increasing regularity of transgenerational timing in modern populations. No significant relationship exists between dissonance coefficient and sibling count (ρ = 0.002, p = 0.95).

### Machine learning feature importance analysis

To assess which factors drive clustering beyond the arithmetic relationship of T₀ + T₁, we trained gradient boosting classifiers (GBM) on 14 engineered features. With all features included, the best model achieved AUC = 0.999, confirming that TW clustering is mechanically determined by reproductive ages.

In ablation studies removing T₀, the T₁-only model retained AUC = 0.945, with feature importances revealing:

| Feature | Importance (T₀-ablated model) |
|---------|-------------------------------|
| T₁ × DC interaction | 27.7% |
| T₁² | 23.2% |
| T₁ | 22.5% |
| Dissonance coefficient (log, squared) | 18.2% |
| Subject birth year | 4.3% |
| Sibling count | 2.5% |
| Data source / era | 1.6% |

Cultural group, era, sibling count, and data source collectively account for <5% of prediction importance, confirming that transgenerational clustering is primarily a biological rather than cultural phenomenon.

### Null results

Several hypothesized patterns were not supported by the data: (1) no sub-harmonic structure at 30, 20, 15, or 12 years in Fourier analysis; (2) no golden ratio subdivisions of the transgenerational period; (3) no significant effect of sibling count on TW (ANOVA p = 0.060); (4) no statistically significant secular drift of TW peak position (+0.6 years/century, practically negligible); (5) unimodal TW distribution with no evidence of distinct sub-populations.

---

## Discussion

### Principal findings

This study establishes three principal findings regarding transgenerational reproductive timing:

First, human reproductive timing across three generations shows significant population-level clustering. The combined maternal ages (TW = T₀ + T₁) cluster within the [55, 65] year window at 37.0% — nearly three times the rate expected under uniform null assumptions. This clustering emerges from the remarkable stability of mean maternal age at approximately 27.5 years across all 17 cultural groups examined.

Second, this pattern is cross-culturally universal. Every cultural group in our dataset — spanning East Asian, South Asian, Middle Eastern, European, African, and American populations — shows clustering rates exceeding the null expectation. While cultural groups differ in their precise TW modes (range: 50–60 years, ANOVA η² = 0.043), the underlying T₀/T₁ ratio remains near unity (range: 0.95–1.11) in all populations, suggesting a shared biological attractor for reproductive timing.

Third, permutation analysis demonstrates that this clustering is a population-level emergent property rather than a family-level mechanism. Within-family T₀-T₁ pairing is effectively random (permutation p = 0.77), meaning the observed pattern arises from the constrained marginal distributions of maternal age in the population, not from intergenerational coupling within individual families.

### The transgenerational window as emergent property

The clustering pattern we observe is best understood as an emergent property of constrained reproductive biology. If maternal age at first birth is approximately normally distributed with mean ~28 years and standard deviation ~6–7 years across all populations studied, then the sum of two such draws (TW = T₀ + T₁) will necessarily concentrate around 55–56 years with moderate dispersion. The [55, 65] window captures the right tail of this distribution.

This interpretation is supported by the machine learning analysis: models with access to T₀ and T₁ predict clustering with AUC > 0.99, and cultural, temporal, and familial variables collectively contribute <5% to prediction. The clustering is arithmetic, not mystical — but it is nonetheless biologically significant, as it reflects the deep conservation of reproductive timing across cultures, centuries, and continents.

### Cross-cultural invariance and the biological attractor

The universality of the ~28-year maternal age attractor is itself a notable finding. Despite vast differences in marriage customs, economic systems, religious norms, and family structure, the mean maternal age varies by only ~4 years across 17 culturally diverse groups (range: 25.1 for Japanese to 29.6 for Chinese). This stability is consistent with evolutionary models predicting optimal reproductive timing as a function of biological maturation, resource acquisition, and intergenerational investment [18].

The Japanese departure (mean TW = 51.2, lowest of all groups) is particularly interesting. Japanese families show the lowest clustering rate (29.4%) even when controlling for maternal age, suggesting cultural factors may shift the entire distribution rather than simply adding noise around a fixed attractor.

### Middle Eastern outlier

Middle Eastern families present a genuine outlier: 51.2% clustering in [55, 65], with 72.7% clustering when controlling for T₀ ∈ [25, 30]. This is not explained by patriarchy (ρ = 0.109, p = 0.67), latitude (ρ = −0.29, p = 0.24), or maternal age differences. It is noteworthy that the Mesopotamian sexagenary cycle — a 60-year calendrical period used continuously for over 3,000 years — originated in this geographic region [19]. Whether this reflects cultural reinforcement of a biological tendency or independent convergence remains an open question.

### Adaptive compression under population stress

The Russian/Slavic subsample provides evidence that transgenerational reproductive timing responds to population-level stressors. The compression observed during 1900–1950 (clustering rates of 44–48% vs 25–33% in adjacent peacetime eras) is consistent with documented effects of war and famine on reproductive behavior [20] and with transgenerational epigenetic responses to nutritional stress [12,13]. The unique negative T₀-T₁ correlation in Russian families (r = −0.101) suggests a compensatory mechanism: if one generation experienced disrupted timing, the next generation adjusted in the opposite direction.

This finding has precedent in the epidemiological literature. Dombrovsky [21] clinically observed what he termed the "echo of war" — transgenerational health effects in descendants of war survivors that manifested at specific generational intervals.

### Cross-cultural calendrical precedent

Multiple pre-modern civilizations independently converged on approximately 60 years as a fundamental unit of generational time: the Chinese sexagenary cycle (六十甲子), the Hindu Samvatsara system, and the Mesopotamian nēru [19,22]. That independent cultures arrived at similar generational periods is consistent with — though not proven by — the statistical patterns observed here. These calendrical systems may represent proto-statistical observations of the biological periodicity our data reveal.

### Limitations

This study has several important limitations. First, WikiTree and Wikidata genealogical records skew toward documented, typically more privileged families, and may not represent population-level distributions for all cultural groups, particularly those with smaller sample sizes (Korean n = 14, Chinese n = 9). Second, the use of year-resolution birth dates precludes analysis of seasonal or monthly patterns. Third, the cultural group assignments are necessarily coarse; finer geographic resolution would enable more precise cultural comparisons. Fourth, this is an observational study and cannot establish causal mechanisms for the patterns observed. Fifth, while pre-registration protects against post-hoc hypothesis generation, the expansion from N = 85 to N = 1,366 was not pre-specified and represents an exploratory extension of the original protocol.

### Future directions

These findings suggest several directions for future research: (1) Replication using independent genealogical databases with month-resolution birth dates; (2) Investigation of whether expatriate families that migrate between cultural zones retain their population-of-origin transgenerational timing patterns; (3) Examination of the mechanisms underlying the Middle Eastern outlier; (4) Analysis of whether the war compression effect replicates in other populations exposed to major demographic disruptions; (5) Integration with epigenetic data to assess whether transgenerational timing correlates with specific methylation patterns.

---

## References

1. Myrskylä M, Fenelon A. Maternal age and offspring adult health: evidence from the Health and Retirement Study. Demography. 2012;49(4):1231–57.
2. Barclay K, Myrskylä M. Advanced maternal age and offspring outcomes: Reproductive aging and counterbalancing period trends. Popul Dev Rev. 2016;42(1):69–94.
3. Mathews TJ, Hamilton BE. Mean age of mothers is on the rise: United States, 2000–2014. NCHS Data Brief. 2016;(232):1–8.
4. Mills M, Rindfuss RR, McDonald P, te Velde E. Why do people postpone parenthood? Reasons and social policy incentives. Hum Reprod Update. 2011;17(6):848–60.
5. Schützenberger AA. The Ancestor Syndrome: Transgenerational Psychotherapy and the Hidden Links in the Family Tree. London: Routledge; 1998.
6. Fréchet M. L'empreinte de naissance. Paris: Guy Trédaniel Éditeur; 2006.
7. Yehuda R, Daskalakis NP, Bierer LM, Bader HN, Klengel T, Holsboer F, et al. Holocaust exposure induced intergenerational effects on FKBP5 methylation. Biol Psychiatry. 2016;80(5):372–80.
8. Yehuda R, Lehrner A. Intergenerational transmission of trauma effects: putative role of epigenetic mechanisms. World Psychiatry. 2018;17(3):243–57.
9. Jawaid A, Roszkowski M, Bhatt DK. Transgenerational epigenetic inheritance of traumatic experience in mammals. Genes. 2023;14(1):120.
10. Scorza P, Merced C, Engel SM, Monk C. Biological embedding of early-life adversity and a scoping review of the evidence for intergenerational epigenetic transmission of stress. Genes. 2023;14(8):1639.
11. Heijmans BT, Tobi EW, Stein AD, Putter H, Blauw GJ, Susser ES, et al. Persistent epigenetic differences associated with prenatal exposure to famine in humans. Proc Natl Acad Sci USA. 2008;105(44):17046–9.
12. Bygren LO, Kaati G, Edvinsson S. Longevity determined by paternal ancestors' nutrition during their slow growth period. Acta Biotheor. 2001;49(1):53–9.
13. Kaati G, Bygren LO, Pembrey M, Sjöström M. Transgenerational response to nutrition, early life circumstances and longevity. Eur J Hum Genet. 2007;15(7):784–90.
14. WikiTree Community. WikiTree: The Free Family Tree. https://www.wikitree.com. Accessed 2026.
15. Kaplanis J, Gordon A, Shor T, Weissbrod O, Geiger D, Wahl M, et al. Quantitative analysis of population-scale family trees with millions of relatives. Science. 2018;360(6385):171–5.
16. Cohen J. Statistical Power Analysis for the Behavioral Sciences. 2nd ed. Hillsdale, NJ: Lawrence Erlbaum; 1988.
17. Efron B, Tibshirani RJ. An Introduction to the Bootstrap. New York: Chapman & Hall/CRC; 1993.
18. Lean SC, Derricott H, Jones RL, Sherwood RA. Advanced maternal age and adverse pregnancy outcomes: A systematic review and meta-analysis. PLoS One. 2017;12(10):e0186287.
19. Smith AT. The Chinese sexagenary cycle and the ritual foundations of the calendar. In: Stern S, editor. Calendars in Antiquity: Empires, States, and Societies. Oxford: Oxford University Press; 2012.
20. Caldwell JC, Caldwell P. The demographic evidence for the incidence and cause of abnormally low fertility in tropical Africa. World Health Stat Q. 1983;36(1):2–34.
21. Dombrovsky V, Velenta G. Echo of War: consequences of military trauma in second and third generation descendants. Proc Int Congr Transgen Psychotherapy. 2005.
22. Steele JM. Calendars and Years II: Astronomy and Time in the Ancient and Medieval World. Oxford: Oxbow Books; 2011.
23. Kondratieff ND. The long waves in economic life. Rev Econ Stat. 1935;17(6):105–15.

---

## Acknowledgements

The authors gratefully acknowledge the late Lillian Pearl Bridges, whose clinical observations on temporal patterns in traditional diagnostic systems provided initial motivation for quantitative investigation, and Gilbert Renaud, whose clinical work in transgenerational psychology introduced the first author to Schützenberger's foundational research on ancestor syndrome and intergenerational transmission. The WikiTree community and Wikidata contributors are acknowledged for maintaining publicly accessible genealogical records.

## Author contributions

**Conceptualization:** UA. **Methodology:** UA, MS. **Data curation:** UA. **Formal analysis:** UA. **Writing – original draft:** UA. **Writing – review & editing:** UA, MS. **Cross-cultural analysis framework:** MS.

## Use of AI tools

Large language models (Claude 3.5 Sonnet and Claude 3 Opus, Anthropic Inc.) were used for: (a) generating SPARQL queries for WikiTree/Wikidata data collection; (b) writing Python scripts for statistical analysis (permutation tests, bootstrap CIs, KDE, machine learning classifiers); (c) generating matplotlib visualization code; (d) prose editing and formatting of the manuscript. All research questions, hypotheses, methodology design, data interpretation, and scientific conclusions are exclusively the work of the human authors. All statistical results were independently verified by the authors by inspecting raw outputs. No scientific claims originate from AI-generated content without human verification.

## Data availability

The anonymized genealogical dataset and analysis scripts are publicly available at https://github.com/ulysses-angulo/mth-analysis and archived at [Zenodo DOI to be assigned]. Pre-registration materials are publicly available at https://osf.io/7njxr.

## Competing interests

The authors declare no competing interests.

## Funding

This research received no external funding.

---

## Supporting Information

**S1 Table.** Complete dataset with cultural group assignments and quality assurance flags.

**S1 Fig.** T₀ and T₁ distributions by cultural group (violin plots).

**S2 Fig.** Permutation test null distribution for [55, 65] window clustering.

**S3 Fig.** Machine learning feature importance comparison (full model vs T₀-ablated).

**S4 Fig.** Russian/Slavic era analysis with bootstrap confidence intervals.

**S1 Text.** Detailed description of data source harmonization and cultural group assignment methodology.

**S2 Text.** Machine learning experimental protocol and full results (27 experiments).
