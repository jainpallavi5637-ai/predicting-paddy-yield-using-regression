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
   
## Multicollinearity Analysis — VIF

Variance Inflation Factor (VIF) was used to identify **multicollinearity** among the numerical features.

The VIF analysis showed very high multicollinearity among several agricultural input and environmental variables. For example, `Seedrate(in Kg)` had an infinite VIF, while several other features had extremely high VIF values.

This indicated that some features were highly correlated and contained overlapping information.

The analysis helped identify features that required further consideration before building the regression models.

### Why VIF?

VIF was used to:

- Detect multicollinearity between independent variables
- Identify highly correlated features
- Improve the quality of the feature set
- Support better interpretation of regression models

## Feature Engineering — Yield per Hectare

To make the analysis more meaningful and comparable across farms of different sizes, a new target variable called **Yield per Hectare** was created.

It was calculated using:

**Yield per Hectare = Paddy Yield (Kg) / Area (Hectares)**

This approach focuses on **production efficiency** rather than total production alone.

### Per-Hectare Features

Additional features were created by converting selected agricultural inputs into per-hectare measures, including:

- Trash per Hectare
- Pest Application per Hectare
- Nursery Input per Hectare
- DAP per Hectare
- Potassium per Hectare
- Micronutrients per Hectare
- Seed Rate per Hectare
- Urea per Hectare
- Weed Control Input per Hectare

These engineered features were used to help the models understand agricultural inputs relative to the cultivated area.

### Why Feature Engineering?

Feature engineering was performed to:

- Account for differences in farm size
- Represent agricultural inputs relative to cultivated area
- Focus on yield efficiency
- Provide more meaningful features for regression modeling
- Improve the model's ability to identify important factors affecting yield per hectare

## Principal Component Analysis (PCA)

Principal Component Analysis (PCA) was applied to reduce the dimensionality of the feature set while retaining most of the information present in the original data.

In this project:

- **Original features:** 42
- **Principal Components retained:** 8
- **Variance retained:** 96.69%

PCA was performed using `PCA(n_components=0.95)`, which selected the number of components required to retain at least 95% of the variance.

### Why PCA?

PCA was used to:

- Reduce the number of features
- Handle information from correlated variables
- Create a more compact feature representation
- Reduce the complexity of the dataset
- Compare model performance before and after dimensionality reduction

### PCA Model Results

After applying PCA, the regression models produced the following results:

| Model | R² | MAE | RMSE |
|---|---:|---:|---:|
| Linear Regression | 0.366 | 187.017 | 237.419 |
| Random Forest | 0.395 | 181.461 | 231.911 |
| XGBoost | 0.425 | 178.023 | 226.111 |
| Decision Tree | 0.385 | 182.326 | 233.766 |

Among the PCA-based models, **XGBoost performed best with an R² score of 0.425**.

## Regression Models

Since the target variable, **Yield per Hectare**, is continuous, regression algorithms were used for prediction.

The following models were evaluated:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor

The models were evaluated using:

- **R² Score** — measures the proportion of variation explained by the model
- **MAE (Mean Absolute Error)** — measures the average absolute prediction error
- **RMSE (Root Mean Squared Error)** — measures the average magnitude of prediction errors, with greater weight given to larger errors

### Model Performance After Feature Engineering

| Model | R² Score | MAE | RMSE |
|---|---:|---:|---:|
| Linear Regression | 0.371 | 187.929 | 236.437 |
| Decision Tree | 0.377 | 183.455 | 235.354 |
| Random Forest | 0.396 | 181.436 | 231.733 |
| **XGBoost** | **0.432** | **176.946** | **224.660** |

### Best Performing Model

**XGBoost Regressor** achieved the best performance among the models evaluated after feature engineering, with:

- **R² Score:** 0.432
- **MAE:** 176.946
- **RMSE:** 224.660

This indicates that XGBoost provided the strongest predictive performance among the evaluated models for the feature-engineered Yield per Hectare dataset.

## Model Comparison Across Different Approaches

To understand how different preprocessing and feature-selection techniques affected model performance, the XGBoost model was evaluated using different feature sets.

| Approach | R² Score |
|---|---:|
| Original Features | 0.436 |
| After Removing Multicollinearity | 0.433 |
| After Feature Engineering | 0.432 |
| After PCA | 0.425 |

### Key Observation

The results show that the **Original Feature Set achieved the highest R² score (0.436)** among the approaches evaluated.

Feature engineering and PCA provided different representations of the data, but they did not improve the XGBoost R² score compared with the original feature set.

This comparison demonstrates the importance of testing different preprocessing and feature-selection approaches rather than assuming that additional transformations will always improve model performance.

## Feature Importance

Feature importance was analyzed using the **XGBoost Regressor** to understand which variables contributed most to predicting paddy yield.

The feature importance analysis helps identify the agricultural, environmental, and other factors that had greater influence on the model's predictions.

The notebook includes a feature importance visualization showing the **Top 10 important features**.

This analysis helps provide better interpretation of the machine learning model and can support understanding of the factors associated with paddy yield.

## Technologies Used

- **Python**
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical computations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical data visualization
- **Scikit-learn** — Machine learning and preprocessing
- **XGBoost** — Gradient boosting regression
- **Statsmodels** — Statistical analysis and VIF
- **Jupyter Notebook / Google Colab** — Development environment

## Project Structure

```text
predicting-paddy-yield-using-regression/
│
├── README.md
├── paddydataset.csv
├── Yield_Per_hectare_with_VIF_and_PCA.ipynb
└── requirements.txt
