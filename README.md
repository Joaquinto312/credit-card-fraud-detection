# Credit Card Fraud Detection: Handling Highly Imbalanced Data
## **Project Overview**:
Credit card fraud costs millions of dollars to the banks each year, but they are extremely rare compared to the normal transactions creating highly imbalanced data
## **Methodology & Tech Stack**:
To prevent the model from simply predicting "Not Fraud" for every transaction, several advanced techniques were applied:
*   **Data Splitting:** Stratified Train/Test split to maintain the original class distribution
*   **SMOTE (Synthetic Minority Over-sampling Technique):** Applied **only** to the training set to prevent data leakage and ensure realistic model evaluation
*   **Hyperparameter Tuning:** Used `GridSearchCV` to find the optimal parameters for the Gradient Boosting model
*   **Threshold Optimization:** Replaced the default 0.5 classification threshold by analyzing the Precision-Recall curve to find the exact point that maximizes the **F1-Score**
## Results and Model Comparison
The models were evaluated focusing on Precision, Recall, F1-Score, and ROC AUC.

| Model | Precision | Recall | F1-Score | ROC AUC |
| :--- | :---: | :---: | :---: | :---: |
| Random Forest (default threshold) | 0.8461 | 0.8048 | 0.8250 | 0.9652 |
| **Random Forest (optimized threshold)** | **0.9320** | **0.7804** | **0.8495** | **0.9652** |
| GradBoost (baseline) | 0.1974 | 0.8780 | 0.3223 | 0.9759 |
| GradBoost (tuned) | 0.4101 | 0.8536 | 0.5540 | 0.9706 |
| GradBoost (optimized threshold) | 0.8130 | 0.8130 | 0.8130 | 0.9706 |
## Business Impact
*   **The Winning Model:** The **Random Forest** with an optimized threshold proved to be the most effective model. 
*   By tuning the probability threshold, the **Precision spiked to 93.2%**. This means that when the model flags a transaction as fraud, it is almost entirely certain, drastically reducing the number of falsely blocked cards and improving customer experience. 
*   The overall **F1-Score of 0.85** represents an excellent equilibrium between stopping financial losses and maintaining customer satisfaction.

## Acknowledgments
The methodologies, technical approach, and custom evaluation functions used in this project were inspired by the knowledge acquired during the **Data Science Lab at WorldQuant University**.
