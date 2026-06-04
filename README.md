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

## Repository Structure

```text
.
├── README.md
├── mortgage_loan_dataset.csv
├── MORTGAGE30US-2.csv
├── 1_Mortgage_Loan_EDA_final_screened.ipynb
├── 2_Modeling_Evaluation_final_screened.ipynb
├── 3_Forecasting_Projection_final_screened.ipynb
└── outputs/
    ├── processed_data/
    │   └── mortgage_loan_dataset_engineered.csv
    ├── models/
    │   ├── best_mortgage_loan_model.joblib
    │   └── model_metadata.json
    ├── model_reports/
    │   ├── model_comparison_results.csv
    │   ├── final_model_comparison_results.csv
    │   └── feature_importance.csv
    ├── projection_reports/
    │   ├── ten_year_mortgage_rate_forecast.csv
    │   ├── user_10_year_loan_capacity_projection.csv
    │   └── projection_summary.csv
    └── plots/
```

## Notebook Workflow

### 1. Exploratory Data Analysis

Notebook: `1_Mortgage_Loan_EDA_final_screened.ipynb`

This notebook loads the mortgage loan dataset, reviews data quality, analyzes the target variable, explores numerical and categorical feature relationships, performs feature engineering, and saves an engineered dataset for modeling.

Main outputs:

- Data-quality review
- Target-variable distribution
- Numerical and categorical feature analysis
- Engineered borrower-level features
- Processed dataset saved to `outputs/processed_data/`

### 2. Regression Modeling and Evaluation

Notebook: `2_Modeling_Evaluation_final_screened.ipynb`

This notebook trains and evaluates candidate regression models to predict the maximum approved mortgage loan amount.

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
- Trained model saved to `outputs/models/best_mortgage_loan_model.joblib`
- Model metadata saved to `outputs/models/model_metadata.json`

### 3. Mortgage-Rate Forecasting and 10-Year Projection

Notebook: `3_Forecasting_Projection_final_screened.ipynb`

This notebook loads the trained regression model and historical 30-year fixed mortgage-rate data. It creates a 10-year mortgage-rate forecast path and uses borrower assumptions to project future borrowing capacity.

The time-series section uses a central trend forecast combined with historically sampled monthly fluctuations. This creates a future rate path that behaves more like real mortgage-rate data than a flat rolling-average forecast.

Main outputs:

- Historical mortgage-rate analysis
- 10-year fluctuating mortgage-rate forecast
- User-input borrower profile
- Projected annual income and savings assumptions
- 10-year estimated borrowing capacity projection
- Projection summary saved to `outputs/projection_reports/`

## Data Sources

This project uses two input datasets:

1. `mortgage_loan_dataset.csv`  
   Borrower-level mortgage loan dataset used for exploratory analysis and regression modeling.

2. `MORTGAGE30US-2.csv`  
   Historical 30-year fixed mortgage-rate dataset used for time-series forecasting and future affordability projection.

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

## How to Run the Project

Run the notebooks in this order:

```text
1_Mortgage_Loan_EDA_final_screened.ipynb
2_Modeling_Evaluation_final_screened.ipynb
3_Forecasting_Projection_final_screened.ipynb
```

Required input files should be placed in the repository root:

```text
mortgage_loan_dataset.csv
MORTGAGE30US-2.csv
```

The first notebook creates the processed dataset used by the second notebook. The second notebook saves the trained model and metadata used by the third notebook.

## Python Packages

The project uses the following major Python libraries:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
statsmodels
joblib
```

A typical installation command is:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels joblib
```

## Key Results

The supervised learning portion showed that machine learning models can estimate maximum approved mortgage loan amount with strong predictive performance. Linear models provided a strong baseline, while ensemble models improved prediction accuracy by capturing nonlinear relationships between borrower characteristics and loan capacity.

The projection notebook demonstrates how the trained loan model can be combined with mortgage-rate forecasting, income growth assumptions, and savings assumptions to estimate a borrower's future affordability path over 10 years.

## Limitations

This project should be interpreted as an educational and analytical machine learning project, not as financial advice or a production loan-approval system.

Important limitations include:

- Mortgage rates are affected by macroeconomic factors that are difficult to forecast over long horizons.
- The fluctuating rate forecast is a scenario simulation, not a guaranteed prediction.
- The regression model depends on the quality, representativeness, and feature coverage of the available mortgage dataset.
- Real lending decisions may include additional underwriting rules, lender-specific policies, regional housing-market factors, debt obligations, taxes, insurance, and regulatory requirements.
- The user projection is sensitive to assumed income growth, savings rate, down payment, and future mortgage-rate movement.

## Project Deliverables

Final project deliverables include:

- Clean exploratory data analysis notebook
- Regression modeling and evaluation notebook
- Forecasting and 10-year projection notebook
- Saved trained model and metadata
- Model-performance reports
- Forecast and user-projection reports
- README documentation

## Suggested GitHub Repository Name

Recommended repository name:

```text
mortgage-loan-affordability-forecasting
```

Recommended GitHub display title:

```text
Mortgage Loan Affordability Forecasting
```

Recommended short description:

```text
Machine learning and time-series forecasting project for mortgage loan capacity prediction and 10-year affordability projection.
```

## Author

Ziyang Jiang

UC Berkeley Machine Learning and Artificial Intelligence Capstone Project
