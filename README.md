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
| 3 | 2 × logistic regression (high vs. low progression) | All / EDA-selected |

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

## Setup

Requires [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run jupyter lab lab2_diabetes.ipynb
```

## Libraries

numpy · pandas · scikit-learn · matplotlib · seaborn · jupyter
