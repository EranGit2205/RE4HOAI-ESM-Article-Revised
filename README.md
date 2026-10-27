# RE4HOAI Online Resources 1–9

Supplementary materials for **How Teams Decide on Human Oversight in AI-Powered Systems: A Mixed-Methods Study**

**Authors:** Eran Sadovski, Itzhak Aviv, and Irit Hadar  
**Journal:** Empirical Software Engineering  
**Contact:** Eran Sadovski — sdv.eran@gmail.com

These resources document the conceptual foundations, empirical evidence, framework refinement, illustrative trade-off analysis, and survey results supporting RE4HOAI. Resource numbers correspond to the manuscript. File links below assume this README is placed beside the resource files.

## Resource inventory

| Online Resource | File | Contents and purpose |
|---|---|---|
| **1 — Requirement interrelationships** | [ESM_1_revised.pdf](ESM_1_revised.pdf) | Explains the requirement relationships underlying the human-oversight conceptual model, including interactions with trustworthiness, ethics, performance, safety, accountability, and explainability. Supports the conceptual grounding of RE4HOAI. |
| **2 — Literature-based case illustrations** | [ESM_2_Revised.pdf](ESM_2_Revised.pdf) | Eight brief, source-based illustrations covering autonomous driving, banking fraud detection, medical diagnostics, hiring, mortgage lending, predictive policing, pandemic triage, and aerospace predictive maintenance. Illustrates oversight tensions and competing requirements, with supporting references. These are contextual illustrations, not applications or validations of RE4HOAI. |
| **3 — Stakeholder interview demographics** | [ESM_3_Revised.pdf](ESM_3_Revised.pdf) | Participant characteristics for the 35 stakeholder interviews previously collected in the OG-RE4AI study, including professional experience, domains, and the two original interview waves. Documents the composition of the interview sample used for the focused oversight analysis. |
| **4 — OG-RE4AI research interview protocol** | [ESM4_Revised.pdf](ESM4_Revised.pdf) | The research interview questions used to explore AI-system requirements. Questions contributing oversight-relevant material are marked in bold italics, but also address broader requirement concerns.  |
| **5 — Stakeholder thematic-analysis record** | [ESM_5_revised.xlsx](ESM_5_revised.xlsx) | The `Readme` and `quotations` sheets document interview excerpts, quotation references, anonymized interview identifiers, codes, and thematic assignments before and after peer debriefing. Supports traceability of the five stakeholder themes and distinguishes coding rows, excerpts, and theme assignments. |
| **6 — Worked MCDA illustration** | [ESM_6_Revised.pdf](ESM_6_Revised.pdf) | A retrospective illustration of Multi-Criteria Decision Analysis using the Uber ATG accident context. Includes author-assigned scores and weights, alternative oversight configurations, weight-sensitivity scenarios, limitations, and references. 
| **7 — Expert evaluation and thematic analysis** | [ESM_7_Revised.pdf](ESM_7_Revised.pdf) | Documents evaluation by five experts, the interview questions, themes organized by framework phase, coverage in Version 1, expert identifiers, and supporting-passage counts. An appendix provides 96 attributed passages, linked to the themes they support. The mappings include explicit evaluations and contextually interpreted observations. These passages are selected extracts, not complete interview transcripts. |
| **8 — Survey data and statistical results** | [ESM_8_Revised.xlsx](ESM_8_Revised.xlsx) | Respondent-level data for 58 practitioners and analyses of 11 survey statements. Includes group-comparison sheets for perceived risk, professional role, and familiarity; continuous-age Spearman correlations; study-wide multiplicity adjustments; effect-size estimates; and exploratory pairwise comparisons with within-family Bonferroni adjustment. |
| **9 — R reproducibility package** | [Online_Resource_9.zip](Online_Resource_9.zip) | ZIP archive containing exactly two files: `analyse_survey_ESM8.R` and `survey_input.csv`. The script independently reproduces the survey calculations in base R. Execution instructions are provided below. |

## Survey analysis and interpretation

The authors performed the reported statistical analyses using **IBM SPSS Statistics version 31.0**, with assistance from a university statistician. The R script was subsequently developed solely to support reproducibility, executed independently, and checked against the reported results. The pairwise table presents R-calculated mean ranks and signed statistics with an explicit group-A-minus-group-B convention.

The analysis includes:

- **33 Kruskal–Wallis tests:** 11 statements compared across perceived risk, professional role, and AI familiarity.
- **11 two-sided Spearman correlations:** actual age in years associated with each statement, without age bands or age-group exclusions.
- **Holm correction across all 44 primary tests.** The group-comparison sheets in Resource 8 also report study-wide Bonferroni-adjusted values.
- **Exploratory pairwise comparisons** following Kruskal–Wallis tests with unadjusted p < .05. Bonferroni correction is applied separately within each pairwise family: three comparisons for risk and six for role or familiarity.

Missing responses are excluded separately for each analysis, without imputation. Statements 1, 5, and 10 each have 57 valid responses; the other statements have 58. Descriptive statistics include both population and sample standard deviations; manuscript Table 6 uses population SD.

For Kruskal–Wallis comparisons, the effect-size estimator is:

```text
eta_squared_H = (H - k + 1) / (n - k)
```

Here, `k` is the number of observed groups and `n` is the valid sample for that comparison. Negative estimates are retained.

For the supplied data, five Kruskal–Wallis comparisons have unadjusted p < .05, producing 27 exploratory pairwise comparisons. Four pairwise contrasts pass within-family Bonferroni correction:

| Statement | Higher agreement | Bonferroni-adjusted p, rounded |
|---|---|---:|
| 2 | Operators > Management | .005 |
| 3 | Development team > Management | .024 |
| 10 | Medium risk > High risk | .022 |
| 10 | Low risk > High risk | .003 |

**None of the 44 primary tests survives study-wide Holm correction.** The four pairwise findings remain exploratory and do not establish study-wide significance. Lack of adjusted significance does not establish equivalence between groups.

## Run Online Resource 9

### Requirements and extraction

Install R, then extract `Online_Resource_9.zip` into a writable folder. No additional R packages are required. The extracted folder contains:

```text
analyse_survey_ESM8.R
survey_input.csv
```

### Terminal

Open a terminal in the extracted folder and run:

```sh
Rscript analyse_survey_ESM8.R
```

To specify input and output paths explicitly:

```sh
Rscript analyse_survey_ESM8.R "C:/path/to/survey_input.csv" "C:/path/to/survey_results"
```

Quote paths containing spaces. Replace the example paths with your own locations.

### RStudio

Set the working directory to the extracted folder, then source the script:

```r
setwd("C:/path/to/extracted_folder")
source("analyse_survey_ESM8.R")
```

The script executes immediately; there is no separate `analyse_survey()` function to call. With this method, the input CSV must be in the working directory.

### Input requirements

The CSV contains one row per respondent. Required column names are:

```text
age,role,risk,familiarity,S1,S2,S3,S4,S5,S6,S7,S8,S9,S10,S11
```

An additional `respondent_id` column identifies records but is not used in the calculations.

| Field | Accepted values |
|---|---|
| `age` | Numeric age in years |
| `role` | `Academia`, `Operator`, `Management`, `Development team` |
| `risk` | `High`, `Medium`, `Low` |
| `familiarity` | `Basic`, `Moderate`, `High`, `Expert` |
| `S1`–`S11` | Numeric responses from 1 to 5 |

Blank fields and `NA` represent missing values. Familiarity labels are trimmed for surrounding whitespace; role and risk labels must match exactly. The supplied CSV already uses the harmonized label `Basic`.

The group order matches the revised Resource 8 pairwise presentation: High–Medium–Low for risk; Academia–Operator–Management–Development team for role; Basic–Moderate–High–Expert for familiarity. Numeric codes are display identifiers in Resource 8; the R script analyzes text labels.

### Generated outputs

By default, the script creates `survey_results` beside the input CSV and writes:

| Generated file | Contents |
|---|---|
| `descriptive_statistics.csv` | Statement-level valid n, mean, population SD, sample SD, minimum, and maximum. |
| `primary_tests_44.csv` | All 44 primary tests, including valid n, H or Spearman rho, degrees of freedom where applicable, unadjusted p-values, Kruskal–Wallis effect sizes, and study-wide Holm-adjusted p-values. |
| `spss_pairwise_bonferroni_all.csv` | All 27 exploratory pairwise comparisons for the supplied data, including group sizes, mean ranks, signed differences, standard errors, z statistics, and raw and within-family Bonferroni-adjusted p-values. |
| `spss_pairwise_bonferroni_nominal.csv` | Pairwise contrasts with within-family Bonferroni-adjusted p < .05. |
| `analysis_checks.txt` | R version, input path, participant count, test and contrast counts, missing responses, and interpretation rules. |


