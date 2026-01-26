# 🚢 Task 7: Titanic Survival Prediction (Logistic Regression)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-green?style=for-the-badge&logo=pandas)

## 📌 Project Overview
This project implements a **Logistic Regression** model to predict the survival of passengers on the Titanic. The goal was to build a complete Machine Learning pipeline that handles missing data, encodes categorical variables, and evaluates performance using industry-standard metrics.

## 📂 Dataset Details
* **Source:** Seaborn Built-in Dataset (`titanic`)
* **Rows:** 891 Passengers
* **Target:** `survived` (0 = Deceased, 1 = Survived)
* **Key Features:**
    * `pclass`: Passenger Class (1st, 2nd, 3rd)
    * `sex`: Gender
    * `age`: Age in years
    * `fare`: Ticket price
    * `embarked`: Port of Embarkation (C = Cherbourg, Q = Queenstown, S = Southampton)

## ⚙️ The Preprocessing Pipeline
To ensure robust model training, I constructed a **Scikit-Learn Pipeline** consisting of two parallel branches:

1.  **Numeric Pipeline (Age, Fare, SibSp, Parch):**
    * **Imputation:** Missing values in 'Age' were filled with the **Median** to avoid skewing the data with outliers.
    * **Scaling:** Applied `StandardScaler` to normalize the range of values (Crucial for Logistic Regression convergence).
2.  **Categorical Pipeline (Sex, Embarked, Pclass):**
    * **Imputation:** Missing 'Embarked' values were filled with the **Mode** (Most Frequent).
    * **Encoding:** Applied `OneHotEncoder` to convert text labels into binary vectors.

## 📊 Evaluation Dashboard
The script generates a 3-panel dashboard to visualize model performance:

### 1. Confusion Matrix
* Shows the exact count of True Positives (Correctly Predicted Survivors) vs. False Negatives (Survivors we missed).
* **Result:** The model achieves ~80% accuracy, balancing sensitivity and specificity well.

### 2. ROC Curve & AUC
* **AUC Score:** ~0.86
* **Interpretation:** An AUC of 0.86 indicates the model has a strong ability to distinguish between survivors and non-survivors. The curve hugs the top-left corner, which is the ideal shape.

### 3. Feature Importance (Coefficients)
This chart reveals *what* drove the predictions:
* **Positive Predictors (Green):**
    * `sex_female`: The strongest predictor of survival.
    * `pclass_1`: First-class status significantly increased survival odds.
* **Negative Predictors (Red):**
    * `sex_male`: Being male drastically reduced the probability of survival.
    * `pclass_3`: Third-class passengers had the lowest survival probability.

## 🚀 How to Run
1.  Open the script in Google Colab (or any Jupyter environment).
2.  Run the code.
3.  The dataset will load automatically via Seaborn (no file uploads required).

---
