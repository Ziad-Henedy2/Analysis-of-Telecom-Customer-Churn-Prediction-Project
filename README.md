# Telecom Customer Churn Analysis


## Project Overview

This project analyzes customer behavior in the telecom industry to predict and understand customer churn. We have built predictive models to classify customers into churn or non-churn categories and segmented customers into groups based on shared characteristics. The ultimate goal is to help the telecom company identify factors contributing to customer churn, develop strategies to improve customer retention, and tailor services to different customer segments.

## Team Members

- Basmala Salama
- Mohamed Hany
- Ziad Henedy

## Table of Contents

- [Problem Statement](#problem-statement)
- [Data Dictionary](#data-dictionary)
- [Methodology](#methodology)
  - [Data Preprocessing](#data-preprocessing)
  - [Feature Engineering](#feature-engineering)
  - [Supervised Learning Models](#supervised-learning-models)
  - [Unsupervised Learning Models](#unsupervised-learning-models)
- [Results](#results)
- [Business Insights](#business-insights)
- [Recommendations](#recommendations)
- [Requirements](#requirements)
- [Installation & Usage](#installation--usage)

## Problem Statement

Telco, a telecom company providing home phone and Internet services to 7,043 customers, has observed a decline in customer retention rates. The dataset provides information about which customers have left, stayed, or signed up for their service, along with 20 features including important demographics and service details. The company wants to:
1. Identify factors contributing to customer churn
2. Develop strategies to improve customer retention
3. Tailor services to different customer segments

## Data Dictionary

| Feature | Description |
|---------|-------------|
| Churn | Whether the customer left the company within the last month (Yes/No) |
| gender | Customer's gender (Male/Female) |
| SeniorCitizen | Whether the customer is 65 or older (1/0) |
| Partner | Whether the customer is married (Yes/No) |
| Dependents | Whether the customer lives with any dependents (Yes/No) |
| PhoneService | Whether the customer subscribes to home phone service (Yes/No) |
| MultipleLines | Whether the customer subscribes to multiple telephone lines (Yes/No/No internet service) |
| InternetService | Type of internet subscription (No/DSL/Fiber Optic) |
| OnlineSecurity | Whether the customer subscribes to additional online security service (Yes/No/No internet service) |
| OnlineBackup | Whether the customer subscribes to additional online backup service (Yes/No/No internet service) |
| DeviceProtection | Whether the customer subscribes to device protection plan (Yes/No/No internet service) |
| TechSupport | Whether the customer subscribes to technical support plan (Yes/No/No internet service) |
| StreamingTV | Whether the customer uses internet service to stream TV (Yes/No/No internet service) |
| StreamingMovies | Whether the customer uses internet service to stream movies (Yes/No/No internet service) |
| tenure | Number of months that the customer has been with the company |
| Contract | Customer's contract type (Month-to-Month/One Year/Two Year) |
| PaperlessBilling | Whether the customer has chosen paperless billing (Yes/No) |
| PaymentMethod | Customer's payment method (Electronic check/Credit Card/Mailed Check/Bank transfer) |
| MonthlyCharge | Customer's current total monthly charge |
| TotalCharges | Customer's total charges, calculated to the end of the quarter |
| CustomerID | Unique identifier for the customer |

## Methodology

### Data Preprocessing

1. **Data Cleaning**
   - Removed unnecessary columns (CustomerID)
   - Handled missing values in TotalCharges
   - Converted data types where necessary
   - Replaced string values like 'No internet service' with 'No'

2. **Encoding and Scaling**
   - Applied Label Encoding to binary categorical variables
   - Applied One-Hot Encoding to multi-category variables
   - Used Min-Max Scaling for MonthlyCharges, TotalCharges, and tenure

3. **Handling Class Imbalance**
   - Applied SMOTE (Synthetic Minority Over-sampling Technique) to balance the dataset

### Feature Engineering

1. **Feature Selection**
   - Performed Pearson Correlation Analysis to identify and address multicollinearity
   - Used Fisher Score (ANOVA F-value) to rank features by importance
   - Selected top 12 features for model building

2. **Dimensionality Reduction**
   - Applied Principal Component Analysis (PCA)
   - Explored Linear Discriminant Analysis (LDA)

### Supervised Learning Models

We implemented and compared several classification algorithms:

1. **Logistic Regression**
   - Trained baseline model without penalties
   - Performed hyperparameter tuning using Randomized Search
   - Optimized regularization and penalty type

2. **Decision Trees**
   - Identified and addressed overfitting
   - Optimized hyperparameters like min_samples_split, max_depth, and max_features
   - Extracted top 10 most important features

3. **Random Forest**
   - Tuned hyperparameters using Randomized Search and Grid Search
   - Optimized for better regularization and complexity control

4. **XGBoost**
   - Identified top five important features
   - Tuned hyperparameters using Randomized Search, Grid Search, and Optuna
   - Selected as final model due to superior performance

5. **Voting Classifier**
   - Combined XGBoost, Random Forest, and Logistic Regression
   - Leveraged strengths of individual models

### Unsupervised Learning Models

We applied clustering techniques to segment customers:

1. **K-Means Clustering**
   - Applied to features "MonthlyCharges" and "tenure"
   - Identified optimal number of clusters (K=4) using elbow method
   - Evaluated performance using silhouette score

2. **Hierarchical Clustering**
   - Generated dendrogram using Ward's method
   - Applied Agglomerative Clustering with four clusters
   - Analyzed distribution of features across clusters

## Results

Our analysis revealed several key findings:

- Customer segments with higher churn rates were identified through clustering
- XGBoost outperformed other models with superior precision, recall, and F1-score
- Four distinct customer clusters were identified with varying churn propensities
- Clusters 0 and 1 showed higher churn rates compared to Clusters 2 and 3
- High-risk clusters were associated with shorter tenures, month-to-month contracts, higher percentages of senior citizens, and lack of online security services

## Business Insights

- **Customer Tenure**: Shorter tenures in high-risk clusters suggest new customers may not be finding value in the service.
- **Service Utilization**: The absence of online security services in higher-risk clusters indicates a potential gap in customer needs.
- **Demographic Insights**: Higher percentage of senior citizens in high-risk clusters points to the need for tailored communication and services.
- **Contract Strategies**: Customers on month-to-month contracts are more likely to churn.
- **Payment Preferences**: Higher-risk segments show preference for simpler payment methods.

## Recommendations

Based on our analysis, we recommend that Telco:

1. **Improve Technical Support**: Give more attention to enhancing technical support services.
2. **Enhance Fiber Optic Service**: Invest in improving the quality and reliability of fiber optic service.
3. **Target Marketing Strategies**:
   - Focus on customers with short-term contracts, encouraging them to move to longer contracts
   - Target customers without online services, offering these services at attractive rates
   - Create specific strategies for single customers, as their churn rate is higher than those with partners and dependents
4. **Simplify Payment Methods**: Guide customers towards simple paying methods like paper billing and credit card.

## Requirements

```
pandas>=1.0.0
numpy>=1.18.0
scikit-learn>=0.22.0
matplotlib>=3.1.0
seaborn>=0.10.0
xgboost>=1.0.0
imbalanced-learn>=0.6.0
optuna>=2.0.0
```

## Installation & Usage

1. Clone this repository:
```bash
git clone https://github.com/Ziad-Henedy2/Telecom-Customer-Churn-Prediction
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Run the analysis:
```bash
jupyter notebook Telecom_Customer_Churn_Analysis.ipynb
```

---

**Project by Team Abdelghafor's Hackathon**
