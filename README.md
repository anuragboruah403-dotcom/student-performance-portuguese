# Student Performance Analysis — Portuguese Language Course

## Overview
This project analyzes the [UCI Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance) (Portuguese language course), exploring which factors — study time, past failures, parental education, alcohol consumption, and internet access — relate to a student's final grade. It also includes a machine learning model that predicts a student's final grade from their earlier academic performance.

## Dataset
651 students, 33 features, covering demographics, family background, lifestyle habits, and three period grades (G1, G2, G3 — each out of 20). Target variable: **G3**, the final grade.

## What's in this repo
- `portuguese_analysis.ipynb` — the full analysis notebook (data cleaning, visualization, and a regression model)
- `Portuguese.csv` — the dataset used
- `README.md` — this file

## Tools used
Python, pandas, matplotlib, seaborn, scikit-learn (Google Colab)

## Approach
1. Loaded and inspected the dataset (651 records, 2 duplicate rows removed, no missing values)
2. Engineered a pass/fail flag (G3 ≥ 10 = pass)
3. Visualized final grade distribution and compared it across study time, past failures, alcohol consumption, parental education, internet access, and extra academic support
4. Built a correlation heatmap across all numeric features against the final grade
5. Trained a linear regression model to predict G3 using G1, G2, study time, failures, and absences, evaluated using MAE and R²

## Key findings
- **Past failures are the strongest negative predictor of final grade** (correlation ≈ −0.39) — a bigger effect than alcohol consumption, study time, or absences.
- **Study time has a positive but modest relationship with final grade**: students studying 5–10 hours/week averaged ~13.2, versus ~10.8 for students studying under 2 hours/week.
- **Earlier-term grades are highly predictive of the final grade**: G2 alone correlates at 0.92 with G3, and G1 at 0.83 — performance is quite consistent across the year.
- A linear regression using G1, G2, study time, failures, and absences predicted final grade with **R² = 0.863** and **MAE = 0.75** — on average, predictions were within less than 1 grade point (out of 20) of the actual result.

## What I'd explore next
- Try a non-linear model (e.g. Random Forest) to see if it improves on the linear regression baseline
- Investigate the failures/alcohol-consumption relationship further, since both showed negative effects
- Build a version of the model that excludes G1/G2 to see how well demographic and lifestyle features alone can predict performance

## How to run it
1. Open `portuguese_analysis.ipynb` in [Google Colab](https://colab.research.google.com)
2. Upload `Portuguese.csv` into the same session
3. Run all cells top to bottom

**Note:** despite the `.csv` extension, this file is saved internally in Excel format — it's loaded with `pd.read_excel()`, not `pd.read_csv()`.
