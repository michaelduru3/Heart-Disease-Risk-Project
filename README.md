# UCI HEART RISK DISEASE PROJECT
This project embarked on the critical task of developing a heart disease screening system using the Cleveland cohort of the UCI Heart Disease Dataset. Our analysis focused on a dataset comprising 304 patient records.

## Overview
Data Preparation and Feature Engineering: Initially, we identified 6 core clinical features (age, sex, cp, trestbps, chol, thalch) as most relevant for prediction. Through a meticulous preprocessing pipeline, these features were transformed and expanded:

Physiological Validation: Impossible values (e.g., 0 for blood pressure or cholesterol) were identified and treated as missing, allowing for more robust handling.
Iterative Imputation: Missing values in critical features like ca, slope, and thal were intelligently filled using IterativeImputer, which models each feature with missing values as a function of other features.
Outlier Treatment: Numerical features (age, trestbps, chol, thalch) underwent outlier detection, and extreme values were treated using capping and flooring (Winsorization) to prevent undue influence on the models.
Categorical Encoding: Categorical features such as sex and cp were converted into numerical representations using One-Hot Encoding, expanding our feature set from 6 to 10 features (sex_Male, sex_Female, cp_asymptomatic, cp_atypical angina, cp_non-anginal, cp_typical angina).
Feature Scaling: All numerical features were standardized using StandardScaler to ensure that no single feature dominated the learning process due to its scale.
Model Training and Evaluation: We employed three different classification algorithms: Logistic Regression, Decision Tree, and Random Forest. To ensure model robustness and avoid overfitting, we utilized:

Stratified K-Fold Cross-Validation: This method provided a more reliable estimate of model performance on unseen data by training and testing on different folds while maintaining class proportions.
Hyperparameter Tuning (e.g., max_depth, n_estimators): While explicit grid search was not demonstrated, key hyperparameters like max_depth for Decision Trees and n_estimators along with max_depth for Random Forest were chosen to constrain model complexity and mitigate overfitting tendencies. The class_weight='balanced' was also used in Random Forest to address potential class imbalance.
Model evaluation on the test set revealed strong performance, with Random Forest showing the best recall (0.89) and a high ROC-AUC (0.92), indicating its effectiveness in identifying positive cases while maintaining a good balance of overall accuracy.

For binary classification, we utilized a 0.5 probability threshold to convert model confidence scores into definitive predictions (presence or absence of heart disease). This default threshold was chosen to provide a balanced approach to classifying positive and negative cases, especially given the dataset's relatively small size.

Future Improvements: While the current models demonstrate promising performance, there is significant room for improvement:

Increased Dataset Size: The Cleveland cohort, with its 304 rows, provides a limited view. Incorporating additional data from other heart disease datasets (e.g., Hungarian, Switzerland, Long Beach VA) could dramatically improve model generalization and robustness.
Additional Clinical Features: Integrating more clinical parameters, such as detailed lab results (e.g., specific cholesterol fractions, blood glucose markers beyond fbs), genetic markers, or lifestyle factors, could enhance the predictive power and clinical utility of the system.
Advanced Feature Engineering: Exploring more sophisticated feature engineering techniques or dimensionality reduction methods could uncover deeper insights and improve model performance.
In conclusion, this project established a robust machine learning pipeline for heart disease screening. The meticulous data preprocessing, comparative model analysis, and thoughtful evaluation provide a solid foundation. With further expansion of data and features, this system holds significant potential for real-world clinical applications.

## Technologies Used
* Python
* OpenCV / Machine Learning
* Jupyter Notebooks
