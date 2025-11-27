# Project Summary: Regression for Insurance Charges

## Problem Definition (Front Matter)

-   **Project Title:** Regression for Insurance Charges
-   **Author/Alias:** Brendan Reed
-   **Goal:** Predict individual medical insurance charges using
    demographic and health-related features.
-   **Value:** Helps insurers estimate expected charges and helps
    consumers understand cost drivers.

## 1. Identify the Target Variable

-   **Target variable:** `charges`
-   **Type:** Continuous numeric
-   **Data quality:** No missing values; right-skewed distribution with
    real-world outliers.
-   **Why meaningful:** Predicting cost influences budgeting, pricing,
    and consumer expectations.

## 2. Review Feature Variables

-   **Features:** age, bmi, children, sex, smoker, region.
-   **Types:** Mixed numerical and categorical.
-   **Ethical considerations:** sex and smoker may raise fairness
    questions.
-   **Leakage examples:** future medical events, annual billed totals,
    claims after enrollment.

## 3. Understand Relationships and Distributions

-   **Patterns:** Smoker strongly increases charges; bmi and age
    positively correlated with charges.
-   **Multicollinearity:** Minimal.
-   **Transformations:** Scaling via pipeline; polynomial features used
    to capture curvature.
-   **Outliers:** Kept because they represent real medical variability.

## 4. Select the Regression Model

-   **Baseline:** Linear Regression.
-   **Why:** Simple, interpretable, effective for continuous targets.
-   **Assumptions:** linearity, independence, constant variance.
-   **Assumptions met:** Mostly; polynomial terms help capture
    nonlinearities.

## 5. Evaluate Model Performance

### Metrics Used

MAE, MSE, RMSE, R².

### Linear Regression Performance

  Model               R²           MAE           RMSE
  ------------------- ------------ ------------- -------------
  Linear Regression   **0.8589**   **2859.63**   **4680.48**

### Lasso Regression (best α ≈ 29.67)

  Model   R²           MAE       RMSE
  ------- ------------ --------- -------------
  Lasso   **0.8596**   2884.46   **4668.87**

### Polynomial Regression (degree = 3)

  Model                R²       MAE           RMSE
  -------------------- -------- ------------- ---------
  Polynomial (deg=3)   0.8355   **2706.19**   5053.70

(Notebook output showed the polynomial pipeline using degree=3 and
producing these results.)

## 6. Improve the Model

-   **Tried:** Polynomial degree=3, Lasso regression, scaling,
    pipelines.
-   **What helped:** Lasso slightly improved R² & RMSE.
-   **What didn't:** Polynomial degree=3 underperformed; higher
    nonlinearity increased variance.
-   **Future improvements:** Elastic Net, Ridge, engineered medical
    features, log-transforming `charges`.

## 7. Validate and Compare Models

  Model                R²           MAE           RMSE
  -------------------- ------------ ------------- -------------
  Linear Regression    0.8589       2859.63       4680.48
  **Lasso (best α)**   **0.8596**   2884.46       **4668.87**
  Polynomial (deg=3)   0.8355       **2706.19**   5053.70

**Best model:** Lasso (slightly).

**Generalization:** Reasonably strong; no major overfitting.

## 8. Real-World Interpretation

-   **Strongest predictor:** Smoker.
-   **Other effects:** BMI and age meaningful contributors.
-   **Usefulness:** Good for broad cost estimation; not suitable for
    underwriting-level precision.
-   **Limitations:** Small dataset, few medical predictors, high skew.
