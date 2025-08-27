# Olist-Customer-Satisfaction
Machine learning project using the Olist Brazilian e-commerce dataset (~99k orders). Built an end-to-end pipeline from data preparation and feature engineering to model evaluation. Achieved 82% accuracy (F1 0.893, AUC 0.743), identifying key drivers of customer satisfaction such as delivery speed, late deliveries, and order complexity.

## Project Objective 
Predict whether customers will be satisfied (review score ≥ 4) immediately after order delivery, enabling proactive retention strategies for Olist (Brazil’s largest e-commerce marketplace).

## Dataset
- Source: Olist e-commerce dataset (2016–2018)
- Size: ~99,000 orders
- Tables: Orders, Customers, Payments, Products, Reviews, Geolocation, Sellers
- Target Variable: Review score (binary: ≥4 = satisfied, <4 = not satisfied)

## Workflow
1. Data Preparation – merged 8 datasets into order-level features
2. Feature Engineering – created 15 predictors (delivery days, late flag, order complexity, product attributes, payment methods, etc.)
3. Modeling – compared Logistic Regression, Random Forest, XGBoost, LightGBM, CatBoost, and Stacking
4. Hyperparameter Tuning – used Optuna to optimize CatBoost
5. Evaluation – Accuracy, Precision, Recall, F1, AUC, Log Loss
6. Explainability – SHAP analysis to identify key satisfaction drivers
