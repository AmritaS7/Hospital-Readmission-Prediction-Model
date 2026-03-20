**Requirements**<br>
pandas<br>
numpy<br>
scikit-learn<br>
xgboost<br>
phik<br>
shap<br>
matplotlib<br>
seaborn<br>
jupyter<br>


**Project Overview**

Hospital readmissions are a high-cost burden on the healthcare system and a significant indicator of patient care quality. This project utilizes the 130-US Hospitals Diabetes Dataset to develop a machine learning pipeline that predicts whether a patient will be readmitted within 30 days of discharge.

The primary goal was to maximize Recall, ensuring that high-risk patients are identified for proactive intervention, even at the cost of higher false positives (low precision).

**About the Dataset**

The dataset used in this project is the Diabetes 130-US hospitals for years 1999-2008 dataset, available via the UCI Machine Learning Repository.

Instance Count: ~101,000 clinical records.

Attributes: 50 features including patient demographics, admission details, medications, and lab results (e.g., HbA1c levels).

Target Variable: readmitted (Categorized into: No readmission, >30 days, and <30 days).

Challenge: The dataset is naturally imbalanced, as only a small percentage of patients are readmitted within the critical 30-day window, requiring specialized evaluation metrics beyond simple accuracy.

**Exploratory Data Analysis (EDA)**

Traditional correlation matrices (like Pearson) often fail with categorical healthcare data. In this project:

**ϕ 
k
​	
  Correlation:** Used to capture non-linear and categorical dependencies that standard methods miss.

**Key Findings:** Identified strong associations between readmission and factors such as prior hospital utilisation, post discharge disposition, medical complexity and length of stay in hospital.

Two models were rigorously tested against a highly imbalanced dataset: Random Forest and XGBoost.

| Metric | Random Forest (Selected) | XGBoost |
|--------|--------------------------|-----------|
| Recall | **0.57** | 0.51 |
| F1-Score | **0.22** | 0.21 |
| PR-AUC | 0.13 | **0.14** |
| Precision | 0.14 | 0.14 |

**Decision Logic:** While XGBoost had a slightly better ranking ability (PR-AUC), Random Forest was selected due to its superior Recall (0.57). In a clinical setting, missing a patient who needs care (False Negative) is more critical than flagging a patient who is actually fine (False Positive).

**Model Interpretability (SHAP)**

I utilized SHAP values to explain model behavior:

**Global Interpretability:** Identified the top features driving readmission risk across the entire population.

**Local Interpretability:** (Optional: mention if you visualized specific patient cases) Provided transparency into why specific patients were flagged as high-risk.

**Future Improvements**

**Feature Engineering:** Incorporating more granular medication data or socio-economic indicators.

**Sampling Techniques:** Exploring SMOTE-Tomek or cost-sensitive learning to further improve the PR-AUC.

**Deep Learning:** Testing Tabular Transformers or Neural Networks for better pattern recognition.
