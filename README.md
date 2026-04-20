# ISYE-6704-Course-Project-Predicting-30-Day-Hospital-Readmissions-Using-the-UCI-Diabetes-Dataset
# Predicting 30-Day Hospital Readmissions (Diabetes Patients)

## Overview

Hospital readmissions within 30 days are a major cost and quality concern in healthcare.
This project analyzes patient-level hospital data to identify key factors associated with readmission risk and evaluate predictive modeling approaches.

The goal is **not just prediction**, but understanding *why* patients are readmitted.

---

## Dataset

* Source: UCI Machine Learning Repository
* Dataset: *Diabetes 130-US Hospitals (1999–2008)*
* ~100,000 patient encounters
* ~50 features including:

  * Demographics (age, race, gender)
  * Hospital utilization (inpatient, emergency visits)
  * Diagnoses and comorbidities
  * Admission and discharge details

Challenge: Only ~9% of cases are readmissions → **high class imbalance**

---

## Approach

### 1. Data Preparation

* Removed high-missing and redundant variables
* Encoded categorical features
* Engineered **Charlson Comorbidity Index (CCI)** from diagnosis codes
* Reduced dimensionality via feature selection

---

### 2. Models

#### Logistic Regression (Baseline)

* Focus on interpretability
* Used statistical feature selection (Wald tests)
* Applied class weighting to address imbalance

#### Random Forest

* Ensemble method for improved predictive performance
* Hyperparameter tuning with cross-validation
* Feature importance analysis

---

## Evaluation Metrics

Due to class imbalance, accuracy is misleading.
Models were evaluated using:

* **F1 Score**
* **ROC-AUC**
* Confusion Matrix

---

## 📉 Results

| Model               | AUC   | F1 Score | Key Insight                      |
| ------------------- | ----- | -------- | -------------------------------- |
| Logistic Regression | ~0.62 | 0.21     | Moderate signal, interpretable   |
| Random Forest       | ~0.64 | ~0.00    | Failed to capture minority class |

### Key Observations

* Both models struggled to predict readmissions (<30 days)
* Random Forest overfit to majority class (predicted almost all “no readmission”)
* No statistically significant difference between models

---

## Key Drivers of Readmission

Consistent across models:

* Prior inpatient visits
* Emergency visits
* Comorbidity burden (CCI)
* Discharge disposition (rehab, psych facilities)
* Age

---

## Lessons Learned

This project highlighted important real-world ML challenges:

* **Class imbalance can dominate model behavior**
* High accuracy does not mean good performance
* Real healthcare data is noisy and difficult to model
* Simpler, interpretable models can be just as effective as complex ones

---

## 🚀 Future Improvements

* Try resampling techniques (SMOTE, undersampling)
* Explore gradient boosting (XGBoost, LightGBM)
* Incorporate temporal patient history
* Improve recall for minority class

---

##  Tech Stack

* Python (pandas, NumPy)
* scikit-learn
* statsmodels
* Matplotlib / Seaborn

---

## Repository Structure

```
├── data/              
├── notebooks/          # analysis & modeling
└── README.md
```


