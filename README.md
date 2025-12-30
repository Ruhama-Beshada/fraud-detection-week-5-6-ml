🛡️ Fraud Detection with Explainable Machine Learning
A production-oriented, end-to-end fraud detection system using machine learning, class-imbalance handling, and explainable AI (SHAP). This project emphasizes robust modeling, interpretability, and reproducibility through modular code design and professional Git workflows.

📌 Project Overview
Online transaction fraud is rare, evolving, and costly. This project builds and evaluates machine learning models to detect fraudulent transactions while ensuring:

Explicit handling of extreme class imbalance
Transparent, interpretable predictions using SHAP
Modular, reproducible code organization
Clear separation of data, features, models, and explanations
Two real-world datasets are used:

E-commerce fraud transactions (Fraud_Data.csv)
Credit card transactions (creditcard.csv)
🧠 Key Contributions
✔ Feature engineering grounded in behavioral fraud signals ✔ Explicit SMOTE-based resampling applied correctly to training data ✔ Comparative modeling with Logistic Regression & Random Forest ✔ Global + local explainability with SHAP summary and force plots ✔ Professional Git workflow (branches + PRs) ✔ Fully reproducible environment and modular pipeline

🗂️ Repository Structure
fraud-detection/
│
├── data/                         # (Gitignored)
│   ├── raw/                      # Original datasets
│   └── processed/                # Cleaned & feature-engineered data
│
├── notebooks/                    # Analysis & experimentation
│   ├── eda_fraud_data.ipynb
│   ├── eda_creditcard.ipynb
│   ├── feature_engineering.ipynb
│   ├── modeling.ipynb
│   └── shap_explainability.ipynb
│
├── src/                          # Modular pipeline scripts
│   ├── data_preprocessing.py
│   ├── feature_engineering.py
│   ├── resampling.py             # Explicit imbalance handling
│   ├── train_model.py
│   ├── evaluate_model.py
│   └── explain_model.py
│
├── models/                       # Saved trained models
├── reports/                      # PDF / blog-style report
├── tests/                        # Unit tests
│
├── requirements.txt
├── README.md
└── .gitignore
⚙️ Environment Setup
git clone https://github.com/your-username/fraud-detection.git
cd fraud-detection
pip install -r requirements.txt
Python Version: 3.9+ All dependencies are explicitly pinned for reproducibility.

🧹 Data Preprocessing
Removed duplicates and validated data integrity
Corrected data types (timestamps, numeric, categorical)
Converted IP addresses to integers for geolocation mapping
Merged transactions with IpAddress_to_Country.csv using range-based joins
📌 All preprocessing logic is implemented in:

src/data_preprocessing.py
🧪 Feature Engineering
Behavior-driven features were created to capture fraud patterns:

Feature	Purpose
time_since_signup	Detect rapid fraud attempts
hour_of_day	Identify abnormal transaction timing
day_of_week	Capture weekly patterns
transactions_per_user	Velocity-based fraud detection
IP range features	Geographic risk estimation
Categorical variables are one-hot encoded, and numerical features are standardized.

⚖️ Class Imbalance Handling (Explicitly Demonstrated)
Fraud cases represent <1% of transactions, requiring careful handling.

✔ SMOTE is applied only to training data ✔ Test data remains untouched to preserve real-world distribution ✔ Pre- and post-resampling class distributions are visualized and documented

Implementation:

src/resampling.py
🤖 Modeling & Evaluation
Two models were trained and compared:

Model	Precision	Recall	F1-score	PR-AUC
Logistic Regression	Baseline	Moderate	Moderate	Low
Random Forest	High	High	Best	Best
📌 Evaluation focuses on Recall, F1-score, and PR-AUC, not accuracy.

🔍 Explainability with SHAP (Fully Demonstrated)
Explainability is treated as a core requirement, not an add-on.

Global Explainability
SHAP summary plots identify dominant fraud drivers
Results align with domain intuition (IP risk, timing, velocity)
Local Explainability
SHAP force plots for individual transactions

True Positive (correct fraud detection)
False Negative (missed fraud)
These visualizations clearly show why the model made each decision.

📌 Implemented in:

src/explain_model.py
📈 Key Fraud Drivers Identified
time_since_signup
ip_address and IP range bounds
hour_of_day
transactions_per_user
purchase_value
These insights directly inform business rules and monitoring strategies.

💼 Business Recommendations
Flag transactions occurring minutes after signup
Apply risk scoring to high-risk IP ranges
Increase scrutiny during off-hour transactions
Combine ML predictions with rule-based alerts
🔁 Git & Development Workflow
This repository follows professional Git practices:

Feature development on dedicated branches
Pull Requests (PRs) for merging changes
Modular scripts instead of monolithic notebooks
Clear separation of experimentation and production logic
📌 Limitations & Future Improvements
Incorporate anomaly detection for rare fraud patterns
Add real-time scoring pipeline
Implement drift detection and retraining strategy
Expand ensemble modeling
📄 Final Report
A full PDF / blog-style report is available in:

reports/final_report.pdf
It includes:

Visual EDA evidence
Model performance comparison
SHAP plots with interpretation
Business impact discussion
🏆 Why This Project Is Strong
✔ Explicit class imbalance handling ✔ Fully demonstrated SHAP explainability ✔ Modular, production-oriented code ✔ Reproducible environment ✔ Clear academic and business value
