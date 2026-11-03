# Preregistration: Weekly Study Time and Exam Performance

**Project:** Student Study Time & Exam Performance  
**Version:** 1.0  
**Registration date:** 03 November 2026  
**Dataset status:** Synthetic teaching dataset; no real people or records are represented.

## 1. Research question
Among the simulated students represented in the dataset, is weekly study time associated
with end-of-term exam score after accounting for attendance, prior academic score, and
average nightly sleep?

## 2. Rationale
Study time is a plausible learning-related exposure. Attendance, prior achievement, and
sleep may also be related to exam performance, so they are specified as adjustment variables.
This project demonstrates a transparent analysis workflow; it is not a real-world educational
study.

## 3. Population and observation unit
- Target population for this demonstration: the 500 simulated student records generated for this project.
- Unit of analysis: one simulated student.
- Observation window: one notional academic term.
- No actual students were recruited or observed.

## 4. Exposure, comparator, and outcome
- **Exposure:** `study_hours_per_week`, numeric hours studied per week.
- **Comparator:** students at the 25th percentile of study hours versus students at the 75th
  percentile. These percentiles will be calculated from the exposure variable only.
- **Primary outcome:** `exam_score`, numeric score on a 0–100 scale.
- **Adjustment variables:** `attendance_percent` (0–100), `prior_score` (0–100), and
  `sleep_hours_per_night` (hours/night).

## 5. Hypotheses
- **Null (H0):** The adjusted linear association between weekly study hours and exam score is zero
  (study-hours regression coefficient β1 = 0).
- **Alternative (H1):** The adjusted linear association between weekly study hours and exam score
  is not zero (β1 ≠ 0).

Two-sided significance level: α = 0.05.

## 6. Data handling and exclusions
- Include records with a unique, non-empty `student_id` and all required analysis variables present.
- Exclude rows with missing values in any required variable.
- Exclude rows with values outside these ranges: study hours 0–60; attendance 0–100;
  prior score 0–100; sleep 0–24; exam score 0–100.
- If duplicate IDs occur, stop the pipeline and resolve them rather than silently choosing a row.
- The included dataset is expected to have no missing values, duplicate IDs, or out-of-range values.
- No exclusions will be based on observed exam-score values beyond the prespecified validity range.

## 7. Statistical analysis plan
1. Report the number of records, missingness, and descriptive statistics.
2. Fit an ordinary least squares (OLS) model:
   `exam_score ~ study_hours_per_week + attendance_percent + prior_score + sleep_hours_per_night`.
3. Report the unstandardized study-hours coefficient, 95% confidence interval, p-value,
   model R-squared, and sample size.
4. Use a two-sided test for the primary coefficient at α = 0.05.
5. Report Spearman's rank correlation between study hours and exam score as a secondary,
   unadjusted descriptive association.
6. Do not interpret statistical significance as proof of causality.

## 8. Effect size and interpretation
The primary effect size is the adjusted OLS coefficient: expected difference in exam-score
points associated with one additional weekly study hour, conditional on the specified
adjustment variables. Also report the model R-squared. Interpret the magnitude and uncertainty,
not only the p-value.

## 9. Robustness and diagnostics
- Inspect residual-versus-fitted and Q-Q plots (visual diagnostic only).
- Report HC3 heteroskedasticity-robust standard errors for the primary model.
- Compare the primary OLS estimate with a model using HC3 robust covariance.
- Treat diagnostic findings as caveats; do not change the primary model after seeing results.
- No unregistered subgroup analysis will be used for the primary conclusion.

## 10. Reproducibility and data-blind pipeline check
- Python version target: 3.11.
- Dependencies are pinned in `requirements-lock.txt`.
- The dataset is synthetic and generated with seed `20261103`.
- Unit tests use a separate tiny fixture to verify schema, validation, and model-pipeline behavior.
- Tests do not use the main dataset to decide whether the pipeline is functioning.
- The analysis script saves machine-readable results and a plot in `outputs/`.

## 11. Deviations
Any change to this plan after analysis begins must be recorded here with date, reason, and impact.
No deviations recorded at project creation.
