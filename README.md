# Predicting Paddy Yield Using Regression

### Machine Learning Project for Paddy Yield Prediction
## Project Objective

Agricultural productivity depends on several factors, including crop characteristics, environmental conditions, soil properties, and weather conditions.

The objective of this project is to analyze paddy cultivation data and build regression models to predict **Paddy Yield per Hectare**.

The project follows a complete machine learning workflow, including data cleaning, exploratory data analysis, feature engineering, multicollinearity analysis using **Variance Inflation Factor (VIF)**, dimensionality reduction using **Principal Component Analysis (PCA)**, regression modeling, and model evaluation.

The project also compares model performance across different feature-selection and preprocessing approaches to understand their impact on prediction accuracy.
## Dataset

The dataset contains information related to paddy cultivation, including agricultural, environmental, weather, soil, and crop-related variables.

### Dataset Details

- **Rows:** 2,789
- **Columns:** 45
- **Numerical Variables:** 37
- **Categorical Variables:** 8
- **Missing Values:** No missing values
- **Duplicate Records:** 451 duplicates identified and removed
- **Target Variable:** Yield per Hectare

###  Paddy Varieties

The dataset includes the following paddy varieties:

- CO_43
- Ponmani
- Delux Ponni

### Agricultural Areas

The dataset includes information from:

- Panruti
- Cuddalore
- Kurinjipadi

## Project Workflow

The project was completed through the following stages:

1. **Data Understanding**
   - Loaded and inspected the paddy cultivation dataset
   - Examined the structure, data types, and statistical summary of the data

2. **Data Preprocessing**
   - Checked for missing values
   - Identified and removed duplicate records
   - Examined potential outliers
   - Prepared numerical and categorical variables for analysis

3. **Exploratory Data Analysis (EDA)**
   - Performed univariate analysis
   - Performed bivariate analysis
   - Performed multivariate analysis
   - Analyzed relationships between features and paddy yield

4. **Statistical Analysis**
   - Performed statistical tests to understand relationships within the data

5. **Feature Encoding & Standardization**
   - Encoded categorical variables
   - Standardized the features before modeling

6. **Yield per Hectare**
   - Created a new target variable, **Yield per Hectare**, using paddy yield and cultivated area

7. **Regression Modeling**
   - Built multiple regression models
   - Compared model performance using R², MAE, and RMSE

8. **Multicollinearity Analysis**
   - Used **Variance Inflation Factor (VIF)** to identify highly correlated features

9. **Feature Engineering**
   - Created per-hectare features for selected agricultural inputs

10. **Dimensionality Reduction**
    - Applied **Principal Component Analysis (PCA)**
    - Retained 95% of the variance in the dataset

11. **Model Comparison**
    - Compared model performance across different feature-selection and preprocessing approaches

12. **Feature Importance**
    - Analyzed feature importance using XGBoost to identify influential variables
