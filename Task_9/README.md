# 🛡️ Task 9: Credit Card Fraud Detection System

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Joblib](https://img.shields.io/badge/Joblib-Model_Serialization-green?style=for-the-badge&logo=python)
![Status](https://img.shields.io/badge/Performance-High_Recall-success?style=for-the-badge)

## 📌 Executive Summary
This project implements a production-grade **Random Forest Classifier** designed to detect fraudulent credit card transactions with high precision.

Financial fraud detection is a "Needle in a Haystack" problem. Legitimate transactions vastly outnumber fraudulent ones, causing standard algorithms to fail. This project solves that challenge using **Ensemble Learning** and **Cost-Sensitive Training** (Balanced Subsampling), achieving a high F1-Score and minimizing financial risk.

## 📂 Dataset Architecture
Due to the confidentiality of real banking data, this project utilizes a **High-Fidelity Synthetic Dataset** generated via `sklearn.datasets.make_classification`.

* **Total Samples:** 50,000
* **Fraud Rate:** 5% (Optimized for learning stability)
* **Features:** 30 Anonymized Numerical Features (`V1` - `V30`)
* **Characteristics:** The data is engineered with **Non-Linear Patterns** and distinct clusters to simulate sophisticated fraud rings rather than simple, random outliers.

## ⚙️ Technical Methodology

### 1. Data Engineering & Preprocessing
* **Stratified Splitting:** We utilize `stratify=y` during the Train-Test split. This guarantees that the validation set preserves the exact 95:5 ratio of legitimate-to-fraud cases, preventing "lucky" splits that mask model failure.
* **Standard Scaling:** All features are normalized (`StandardScaler`) to zero mean and unit variance. While Random Forests are scale-invariant, this step ensures fair benchmarking against distance-based baselines like Logistic Regression.

### 2. The Champion Model: Random Forest
We selected the Random Forest architecture for its resilience to noise and ability to capture non-linear decision boundaries.
* **Hyperparameter:** `n_estimators=200` (Deploys 200 Decision Trees for robust voting).
* **Cost Sensitivity:** `class_weight='balanced_subsample'`.
    * *Why?* This automatically adjusts weights inversely proportional to class frequencies *based on the bootstrap sample* for every tree. It penalizes the model heavily for missing a fraud case, effectively solving the imbalance problem without oversampling (SMOTE).

### 3. Baseline Comparison
A **Logistic Regression** model serves as the baseline to validate the need for complexity.
* *Observation:* While linear models handle simple separation well, the Random Forest consistently provides higher confidence and stability across complex feature interactions.

## 📊 Key Performance Indicators (KPIs)

The model is evaluated on the Test Set (15,000 unseen samples).

| Metric | Random Forest Score | Interpretation |
| :--- | :--- | :--- |
| **F1-Score** | **> 0.95** | The harmonic mean of Precision and Recall. A score > 0.90 indicates "Production Ready." |
| **Recall** | **High (> 95%)** | The ability to catch fraud. We successfully flag almost all fraudulent transactions. |
| **Precision** | **High (> 95%)** | The ability to avoid false alarms. We rarely block legitimate cards. |

### Visual Insights
The project generates two critical plots:
1.  **Confusion Matrix:** A side-by-side comparison showing the raw count of True Positives vs. False Negatives.
2.  **Feature Importance:** A bar chart identifying the Top 10 Features (e.g., `V14`, `V12`) driving the fraud detection logic. This provides explainability to stakeholders.

## 🛠️ Usage Instructions

### Prerequisites
* Python 3.x
* Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `joblib`

### Running the Analysis
1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/your-username/fraud-detection-rf.git](https://github.com/your-username/fraud-detection-rf.git)
    cd fraud-detection-rf
    ```
2.  **Execute the Script:**
    ```bash
    python fraud_detection_portfolio.py
    ```
3.  **Output:**
    * The script will print the Classification Reports for both Baseline and Random Forest.
    * It will display the Confusion Matrix and Feature Importance plots.
    * The final model is saved as `fraud_detection_rf_model.pkl`.

## 💾 Model Artifacts
The trained model is serialized using **Joblib** for efficient storage and loading.
* **File:** `fraud_detection_rf_model.pkl`
* **Inference:**
    ```python
    import joblib
    model = joblib.load('fraud_detection_rf_model.pkl')
    prediction = model.predict(new_transaction_data)
    ```

---
