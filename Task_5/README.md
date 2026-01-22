# 🩺 Task 5: Heart Disease Prediction & Model Evaluation

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-green?style=for-the-badge&logo=pandas)

## 📌 Project Overview
This project focuses on the **Evaluation Phase** of the Machine Learning lifecycle. Using the **UCI Heart Disease Dataset**, I trained a Logistic Regression model to predict whether a patient has heart disease.

The core objective was not just to train a model, but to strictly evaluate its performance using advanced metrics (Precision, Recall, F1-Score) and visualizations (ROC Curve, Confusion Matrix, Feature Importance).

## 📂 The Dataset
* **Source:** [UCI Machine Learning Repository - Cleveland Heart Disease Data](https://archive.ics.uci.edu/ml/datasets/heart+disease)
* **Samples:** 303 Patients
* **Features:** 13 Clinical Attributes (Age, Sex, Cholesterol, Max Heart Rate, etc.)
* **Target:** Binary Classification (0 = Healthy, 1 = Presence of Heart Disease)

## ⚙️ Methodology

### 1. Preprocessing Pipeline
* **Cleaning:** Rows with missing values (`?`) were dropped to ensure data integrity.
* **Train-Test Split:** The data was split **80/20** using `stratify=y`.
    * *Why Stratify?* This ensures that both the training and testing sets have the exact same ratio of sick-to-healthy patients, preventing bias.
* **Scaling:** A `StandardScaler` was used within a `make_pipeline`.
    * *Why Pipeline?* This prevents **Data Leakage** by fitting the scaler *only* on the training data and then transforming the test data.

### 2. Model Selection
* **Algorithm:** Logistic Regression
* **Reasoning:** Chosen for its interpretability. In medical fields, it is crucial to understand *why* a model makes a prediction (e.g., "High Cholesterol increases risk by X%").

## 📊 Evaluation Results & Visualizations

The script generates three key visualizations to assess model performance:

### 📉 1. Confusion Matrix
* **Purpose:** breaks down predictions into True Positives, True Negatives, False Positives, and False Negatives.
* **Insight:** Helps us analyze the cost of errors. In healthcare, False Negatives (telling a sick patient they are healthy) are the most dangerous error type.

### 📈 2. ROC Curve & AUC
* **Purpose:** Plots the True Positive Rate against the False Positive Rate at different classification thresholds.
* **Insight:** The **AUC (Area Under Curve)** represents the model's overall ability to distinguish between classes. An AUC score closer to 1.0 indicates excellent performance.

### 🧠 3. Feature Importance
* **Purpose:** Extracts the coefficients from the Logistic Regression model.
* **Insight:**
    * **Red Bars (Positive Coefficients):** Risk Factors (e.g., `ca` - Number of vessels colored by flourosopy, `thal` - Thalassemia).
    * **Blue Bars (Negative Coefficients):** Protective Factors (e.g., Higher `thalach` - Max Heart Rate).

## 📝 Key Metrics Explained
The script outputs the following metrics to the console:

| Metric | Formula | Interpretation |
| :--- | :--- | :--- |
| **Accuracy** | $(TP + TN) / Total$ | How often is the model correct overall? |
| **Precision** | $TP / (TP + FP)$ | Of all patients predicted to have disease, how many actually did? |
| **Recall** | $TP / (TP + FN)$ | Of all patients who actually had disease, how many did we catch? |
| **F1 Score** | $2 * (P * R) / (P + R)$ | The harmonic mean of Precision and Recall. Essential for imbalanced datasets. |

## 🚀 How to Run
1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
    ```
2.  **Install Dependencies:**
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn
    ```
3.  **Run the Script:**
    ```bash
    python model_evaluation_final.py
    ```

---
