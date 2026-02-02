#  Predictive Maintenance: CNC Machine Failure Detection

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Library-Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Seaborn](https://img.shields.io/badge/Library-Seaborn-7798B7?style=for-the-badge&logo=seaborn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Library-Matplotlib-11557c?style=for-the-badge&logo=matplotlib&logoColor=white)
![Imbalanced-Learn](https://img.shields.io/badge/Library-Imbalanced_Learn-yellow?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

##  Project Overview
This project focuses on **Predictive Maintenance** for CNC machines using a dataset of 10,000 records. The goal is to predict machine failures *before* they happen by analyzing sensor data (Temperature, Torque, Rotational Speed, etc.).

Moving from "Reactive Maintenance" to allows factories to reduce downtime and save costs.

---

###  Methodology & Techniques
1.  **Handling Multicollinearity:**
    * Detected a high correlation (**0.88**) between `Air_Temp` and `Process_Temp`.
    * Removed `Air_Temp` to reduce redundancy and improve model stability.
2.  **Data Preprocessing:**
    * Used `StandardScaler` to normalize features with different units (e.g., RPM vs. Torque).
3.  **Handling Imbalanced Data (Crucial Step):**
    * The dataset was highly imbalanced (**96% Normal** vs. **4% Failure**).
    * Initial models failed to detect failures (Recall was ~30%).
    * Applied **SMOTE (Synthetic Minority Over-sampling Technique)** to balance the classes. This significantly improved the model's ability to learn failure patterns.
4.  **Evaluation Metrics:**
    * Evaluated models using **Accuracy**, **Recall (Sensitivity)**, and **F1-Score** to ensure a balanced performance.

---

###  Model Results
The **Random Forest Classifier** achieved the best overall performance.

| Model | Accuracy | Recall (Failure Detection) | F1-Score (Class 1) | Verdict |
| :--- | :--- | :--- | :--- | :--- |
| **Logistic Regression (Base)** | 97.4% | ~30% | Low |  Missed most failures |
| **Logistic Regression (SMOTE)** | 80.0% | 79% | Moderate |  Good detection, lower precision |
| **Decision Tree** | 93.8% | High | Moderate |  Prone to overfitting |
| **Random Forest (Final)** | **94.2%** | **High & Stable** | **Balanced** |  **Best Model** |

---

###  Visual Analysis

#### 1. Confusion Matrix (Random Forest)
The model successfully identifies the majority of machine failures while keeping false alarms low.

![Confusion Matrix](...)

#### 2. Feature Importance
According to the Random Forest analysis, **Torque** and **Rotational Speed** are the most critical indicators of a potential failure.

![Feature Importance](...)

---
---
