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

## Visuals  

### 1. Dataset Merging Process  
<img width="1085" height="342" alt="image" src="https://github.com/user-attachments/assets/3c75a7ff-7ea0-4864-8d9f-64257f9bd98f" />
This flowchart shows how eight raw datasets (customers, orders, reviews, payments, products, etc.) were merged into a single order-level table (~99k rows). This unified dataset formed the foundation for feature engineering and model building. 

---

### 2. Model Performance Comparison  
<img width="1079" height="696" alt="image" src="https://github.com/user-attachments/assets/d6eec564-3b1e-48b5-bc92-448d5ea92200" />
CatBoost (tuned with Optuna) slightly outperformed Logistic Regression and Stacked models, achieving the highest F1 (0.893) and AUC (0.743), a strong balance of accuracy and interpretability.  

---

### 3. ROC Curve (Logistic vs Stacked vs CatBoost)  
<img width="1000" height="522" alt="image" src="https://github.com/user-attachments/assets/3fbd5cbc-f58a-4deb-b280-540ba80ee869" />
The ROC curves confirm that CatBoost and the Stacked model deliver stronger predictive power (higher AUC) compared to Logistic Regression, validating the choice of CatBoost as the best deployment candidate.  

## Business Insights  

- Delivery speed matters most → Longer delivery times strongly reduce satisfaction, so Olist should partner with multiple logistics providers and set stricter SLAs.  
- Late deliveries = churn risk → Orders arriving later than promised drive negative reviews, requiring proactive vouchers or apologies to retain customers.  
- Large/multi-seller orders → Complex orders lower satisfaction slightly, meaning extra quality control and shipment coordination are needed.  
- Regional variation → Some states show lower satisfaction, suggesting region-specific courier partnerships and targeted customer programs.  

## Tech Stack
- Python: Pandas, NumPy, Scikit-learn, CatBoost, LightGBM, XGBoost
- Optuna: Hyperparameter tuning
- SHAP: Model interpretability
- Jupyter Notebook + GitHub for collaboration
