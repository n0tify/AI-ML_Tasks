# 🏆 Task 14: Automated Model Selection Framework

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Joblib](https://img.shields.io/badge/Joblib-Deployment-green?style=for-the-badge)

## 📌 Project Executive Summary
This project represents the culmination of the Machine Learning Internship. It establishes a **Benchmarking Framework** to scientifically compare multiple algorithms and select the best one for production.

Using the **Breast Cancer Diagnostic Dataset**, we automated the training of five distinct models. The framework evaluates them not just on accuracy, but on **Overfitting (Train vs Test Gap)**, **Recall (Sensitivity)**, and **Inference Time**.

## 📂 Benchmarked Algorithms
1.  **Logistic Regression:** Baseline linear classifier.
2.  **Decision Tree:** Non-linear rule-based model.
3.  **Random Forest:** Ensemble bagging method.
4.  **Support Vector Machine (SVM):** Margin-based classifier (Linear Kernel).
5.  **K-Nearest Neighbors (KNN):** Distance-based instance learning.

## ⚙️ Methodology

### 1. Unified Pipeline
To ensure a fair comparison, all models shared the exact same environment:
* **Stratified Split:** 80/20 train-test ratio, preserving class balance.
* **Standard Scaling:** Applied universally to support distance-based models (KNN, SVM).

### 2. The "Overfitting" Watchdog
We implemented logic to detect overfitting automatically:
* If `Train Accuracy` > `Test Accuracy` by more than 5%, the model is flagged as **"Overfitting"**.
* *Result:* The Decision Tree achieved 100% Training Accuracy but dropped to ~91% Test Accuracy, triggering the flag.

### 3. Metric Selection Strategy
Since this is a medical diagnosis problem, we prioritized **Recall**:
* **Recall:** The ability to find all cancer cases.
* **Result:** Logistic Regression achieved the highest Recall (~98.6%), making it the safest choice for patients.

## 📊 Final Leaderboard

| Model | Test Accuracy | Recall | Status |
| :--- | :--- | :--- | :--- |
| **Logistic Regression** | **98.25%** | **98.61%** | **🏆 Winner** |
| SVM (Linear) | 97.37% | 97.22% | Runner Up |
| Random Forest | 95.61% | 97.22% | Good Fit |
| KNN (k=5) | 95.61% | 97.22% | Good Fit |
| Decision Tree | 91.23% | 90.28% | **Overfitting** |

### Visual Insights
* **Bar Chart:** 

[Image of model comparison chart]
 A visual ranking of all models based on Test Accuracy.
* **Comparison Table:** A comprehensive DataFrame tracking Training Time, F1-Score, and Overfitting Status.

## 💾 Model Artifacts
* **File:** `best_model_pipeline.pkl`
* **Contents:** The winning **Logistic Regression** model + the fitted `StandardScaler`, serialized for immediate deployment.

## 🚀 How to Run
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/your-username/model-comparison-framework.git](https://github.com/your-username/model-comparison-framework.git)
    ```
2.  **Run the Script:**
    ```bash
    python model_comparison_final.py
    ```
3.  **Output:**
    * The script prints the full leaderboard.
    * It saves the best model automatically.

---
