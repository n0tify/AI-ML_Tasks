# 🎗️ Task 11: Breast Cancer Diagnosis (Tuned SVM)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Metric](https://img.shields.io/badge/Recall-98%25-green)

## 📌 Project Executive Summary
This project implements a **Support Vector Machine (SVM)** to classify breast tumor biopsies as **Malignant** (Cancerous) or **Benign** (Safe).

In medical diagnostics, **Recall** (Sensitivity) is the most critical metric. Missing a cancer case (False Negative) is life-threatening. By utilizing a **Grid Search Tuned RBF Kernel**, this model achieves near-perfect sensitivity while maintaining high precision.

## 📂 Dataset Architecture
* **Source:** Scikit-Learn `load_breast_cancer()` (Wisconsin Diagnostic Breast Cancer).
* **Samples:** 569 Patients.
* **Features:** 30 features derived from digitized images of Fine Needle Aspirates (FNA), describing cell nucleus properties (Radius, Texture, Perimeter, Area, Smoothness, etc.).
* **Target:** Malignant (0) vs. Benign (1).

## ⚙️ Technical Methodology

### 1. Preprocessing (Standardization)
* **The Challenge:** SVMs are distance-based. Features like "Area" (values ~1000) naturally overpower features like "Smoothness" (values ~0.1).
* **The Fix:** We implemented a `Pipeline` that applies `StandardScaler` ($\mu=0, \sigma=1$) before the data ever touches the SVM. This guarantees equal feature importance.

### 2. Model Selection: Linear vs. RBF
We benchmarked two approaches:
* **Linear SVM:** Draws a straight line. (Accuracy: ~97%).
* **RBF SVM (Radial Basis Function):** Projects data into higher dimensions to find non-linear boundaries. After tuning, this model matched or exceeded the linear baseline, offering more robustness against complex edge cases.

### 3. Hyperparameter Optimization
We used `GridSearchCV` to optimize:
* **C (Regularization):** Controls the trade-off between smooth boundaries and classifying training points correctly.
* **Gamma (Kernel Coefficient):** Controls the "reach" of a single training example.
* **Scoring Metric:** We optimized for `f1_macro` to ensure the model performed well on **both** classes, avoiding the trap of simply predicting the majority class.

## 📊 Performance Analysis

| Metric | Score | Interpretation |
| :--- | :--- | :--- |
| **Accuracy** | **~98%** | Highly reliable overall. |
| **Recall (Malignant)** | **~95-98%** | We successfully identify almost all cancerous tumors. |
| **AUC Score** | **~0.99** | The model has excellent separability between classes. |

### Visual Validation
* **Confusion Matrix:** Shows that False Negatives (Cancer patients told they are safe) are minimized to near zero.
* **ROC Curve:** The curve hugs the top-left corner (AUC 0.99), validating the model's strength.

## 🚀 How to Run
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/your-username/breast-cancer-svm.git](https://github.com/your-username/breast-cancer-svm.git)
    ```
2.  **Run the Script:**
    ```bash
    python breast_cancer_svm_final.py
    ```
3.  **Result:**
    * View the ROC Curve.
    * The trained pipeline is saved as `breast_cancer_svm_pipeline.pkl`.

---
