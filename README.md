# Diabetes Progression – Lab 2

Predicting **disease progression one year after baseline** with the
[Scikit-Learn Diabetes dataset](https://scikit-learn.org/stable/datasets/toy_dataset.html#diabetes-dataset).
The model is meant as a **screening tool** to help physicians identify patients at risk of progression.

## Models compared

| Part | Models | Features |
|------|--------|----------|
| 2 | Univariate polynomial regression, degree 0 – 5 (6 models) | BMI only |
| 3 | 2 × multivariate polynomial regression (degree > 1) | All / EDA-selected |
| 3 | 2 × decision tree (different `max_depth`) | All / EDA-selected |
| 3 | 2 × k-Nearest Neighbours (different `k`) | All / EDA-selected |
| 3 | 2 × logistic regression (above- vs. below-median progression) | All / EDA-selected |

## Evaluation

- Split: **75 % train / 10 % validation / 15 % test**
- Regression metrics: **R²**, **Mean Absolute Error (MAE)**, **Mean Absolute Percentage Error (MAPE)**
- Model selection on the validation set; the chosen model is reported once on the test set.

## Notebook structure

`lab2_diabetes.ipynb`

**Part 1 – Data**
1. Get the data
2. Frame the problem
3. Exploratory data analysis (statistics, histograms, scatter plots, correlation matrix)
4. Data cleaning
5. Train / validation / test split

**Part 2 – Univariate polynomial regression on BMI**

6. Fit degree 0 – 5 models
7. Train vs. validation comparison table (R², MAE, MAPE)
8. Choose the best model
9. Evaluate on the test set
10. Plot train / validation / test data with the fitted curve
11. Equation of the best model
12. Prediction for a chosen BMI value
13. Number of trainable parameters per model
14. Conclusions and limitations

**Part 3 – Multivariate models**

Steps 6 – 14 repeated for polynomial, decision tree, kNN and logistic regression models.

## Key results (test set)

| Model | R² | MAE | MAPE | Screening recall |
|-------|----|-----|------|------------------|
| BMI only, degree-1 polynomial | 0.20 | 54.9 | 48.8 % | 0.67 |
| kNN (k = 15), 9 features | 0.41 | 45.2 | 40.6 % | 0.83 |
| Logistic regression (C = 1) | – | – | – | 0.87 at threshold 0.35 (0.73 at 0.5) |

- The BMI–progression relationship is essentially linear; degree 1 was chosen, and the validation top scorer (degree 3) is almost identical on test.
- Using all features (minus redundant `tc`) roughly doubles explained variance.
- Degree-3 polynomial (220 parameters) and depth-5 tree overfit badly.
- The logistic threshold (0.35) and model (lowest log-loss) were chosen on validation only; the above-median label is statistical, not clinical.

## Setup

Requires Python 3.12 or newer.

### Option 1 – uv

Requires [uv](https://docs.astral.sh/uv/).

```bash
git clone https://github.com/Namypark/diabetes-progression-lab2.git
cd diabetes-progression-lab2
uv sync
uv run jupyter lab lab2_diabetes.ipynb
```

### Option 2 – pip

```bash
git clone https://github.com/Namypark/diabetes-progression-lab2.git
cd diabetes-progression-lab2
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab lab2_diabetes.ipynb
```

## Libraries

numpy · pandas · scikit-learn · matplotlib · seaborn · jupyter
