# Student Study Time & Exam Performance — Reproducible Research Project

## Project status
This is a complete, reproducible **demonstration project** for the RabTech Academy task
“Reproducible Research Question & Analysis Preregistration”.

**Important:** The included student dataset is fully synthetic (computer-generated). It is
not real student data and must not be presented as evidence about actual students. The
results demonstrate the analysis workflow only.

## Research question
Among the 500 simulated students in this dataset, is weekly study time associated with
end-of-term exam score, after accounting for attendance, prior score, and sleep?

## Quick start (Python 3.11 recommended)
1. Extract the ZIP file.
2. Open a terminal in this project folder.
3. Create and activate a virtual environment:
   - Windows: `py -3.11 -m venv .venv` then `.venv\\Scripts\\activate`
   - macOS/Linux: `python3.11 -m venv .venv` then `source .venv/bin/activate`
4. Install pinned dependencies: `python -m pip install -r requirements-lock.txt`
5. Run the analysis: `python src/analyze.py`
6. Run the pipeline tests: `python -m unittest discover -s tests -v`

The analysis writes a summary JSON, a regression table CSV, and a scatter plot to `outputs/`.

## Project structure
- `preregistration.md` — hypotheses, variables, exclusions, tests, effect sizes, robustness plan.
- `data/student_performance_synthetic.csv` — deterministic illustrative dataset (n=500).
- `src/analyze.py` — complete analysis pipeline.
- `tests/test_pipeline.py` — data-blind tests using synthetic fixtures.
- `requirements-lock.txt` — pinned Python dependencies.
- `environment.yml` — Conda environment specification.
- `outputs/` — generated report outputs after running the script.
- `analysis_report.md` — interpretation template and synthetic-results note.

## Reproducibility
- Random dataset generation seed: `20261103`.
- Analysis is deterministic for the included data.
- The analysis script checks required columns, ranges, missing values, and duplicate IDs.
- `outputs/analysis_summary.json` records sample size, estimates, p-values, confidence intervals,
  and the dataset SHA-256 hash.
- The test suite uses a tiny artificial fixture and does not inspect the main dataset's outcome
  patterns.

## Interpretation caution
This is observational and synthetic. Association is not causation. The dataset was generated
for learning, so the numeric results are not generalizable. For real research, obtain an
approved, ethically collected, de-identified dataset and preregister before examining outcomes.

## GitHub submission
Create a **public** GitHub repository, for example:
`student-study-time-preregistration`
Upload the extracted project folder contents (not the ZIP alone), then submit the repository URL
in RabTech Academy. Do not upload private student records or API keys.
