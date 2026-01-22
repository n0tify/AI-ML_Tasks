# Task 4
# 🛠️ Feature Engineering & Preprocessing Pipeline

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?style=for-the-badge&logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)

## 📌 Project Overview
This repository contains a robust feature engineering pipeline designed for the **Adult Income Dataset**. The goal of this project is to transform raw, messy demographic data into a clean, numerical format optimized for Machine Learning algorithms (such as Logistic Regression, SVM, or Neural Networks).

**Key Objectives:**
1.  Handle missing data and inconsistencies.
2.  Transform categorical text data into machine-readable numerical formats.
3.  Normalize feature scales to ensure model stability and faster convergence.

---

## 📊 The Dataset
**Source:** [UCI Machine Learning Repository - Adult Dataset](https://archive.ics.uci.edu/ml/datasets/adult)  
**Task:** Binary Classification (Predict if income > $50K/yr)  
**Original Features:** 14 (Mixed Categorical & Numerical)  

---

## ⚙️ Methodology & Implementation

### 1. Data Cleaning
* **Missing Values:** The raw dataset contains `?` characters representing missing data. These were parsed as `NaN` and rows containing them were dropped to maintain dataset integrity.
* **Whitespace Handling:** Removed leading/trailing whitespace from string columns to prevent category duplication (e.g., `" Male"` vs `"Male"`).

### 2. Feature Encoding Strategy
Machine Learning models require numerical input. We applied two distinct strategies:

* **Label Encoding:** * *Target:* `income` (`<=50K`, `>50K`) → `0`, `1`
    * *Binary Features:* `sex` (`Male`, `Female`) → `1`, `0`
    * *Why?* Efficient for binary targets where preserving hierarchy isn't an issue.

* **One-Hot Encoding:**
    * *Target:* `workclass`, `occupation`, `race`, `native-country`
    * *Technique:* Used `pd.get_dummies` with `drop_first=True`.
    * *Why?* These features are **nominal** (no intrinsic order). Assigning them numbers (1, 2, 3) would introduce a false hierarchy. One-Hot Encoding prevents the model from assuming that `Sales (3)` is "greater than" `Admin (1)`.

### 3. Feature Scaling (StandardScaler)
* **Algorithm:** Z-Score Normalization (`sklearn.preprocessing.StandardScaler`)
* **Formula:** $z = \frac{x - \mu}{\sigma}$
* **Impact:** * Transforms all numerical features (`age`, `capital-gain`, etc.) to have a **Mean of 0** and **Standard Deviation of 1**.
    * **Crucial for:** Distance-based algorithms (KNN, SVM) and Gradient Descent-based algorithms (Linear Regression, Neural Networks), preventing features with large magnitudes (like `capital-gain`) from dominating the loss function.

---

## 📈 Visual Results
The pipeline generates visualization comparing the data distribution **Before** and **After** scaling.

| State | Observation |
| :--- | :--- |
| **Before Scaling** | `Age` ranges from 17-90, while `Capital-Gain` ranges from 0-99,999. This variance creates bias in ML models. |
| **After Scaling** | All features are centered around 0. The shape of the distribution is preserved, but the scale is normalized. |

---

## 🚀 How to Run
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/your-username/feature-engineering-task.git](https://github.com/your-username/feature-engineering-task.git)
    ```
2.  **Install Requirements:**
    ```bash
    pip install pandas numpy seaborn scikit-learn matplotlib
    ```
3.  **Execute the Pipeline:**
    ```bash
    python feature_engineering_advanced.py
    ```
4.  **Output:** * Processed file saved as: `adult_income_processed_advanced.csv`

---

