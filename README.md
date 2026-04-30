# RR_project_Group-13

# House Prices: R to Python Translation & Extension

## Project Aim & Motivation
This project is a **reproducible research study** focused on translating a high-performing R-based housing price prediction model into Python. The primary goal is to verify if the analytical conclusions of the original study hold true across different programming environments and to extend the research by testing the robustness of various regularization techniques.

### Why this project?
*   **Reproducibility:** Scientific and data-driven insights must be reproducible. We aim to replicate the Cross-Validation (CV) RMSE of the original study.
*   **Cross-Language Translation:** Translating logic from R (`glmnet`, `xgboost`, `ggplot2`) to Python (`scikit-learn`, `xgboost`, `matplotlib/seaborn`) ensures a deep understanding of library-specific hyperparameter defaults and data scaling.
*   **Extension:** Beyond mere reproduction, we investigate whether the choice of regularization (**LASSO vs. Ridge vs. Elastic Net**) significantly alters feature importance or predictive performance.

---

## Project Workflow

### 1. Exploratory Data Analysis (EDA)
Following the original source, we analyzed 79 explanatory variables of residential homes in Ames, Iowa.
*   **Target Transformation:** Addressed the right-skewness of `SalePrice` using a `log1p` transformation.
*   **Feature Correlation:** Identified key drivers such as `OverallQual` ($r=0.79$) and `GrLivArea` ($r=0.71$).
*   **Outlier Detection:** Visualized and flagged specific outliers (#523 and #1298) characterized by massive living areas but unusually low prices.

### 2. Preprocessing & Feature Engineering
*   **Imputation:** Implemented a complex strategy using Neighborhood medians for `LotFrontage` and categorical modes for `MSZoning`.
*   **Ordinal Encoding:** Converted categorical quality scales (e.g., Excellent to Poor) into numeric integers.
*   **Handling Skewness:** Applied `log1p` transformations to 203 numeric features with absolute skewness $> 0.75$.
*   **Encoding:** Expanded categorical variables via one-hot encoding, resulting in a 233-feature dataset.

### 3. Core Models & Reproduction
We targeted the reproduction of two specific models:
*   **LASSO:** Used for automatic feature selection in the presence of high multicollinearity.
*   **XGBoost:** A gradient boosting framework used to capture non-linear relationships.
