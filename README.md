# bias-fairness-ml
Bias, Fairness and Explainability in Machine Learning :
This project studies if machine learning models treat different groups fairly and how such fairness is explained.




--> Initial Bias Observation:

An expolatory analysis of adult income dataset reveals significt outcome disparities across sensitive attribute "sex"

Approximately 30.5% male earn more than 50k while only 11% of female do so.This disparity exists prior to model training and highlights importance of careful fairness evolution in downstream machine learning models.



--> Data Cleaning :

The Adult Income datset uses "?" to represent null values in several categoriacal attributes. These values were converted into nan and then removes for simplicity.
This preprocessing step reduces the size of dataset and is noted as a limitation of the study.



--> Feature Encoding and Data Split

Categorical features were transformed using one-hot encoding.
The target variable (income) was converted into a binary label.
The dataset was split into training and testing sets using a
stratified split to preserve class distribution.
During target variable encoding, it was observed that income labels
contained leading whitespace due to the original data formatting.
Therefore, string normalization using the strip() function was applied
to ensure correct and consistent binary encoding.

-->Baseline Model

A Logistic Regression model was trained as an interpretable baseline.
The model achieves reasonable predictive performance and serves as
a reference point for subsequent fairness evaluation.

During baseline model training, convergence warnings were observed when
using the default optimization solver. This behavior was attributed to
the high-dimensional and sparse feature space resulting from one-hot
encoding of categorical variables, as well as class imbalance in the
target variable. To improve optimization stability and convergence,
the Logistic Regression solver was switched to `liblinear`, which is
better suited for binary classification with sparse and correlated
features. Additionally, class weighting was applied to account for
imbalanced class distributions.


