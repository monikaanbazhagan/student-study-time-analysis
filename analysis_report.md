# Analysis Report

## Study
Weekly study time and exam score in a synthetic student dataset.

## Dataset
The project contains 500 generated records. The dataset is synthetic and must not be treated
as evidence about real students.

## Preregistered analysis
The primary analysis is an OLS regression of exam score on weekly study hours, attendance,
prior score, and nightly sleep. The primary coefficient is the adjusted association per
additional weekly study hour. HC3 robust standard errors and Spearman correlation are also
reported.

## Results
Run `python src/analyze.py` to create `outputs/analysis_summary.json`,
`outputs/regression_coefficients.csv`, and diagnostic plots. Copy the estimates from the JSON
file here after running the analysis.

## Interpretation
Because the data are simulated, all estimates are instructional examples. They cannot be
generalized to actual students. An association in this observational example does not establish
causation.

## Reproducibility
Run `python -m unittest discover -s tests -v`. The tests use a separate artificial fixture and
check input validation and output generation.
