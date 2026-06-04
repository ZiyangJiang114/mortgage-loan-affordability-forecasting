# Mortgage Loan Affordability Forecasting

## Project Overview

This capstone project applies machine learning and time-series forecasting to estimate mortgage borrowing capacity and project how affordability may change over a 10-year planning horizon.

The project has two connected modeling components:

1. A supervised regression model that predicts the maximum mortgage loan amount a borrower may be approved for based on borrower profile, income, credit, employment, and financial-status variables.
2. A time-series mortgage-rate projection that creates a future rate path with historical-style month-to-month fluctuation, then uses that forecast to estimate future borrowing capacity.

The final output is a forward-looking affordability planning tool that connects borrower-level machine learning with mortgage-rate forecasting.

## Research Question

How can borrower characteristics and future mortgage-rate assumptions be combined to estimate a borrower's current and future maximum mortgage loan capacity?

Sub-questions include:

- Which borrower and financial features are most related to maximum approved mortgage loan amount?
- Which regression model provides the strongest predictive performance?
- How can historical 30-year fixed mortgage-rate data be used to create a practical 10-year planning scenario?
- How does projected income growth and mortgage-rate movement affect future borrowing capacity?

## Notebook Workflow

### 1. Exploratory Data Analysis

Notebook: `1_Mortgage_Loan_EDA.ipynb` loads the mortgage loan dataset, reviews data quality, analyzes the target variable, explores numerical and categorical feature relationships, performs feature engineering, and saves an engineered dataset for modeling.

Main outputs:

- Data-quality review
- Target-variable distribution
- Numerical and categorical feature analysis
- Engineered borrower-level features

### 2. Regression Modeling and Evaluation

Notebook: `2_Modeling_Evaluation_final_screened.ipynb` trains and evaluates candidate regression models to predict the maximum approved mortgage loan amount.

Candidate models include:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regressor
- Gradient Boosting Regressor

The final selected model is saved for use in the projection notebook.

Main outputs:

- Model comparison table
- Cross-validation results
- Final model diagnostics
- Feature-importance analysis

### 3. Mortgage-Rate Forecasting and 10-Year Projection

Notebook: `3_Forecasting_Projection_final_screened.ipynb` loads the trained regression model and historical 30-year fixed mortgage-rate data. It creates a 10-year mortgage-rate forecast path and uses borrower assumptions to project future borrowing capacity.

The time-series section uses a central trend forecast combined with historically sampled monthly fluctuations. This creates a future rate path that behaves more like real mortgage-rate data than a flat rolling-average forecast.

Main outputs:

- Historical mortgage-rate analysis
- 10-year fluctuating mortgage-rate forecast
- User-input borrower profile
- Projected annual income and savings assumptions
- 10-year estimated borrowing capacity projection

## Data Sources

This project uses two input datasets:

1. `mortgage_loan_dataset.csv`  from Kaggle
   [Borrower-level mortgage loan dataset used for exploratory analysis and regression modeling.](https://www.kaggle.com/datasets/chukwuemeka64/mortgage-data/data?select=mortgage_loan_dataset.csv)

2. `MORTGAGE30US-2.csv`  from FRED
  [ Historical 30-year fixed mortgage-rate dataset used for time-series forecasting and future affordability projection.
](https://fred.stlouisfed.org/series/MORTGAGE30US)
## Methods

### Feature Engineering

Feature engineering includes borrower financial ratios and categorical transformations such as:

- Debt-to-income ratio
- Loan repayment rate
- Credit score category
- Income category

These engineered features help connect borrower financial condition to predicted loan capacity.

### Regression Modeling

The regression task predicts:

```text
Max Loan Amount (USD)
```

Model performance is evaluated using:

- Mean Absolute Error
- Root Mean Squared Error
- R-squared
- Cross-validation RMSE

Tree-based ensemble models provided the strongest performance, with Gradient Boosting selected as the final model based on test-set and cross-validation results.

### Time-Series Forecasting

The mortgage-rate projection uses:

- A rolling-average baseline
- An Exponential Smoothing central trend
- A simulated fluctuating forecast path based on historical monthly rate changes

The fluctuating forecast is intended as a planning scenario rather than a precise prediction of future mortgage rates.

## Key Results

The supervised learning portion showed that machine learning models can estimate maximum approved mortgage loan amount with strong predictive performance. Linear models provided a strong baseline, while ensemble models improved prediction accuracy by capturing nonlinear relationships between borrower characteristics and loan capacity.

The projection notebook demonstrates how the trained loan model can be combined with mortgage-rate forecasting, income growth assumptions, and savings assumptions to estimate a borrower's future affordability path over 10 years.
