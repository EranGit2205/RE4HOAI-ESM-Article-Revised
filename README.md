# RE4HOAI Supplementary Materials

This repository contains the revised supplementary resources for:

**How Teams Decide on Human Oversight in AI-Powered Systems: A Mixed-Methods Study**

**Authors:** Eran Sadovski, Itzhak Aviv, and Irit Hadar  
**Journal:** Empirical Software Engineering

RE4HOAI is a lifecycle-oriented requirements-engineering framework for defining, negotiating, documenting, and revisiting human-oversight requirements in AI-powered systems. These resources document its conceptual and empirical foundations, expert-informed evolution, worked MCDA illustration, and survey analysis.

## Revised supplementary resources

The Online Resource numbers below correspond to the references in the manuscript.

| Online Resource | Revised file | Contents |
| --- | --- | --- |
| 1 | [ESM_1_revised.pdf](ESM_1_revised.pdf) | Description of the requirement relationships underlying the human-oversight conceptual model, including interactions with trustworthiness, ethics, performance, safety, accountability, and explainability. |
| 2 | [ESM_2_Revised.pdf](ESM_2_Revised.pdf) | Eight brief, source-based case illustrations: autonomous vehicles, banking fraud detection, medical diagnostics, hiring, mortgage approvals, predictive policing, pandemic triage, and aerospace predictive maintenance. Includes supporting references. |
| 3 | [ESM_3_Revised.pdf](ESM_3_Revised.pdf) | Demographic and professional characteristics of the 35 stakeholder interviewees, including the composition of the two original interview waves. |
| 4 | [ESM4_Revised.pdf](ESM4_Revised.pdf) | The OG-RE4AI research interview protocol. Questions relevant to exploring human-oversight aspects are marked in bold italics; their scope also includes other AI-system requirements. |
| 5 | [ESM_5_revised.xlsx](ESM_5_revised.xlsx) | Stakeholder-interview coding record, quotation references, anonymised interview IDs, excerpt texts, open codes, initial theme assignments, and assignments after peer debriefing. The Readme explains the counting units, coding changes, and mapping to manuscript theme names. |
| 6 | [ESM_6_Revised.pdf](ESM_6_Revised.pdf) | Retrospective worked MCDA illustration based on the Uber ATG accident context, with author-assigned scores, baseline weights, four weight-sensitivity scenarios, limitations, and references. |
| 7 | [ESM_7_Revised.pdf](ESM_7_Revised.pdf) | Expert-evaluation protocol and thematic analysis for five experts. Includes theme coverage in Version 1, expert identifiers, supporting-record counts, and illustrative passages used to explain framework developments or retained elements. |
| 8 | [ESM_8_Revised.xlsx](ESM_8_Revised.xlsx) | Survey responses from 58 practitioners and corrected analyses: age-group recoding, familiarity-category harmonisation, descriptive statistics, and exploratory comparisons by risk profile, familiarity, role, and age. Reports tie-corrected H, degrees of freedom, valid sample sizes, effect sizes, and unadjusted and adjusted p-values. |
| 9 | [ESM_9_R_analysis.zip](ESM_9_R_analysis.zip) | Reproducibility package containing the R script, respondent-level input CSV, generated results, execution-environment information, and an R-specific README with run instructions. |

## Study stages and interpretation

**Stage 1 — Problem-domain exploration and initial artifact construction.** The OG-RE4AI conceptual foundation, human-oversight literature, documented AI-system cases, and focused analysis of existing stakeholder interviews supported RE4HOAI Version 1, reported in Sadovski et al. (2025). Online Resources 1–5 document this foundation.

**Stage 2 — Artifact evolution and assessment.** Formative evaluation by five experts informed substantial development of Version 1's operational content, decision points, and oversight mechanisms while preserving its six-phase structure. Online Resource 7 documents this feedback. A subsequent survey examined practitioner attitudes and preferences concerning core oversight concerns mapped to RE4HOAI; Online Resources 8–9 provide the survey data and analyses.

Survey respondents were not shown RE4HOAI. Agreement with framework-derived statements provides complementary evidence about alignment with practitioner concerns; it does not directly establish the complete framework's clarity, usefulness, implementation feasibility, or effectiveness in practice.

The case illustrations in Online Resource 2 provide contextual grounding rather than independent evaluations. Online Resource 6 demonstrates an MCDA calculation and weight sensitivity, not improved real-world safety, validation of RE4HOAI, or a completed Win-Win negotiation process.

## Reading the stakeholder coding record

Online Resource 5 distinguishes the following units:

- **123 coding rows**, representing **94 distinct excerpt texts** from **27 of the 35 stakeholder interviews**.
- **47 initial open codes**, consolidated into five higher-level themes.
- **121 rows with retained final theme assignments**; two rows marked `none` remain in the audit record but have no final theme assignment.
- **158 final theme assignments** across the retained rows. A row can support more than one theme.

The peer-debriefing comparison records 104 unchanged rows, 14 rows receiving additional assignments, two reassignments, one partial removal, and two exclusions. These are counts of coding rows, not counts of distinct excerpts or participants.

The final summary maps the recorded coding labels to the theme names used in the manuscript: Oversight spectrum (35 assignments), Safety insights (12), Explainability necessity (49), Trust enablers (33), and Feedback and monitoring (29). Rephrasing theme names does not change the coding assignments. Case and spelling variants are harmonised for these counts.

## Reproducing the survey analysis

Download and extract **Online Resource 9**. Its folder structure is:

```text
analyse_survey.R
survey_input.csv
R_README.md
R_results/
    analysis_summary.txt
    demographics.csv
    descriptive_statistics.csv
    exploratory_tests.csv
    group_summaries.csv
    independent_verification.txt
    nominal_comparisons.csv
    processed_responses.csv
    R_citation.txt
    sessionInfo.txt
    Table_6.csv
    Table_7_unadjusted_and_Holm.csv
```

From the extracted directory, run:

```sh
Rscript analyse_survey.R survey_input.csv R_results
```

Alternatively, in the RStudio Console, set the working directory to the extracted folder and run:

```r
source("analyse_survey.R")
analyse_survey("survey_input.csv", "R_results")
```

The script uses standard R functions, including `stats::kruskal.test()` and `stats::p.adjust()`. No contributed R packages are required. The supplied results record R 4.6.0 and stats 4.6.0; `sessionInfo.txt` identifies the execution environment. Consult `R_README.md` for the recorded execution method and detailed analysis decisions.

### R input and outputs

| File | Contents |
| --- | --- |
| `survey_input.csv` | Input records for 58 respondents: sequential respondent ID, numerical age, role, perceived risk profile, AI familiarity, and responses to Statements S1–S11. Missing item responses are blank. |
| `analyse_survey.R` | Data validation, familiarity harmonisation, age recoding, descriptive analysis, itemwise missing-response handling, group eligibility, Kruskal–Wallis tests, effect-size calculation, and multiplicity adjustment. |
| `R_README.md` | Instructions, data provenance, analysis decisions, output descriptions, and execution details. |
| `R_results/processed_responses.csv` | Responses after familiarity harmonisation and age-group recoding. |
| `R_results/demographics.csv` | Counts and percentages for the four grouping variables, with eligibility for group comparisons. |
| `R_results/descriptive_statistics.csv` | Valid and missing counts, means, sample and population standard deviations, medians, ranges, and five-category response frequencies for each statement. |
| `R_results/Table_6.csv` | Valid counts, means, population standard deviations, and ranges corresponding to manuscript Table 6. |
| `R_results/exploratory_tests.csv` | All 44 comparisons, including H, degrees of freedom, valid sample and group sizes, effect-size estimates, and unadjusted, Holm-adjusted, and Bonferroni-adjusted p-values. |
| `R_results/Table_7_unadjusted_and_Holm.csv` | Unadjusted p-values with Holm-adjusted values in parentheses, corresponding to manuscript Table 7. |
| `R_results/group_summaries.csv` | Statement-specific valid counts, means, and medians for each included comparison group. |
| `R_results/nominal_comparisons.csv` | The five comparisons with unadjusted p-values below .05. This is a convenience subset of `exploratory_tests.csv`; none remains significant after correction across all 44 tests. |
| `R_results/analysis_summary.txt` | Summary of the run, comparison counts, adjusted-significance results, and analysis notes. |
| `R_results/sessionInfo.txt` | R version, platform, locale, and package information for the recorded run. |
| `R_results/R_citation.txt` | Citation information generated by R. |
| `R_results/independent_verification.txt` | Historical comparison of the recorded R results with earlier independently calculated results. This file is not regenerated by the basic command above. |

The basic run regenerates the primary analysis outputs. The optional reference-comparison mode described in `R_README.md` additionally requires the earlier reference-results directory; that directory is not required for the primary analysis.

### Analysis conventions

- `Basic familiarity` is merged into `Basic` before analysis.
- Numerical ages are recoded into 18–34, 35–44, 45–64, and 65+.
- Groups with fewer than five respondents are excluded before itemwise deletion. The age comparisons therefore include only ages 35–44 and 45–64.
- Missing responses are excluded separately for each statement without imputation. Statements 1, 5, and 10 each have one missing response.
- The 44 tests form one family for Holm and Bonferroni adjustment. Nominal differences are interpreted as exploratory; lack of adjusted significance does not establish equivalence between groups.
- Effect sizes use `eta_squared_H = (H - k + 1) / (n - k)`, where `k` is the number of included groups and `n` is their total non-missing sample size for the statement. Negative estimates are retained.
- Both standard-deviation estimators are exported. Manuscript Table 6 uses the population standard deviation.

## Article citation

Sadovski, E., Aviv, I., & Hadar, I. **How Teams Decide on Human Oversight in AI-Powered Systems: A Mixed-Methods Study.** Empirical Software Engineering.

## Contact

**Eran Sadovski**  
Email: [sdv.eran@gmail.com](mailto:sdv.eran@gmail.com)
