# 🌳 Task 8: Bank Marketing Prediction (Decision Tree Analysis)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![OpenML](https://img.shields.io/badge/Data_Source-OpenML-purple?style=for-the-badge&logo=openml)
![Status](https://img.shields.io/badge/Status-Complete-success)

## 📌 Project Executive Summary
This project leverages **Machine Learning** to solve a classic banking problem: **Predicting whether a customer will subscribe to a Term Deposit.**

Using the **UCI Bank Marketing Dataset**, we trained an interpretable **Decision Tree Classifier**. The goal was not just to predict outcomes, but to generate clear, actionable **Business Rules** that marketing managers can use to optimize their call center strategies.

## 📂 Dataset Overview
* **Source:** UCI Machine Learning Repository (Fetched via OpenML ID 1461).
* **Size:** ~45,000 Records.
* **Target Variable:** `deposit` (Binary: 0 = No, 1 = Yes).

### Key Features (Data Dictionary)
| Feature | Description |
| :--- | :--- |
| `duration` | Length of the last phone call (in seconds). |
| `poutcome` | Outcome of the previous marketing campaign (success/failure). |
| `balance` | Average yearly balance in euros. |
| `housing` | Has housing loan? (yes/no). |
| `month` | Last contact month of year. |

## ⚙️ Methodology & Technical Approach

### 1. Data Loading & Cleaning
* **Challenge:** The raw OpenML data uses obfuscated column names (`V1`, `V2`, etc.).
* **Solution:** Implemented a robust mapping pipeline to rename columns to their business equivalents (`Age`, `Job`, `Duration`), ensuring the final visualization is human-readable.

### 2. Feature Engineering
* **Categorical Encoding:** Applied `OneHotEncoder` to features like `Job` and `Marital Status` to convert them into a machine-readable binary format.
* **Stratification:** Used `stratify=y` during the Train-Test split to maintain the ratio of subscribers/non-subscribers.

### 3. Model Architecture (The "White Box")
* **Algorithm:** Decision Tree Classifier (Gini Impurity).
* **Depth Limit (`max_depth=4`):** Strictly enforced to prevent the "Spaghetti Tree" effect. This ensures the logic remains simple enough for humans to verify.
* **Class Weighting (`balanced`):** * *Problem:* Only ~11% of customers subscribe. A standard model ignores them to maximize accuracy.
    * *Fix:* We heavily penalized the model for missing a subscriber. This sacrificed some overall accuracy to drastically improve **Recall** (Sensitivity).

## 📊 Performance Analysis

### Metrics that Matter
| Metric | Score | Interpretation |
| :--- | :--- | :--- |
| **Accuracy** | ~77% | Overall correctness. (Lower than baseline due to aggressive Recall strategy). |
| **Recall (Class 1)** | **~79%** | We successfully identify **8 out of 10** potential subscribers. |
| **Precision (Class 0)** | **97%** | We rarely waste time calling someone who is definitely not interested. |

### Visual Confusion Matrix
The confusion matrix heatmap confirms our strategy:
* **True Positives (Subscribers Found):** High Count.
* **False Negatives (Subscribers Missed):** Low Count.

## 🧠 Business Insights (The Rules)
The Decision Tree revealed three "Golden Rules" for the marketing team:

### 1. The "Engagement" Rule
> **IF** `Duration` > 250 seconds (4 mins) **THEN** Probability of Subscription > 60%.
> * **Action:** If a customer stays on the line past the 4-minute mark, the agent should aggressively close the deal.

### 2. The "Housing Burden" Rule
> **IF** `Duration` < 250s **AND** `Housing Loan` = Yes **THEN** Probability of Subscription < 5%.
> * **Action:** Short calls with customers who have debt (housing loans) are low-value leads. Do not chase them.

### 3. The "Momentum" Rule
> **IF** `Previous Outcome` = Success **THEN** Probability of Subscription is High.
> * **Action:** Prioritize calling customers who have purchased from the bank in the past. They are the "Low Hanging Fruit."

## 🚀 How to Reproduce
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/your-username/bank-marketing-tree.git](https://github.com/your-username/bank-marketing-tree.git)
    ```
2.  **Run the Script:**
    * Open `bank_marketing_elite.py` in Google Colab or Jupyter.
    * Run all cells. (No manual data download required).

---
