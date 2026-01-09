# bias-fairness-ml
Bias, Fairness and Explainability in Machine Learning :
This project studies if machine learning models treat different groups fairly and how such fairness is explained.




--> Initial Bias Observation:

An expolatory analysis of adult income dataset reveals significt outcome disparities across sensitive attribute "sex"

Approximately 30.5% male earn more than 50k while only 11% of female do so.This disparity exists prior to model training and highlights importance of careful fairness evolution in downstream machine learning models.



--> Data Cleaning :

The Adult Income datset uses "?" to represent null values in several categoriacal attributes. These values were converted into nan and then removes for simplicity.
This preprocessing step reduces the size of dataset and is noted as a limitation of the study.
