# Retail Sales Prediction and Inventory Analysis using Machine Learning

## Project Overview

This project implements an end-to-end Machine Learning solution to predict retail product sales using historical sales data and product and outlet-related information.

The system analyzes factors such as product weight, visibility, price, item category, outlet size, location, and establishment year to understand their relationship with sales performance.

Multiple regression algorithms are developed and evaluated to identify the best-performing model. The selected XGBoost model is then used to predict sales for unseen test data and estimate future sales for inventory planning.

The project also incorporates a basic inventory risk analysis mechanism to identify potential stockout and overstock situations by comparing predicted sales with available stock.

## Dataset

The project uses the BigMart Sales Prediction dataset, consisting of product-level and outlet-level information.

**Training Dataset:** 8,523 records.

**Features include:**
- Item Identifier
- Item Weight
- Item Fat Content
- Item Visibility
- Item Type
- Item Maximum Retail Price (MRP)
- Outlet Identifier
- Outlet Establishment Year
- Outlet Size
- Outlet Location Type
- Outlet Type

**Target Variable:** `Item_Outlet_Sales`

The dataset contains numerical and categorical variables used to predict product sales across different retail outlets.

## Data Preprocessing and Exploratory Data Analysis

The dataset was explored and prepared before model development.

**Key Implementations:**

- Inspected dataset structure, data types, and statistical summaries.
- Identified and handled missing values using median and mode imputation.
- Checked for duplicate records.
- Standardized inconsistent categorical values in Item Fat Content.
- Analyzed sales distributions and relationships between numerical and categorical features.
- Used histograms, boxplots, scatterplots, bar plots, and correlation heatmaps for visualization.
- Applied logarithmic transformation to the target variable to modify its distribution.

## Feature Engineering

Additional features were created to improve the model's ability to capture meaningful relationships in the dataset.

- **Outlet Age:** Calculated using the outlet establishment year.
- **MRP per Visibility:** Derived by relating product price to its visibility.
- **Is Food Item:** Created a binary feature to distinguish food and non-food product categories.

Categorical variables were encoded using Label Encoding before model training.

## Machine Learning Models

Three regression algorithms were implemented and compared:

### 1. Linear Regression

Used as a baseline regression model to understand the relationship between input features and retail sales.

### 2. Random Forest Regressor

Implemented an ensemble learning approach using multiple decision trees to capture nonlinear relationships and improve prediction performance.

### 3. XGBoost Regressor

Implemented gradient boosting to improve predictive performance. RandomizedSearchCV was used for hyperparameter optimization with 5-fold cross-validation and 30 parameter combinations.

The best-performing XGBoost configuration was selected based on cross-validation performance.

## Model Evaluation and Comparison

The models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score
- 5-Fold Cross-Validation

**Model Comparison Results:**

| Model | Validation R² | CV Mean R² |
|---|---:|---:|
| Linear Regression | 0.6015 | 0.5921 |
| Random Forest | 0.7164 | 0.7010 |
| XGBoost | 0.7411 | 0.7343 |

**Best Performing Model: XGBoost Regressor**

The XGBoost model achieved the highest validation R² score of **0.7411** and a cross-validation mean R² score of **0.7343**, outperforming the other evaluated models.

## Feature Importance Analysis

Feature importance was extracted from the trained XGBoost model and visualized to understand which input variables contributed most to the predictions.

This analysis helps identify important factors influencing retail sales and provides insights into product and outlet characteristics.

## Sales Prediction and Inventory Analysis

The selected XGBoost model was used to generate predictions for the unseen test dataset.

**Key Implementations:**

- Generated sales predictions for test records.
- Reversed the logarithmic target transformation using `expm1()` to obtain predictions in the original sales scale.
- Added predicted sales as a new column.
- Exported the results to `sales_predictions.csv`.
- Tested the model using manually supplied future product and outlet information.
- Compared predicted sales against available stock to identify inventory risks.

**Inventory Risk Categories:**

- **Stockout Risk:** Predicted sales exceed available stock.
- **Overstock Risk:** Predicted sales are below 70% of available stock.
- **Optimal Stock:** Predicted sales fall within the defined inventory range.

This provides a basic demonstration of how sales forecasting can support inventory planning.

## Model Saving and Loading

The trained XGBoost model was saved using Joblib for future use.

**Saved Model:** `retail_sales_model.pkl`

The saved model was successfully loaded to demonstrate model persistence and reuse without retraining.

## Technologies and Libraries Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Joblib
- Machine Learning
- Regression Analysis
- Hyperparameter Tuning
- Exploratory Data Analysis
- Feature Engineering
- Predictive Analytics

## Key Learnings

- Working with real-world retail sales datasets.
- Handling missing values and inconsistent categorical data.
- Performing exploratory data analysis and feature engineering.
- Implementing and comparing multiple regression algorithms.
- Applying cross-validation and hyperparameter tuning.
- Evaluating models using regression metrics.
- Understanding feature importance and model performance.
- Generating sales predictions for unseen data.
- Applying predictive modeling to basic inventory risk analysis.
- Saving and loading trained Machine Learning models.
