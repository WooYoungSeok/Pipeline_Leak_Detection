# Pipeline Leak Detection Using Machine Learning

## Project Overview
This project explores the detection of pipeline leaks using vibration data and machine learning. By analyzing multi-class vibration data categorized into five labels, the project implements and evaluates two machine learning models: **Support Vector Classification (SVC)** and **XGBoost**. Key steps include data exploration (EDA), preprocessing, hyperparameter tuning, and performance comparison.

---

## Data Link
https://www.aihub.or.kr/aihubdata/data/view.docurrMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=138

---

## Key Features
- **Vibration Data Analysis:** Analyzed vibration signals from pipelines categorized as `normal`, `out` (external leakage), `in` (internal leakage), `other` (environmental noise), and `noise` (mechanical noise).
- **Machine Learning Models:** Implemented SVC and XGBoost to perform multi-class classification.
- **Performance Tuning:** Conducted hyperparameter tuning using **GridSearchCV** for SVC and **Hyperopt** for XGBoost.
- **Real-Time Potential:** The results can be used for real-time automatic leak detection in pipelines.

---

## Results
### SVC
- Best hyperparameters: `gamma='scale'`, `kernel='rbf'`, `C=100`
- Cross-validation accuracy: **89.79%**
- Test set accuracy: **90.37%**

### XGBoost
- Best hyperparameters:
  - `max_depth=10`
  - `min_child_weight=1`
  - `gamma=0.156`
  - `reg_alpha=0.2`
  - `reg_lambda=4.633`
  - `subsample=0.908`
  - `colsample_bytree=0.501`
  - `learning_rate=0.3`
- Cross-validation accuracy: **94.7%**
- Test set accuracy: **94.30%**
- **F1-Score Comparison:**
  - `normal`: **0.92** (XGBoost) vs. **0.86** (SVC)
  - `out`: **0.88** vs. **0.79**
  - `in`: **1.00** vs. **1.00**
  - `other`: **0.89** vs. **0.80**
  - `noise`: **0.93** vs. **0.89**

---

## Methodology
1. **Data Preprocessing:**
   - Dropped irrelevant features (`0Hz` frequency).
   - Engineered additional features:
     - **Mean Frequency:** Average of frequency bands.
     - **Sum of Max Frequencies:** Sum of maximum frequency values.
   - Standardized data using `StandardScaler`.

2. **Model Training:**
   - **SVC:** Used `GridSearchCV` to tune `gamma`, `kernel`, and `C`.
   - **XGBoost:** Applied Bayesian optimization with `Hyperopt` to find the optimal hyperparameters.

3. **Evaluation:**
   - Compared accuracy, F1-scores, and performance across both models.
   - XGBoost outperformed SVC in all evaluation metrics.

---

## Limitations
- Data leakage: The dataset was not shuffled before training, potentially leading to sequence-dependent learning.
- Imbalanced data: Significant variations in label frequencies may have affected the model performance.

---

## References
1. **Kim, B., Jeon, J., Lee, S.** (2022). Machine Learning Model for Pipeline Leak Detection Using Vibration Sensor Data. _Korea Information Science Society Proceedings_, 2022 (Jeju), 1361-1363.
2. **Choi, J., Lim, S.** (2023). SVM-Based Leak Detection and Classification Using Leakage Noise Spectrum. _Journal of Electronics Engineering_, 60(2), 6-14. DOI: 10.5573/ieie.2023.60.2.6
3. **XGBoost Documentation.** (2024). [XGBoost Official Documentation](https://xgboost.readthedocs.io/en/stable/python/python_api.html)

---

## Contact
- **Author:** Yeongseok Woo  
- **Affiliation:** AI Convergence Department, Sungkyunkwan University  
- **Email:** [dbtjd8289@gmail.com]
