# Project 2: Data and Statistical Reasoning

**Analytical question:** Do secondary-school students who report more weekly study time earn higher final grades in Portuguese?

This project answers that question with a complete statistical workflow: initial data screening, descriptive statistics, four visual models, and a hypothesis test (Welch's one-way ANOVA), written up in an APA-formatted report.

**Dataset:** Cortez, P. (2008). *Student performance* [Data set]. UCI Machine Learning Repository. https://archive.ics.uci.edu/dataset/320/student+performance (https://doi.org/10.24432/C5TG7T)

The file `student-por.csv` is the original, unmodified Portuguese-course file. It is a real, publicly available dataset (CC BY 4.0) with 649 rows and 33 columns: 16 numeric (including the final grade `G3`) and 17 categorical (such as `school` and `sex`). The CSV uses semicolons as its delimiter, so the notebook loads it with `sep=";"`.

## Submission files

| File | Purpose |
|---|---|
| `analysis.ipynb` | Full analysis: loading, initial data screening, descriptive statistics, visual models, hypothesis test, summary |
| `module_summary.pdf` | Statistical analysis report with in-text citations and a References section |
| `requirements.txt` | Pinned environment, generated with `pip freeze > requirements.txt` |
| `student-por.csv` | Original dataset file |

Supporting files: `module_summary.docx` (editable source of the report), `figures/` (charts saved by the notebook on every run), and this README.

## Key findings

- Fifteen students with a final grade of 0 were judged to be not assessed and excluded before testing (n = 634). A sensitivity analysis that keeps them gives the same conclusion.
- Mean final grade rises from 11.3 (under 2 hours of study per week) to 13.2 (5 to 10 hours), then levels off (13.1 for over 10 hours).
- Welch's ANOVA: *F*(3, 133.4) = 16.42, *p* < .001. The effect is modest: study time explains about 7% of the variance in grades (η² = .068).
- The data are observational, so this is an association, not proof that studying more causes higher grades. School and past failures are likely confounders.

## How to run

Requires **Python 3.12 or newer**, because the pinned NumPy and SciPy versions need it. The environment was built and tested with Python 3.13.

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook analysis.ipynb
```

In Jupyter, choose **Kernel > Restart Kernel and Run All Cells**. Or run the whole notebook from the terminal:

```bash
jupyter nbconvert --to notebook --execute --inplace analysis.ipynb
```

The notebook runs top to bottom without errors and regenerates every figure in `figures/`.
