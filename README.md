🏦 Fraud Detection Using Machine Learning
📌 Project Overview
This project builds an end-to-end fraud detection pipeline using real-world transactional datasets. The goal is to identify fraudulent transactions accurately while addressing challenges such as class imbalance, feature engineering, and model interpretability.

Two datasets are used:

Fraud_Data.csv – E-commerce transaction data
creditcard.csv – Credit card transaction data (highly imbalanced)
The project progresses through:

Data cleaning & preprocessing
Exploratory Data Analysis (EDA)
Feature engineering
Model training & evaluation (Task 2 completed)
Model explainability using SHAP (Task 3 completed)
📂 Project Structure
fraud-detection/
├── .github/
│   └── workflows/
│       └── unittests.yml
├── data/                           # Ignored from GitHub
│   ├── raw/                        # Original datasets
│   └── processed/                  # Cleaned & feature-engineered data
├── notebooks/
│   ├── eda-fraud-data.ipynb
│   ├── eda-creditcard.ipynb
│   ├── feature-engineering.ipynb
│   ├── modeling.ipynb              # ✅ Task 2: Model training & evaluation
│   ├── shap-explainability.ipynb   # ✅ Task 3: SHAP analysis
│   └── README.md
├── models/
│   └── random_forest_task3.pkl     # Saved trained model
├── src/
│   └── __init__.py
├── tests/
│   └── __init__.py
├── scripts/
│   └── README.md
├── requirements.txt
├── README.md
└── .gitignore
🧹 Data Cleaning & Preprocessing
Removed duplicate records
Fixed inconsistent data types
Handled missing values using appropriate imputation strategies
Converted IP addresses to integer format
Merged Fraud_Data.csv with IpAddress_to_Country.csv using range-based IP lookup
⚙️ Feature Engineering
Engineered Features
Time-based features

hour_of_day
day_of_week
time_since_signup (purchase_time − signup_time)
Behavioral features

transactions_per_user
IP-based features

ip_address
lower_bound_ip_address
upper_bound_ip_address
Categorical Encoding

One-Hot Encoding for browser, source, sex, country
Scaling

StandardScaler applied to numerical features (when required)
📊 Exploratory Data Analysis (EDA) Highlights
Fraud is more likely to occur:

Shortly after user signup
From specific IP ranges
During unusual hours and days
High-frequency user behavior can signal suspicious activity

Severe class imbalance observed across datasets

⚖️ Class Imbalance Handling
Fraud class represents a very small fraction of total transactions
Applied SMOTE on training data only
Maintained original distribution in test set for realistic evaluation
🤖 Modeling & Evaluation (✅ Task 2 Completed)
Models Trained
Logistic Regression (baseline)
Random Forest Classifier (final model)
Evaluation Metrics
F1-Score
Precision-Recall AUC
Confusion Matrix
Classification Report
Final Model Performance (Random Forest)
Strong fraud detection capability
Balanced trade-off between false positives and false negatives
Selected due to superior performance and robustness
The trained model is saved in:

models/random_forest_task3.pkl
🔍 Model Explainability (Task 3)
Used SHAP (SHapley Additive exPlanations) for interpretability

Generated:

Global feature importance plots
Local explanations for individual predictions
Identified top fraud drivers:

time_since_signup
ip_address
IP range features
Temporal patterns (day_of_week, hour_of_day)
📈 Key Insights
Fraud often occurs immediately after signup
IP address patterns are strong fraud indicators
Temporal behavior significantly influences fraud likelihood
Model decisions are interpretable and aligned with business logic
💡 Business Recommendations
Additional verification for new accounts

Transactions within the first hour after signup should trigger review
IP-based risk scoring

Monitor and flag suspicious IP ranges
Time-based monitoring

Increase scrutiny during unusual hours or days
🛠️ Environment Setup
pip install -r requirements.txt
✅ Submission Note (Interim & Task 2)
This repository demonstrates:

Completed data preprocessing & EDA (Interim-1)
Successful model training and evaluation (Task 2)
Model explainability with SHAP (Task 3)
