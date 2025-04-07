# Telecom Customer Churn Prediction

![Churn Prediction](https://img.shields.io/badge/Type-Classification-blue) 
![Python](https://img.shields.io/badge/Python-3.7%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)

A machine learning project to predict customer churn for a telecom company.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Project Overview
This project aims to predict which customers are likely to churn (leave the service) for a telecom company. By identifying at-risk customers, the company can implement targeted retention strategies.

## Dataset
The dataset contains information about:
- 7,043 customers
- 20 features including:
  - Demographic info (gender, senior citizen status, partner/dependents)
  - Services info (phone, internet, online security, etc.)
  - Account info (tenure, contract type, payment method)
  - Charges (monthly and total)
  - Churn status (target variable)

## Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/telecom-churn-prediction.git
    cd telecom-churn-prediction
    ```

2. Install required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Usage
Run the Jupyter notebook:
    ```bash
    jupyter notebook hackathon-project.ipynb
    ```

## Methodology
### Data Preprocessing:
- Handling missing values
- Feature engineering
- Encoding categorical variables

### Exploratory Data Analysis:
- Univariate and bivariate analysis
- Correlation analysis

### Model Building:
- Logistic Regression
- Decision Trees
- Random Forest
- XGBoost
- Ensemble methods

### Evaluation:
- Accuracy, precision, recall, F1-score
- Confusion matrices
- Feature importance

## Results
### Key findings:
- The best performing model achieved XX% accuracy
- Top factors influencing churn:
  - Contract type (month-to-month customers more likely to churn)
  - Internet service type
  - Tenure length

## Contributing
Contributions are welcome! Please open an issue or submit a pull request.

## License
This project is licensed under the MIT License.
