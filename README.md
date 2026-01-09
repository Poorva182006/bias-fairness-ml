# bias-fairness-ml
Bias, Fairness and Explainability in Machine Learning :
This project studies if machine learning models treat different groups fairly and how such fairness is explained.


--> Initial Bias Observation:
An expolatory analysis of adult income dataset reveals significt outcome disparities across sensitive attribute "sex"
Approximately 30.5% male earn more than 50k while only 11% of female do so.This disparity exists prior to model training and highlights importance of careful fairness evolution in downstream machine learning models.



--> Data Cleaning :
The Adult Income datset uses "?" to represent null values in several categoriacal attributes. These values were converted into nan and then removes for simplicity.
This preprocessing step reduces the size of dataset and is noted as a limitation of the study.



--> Feature Encoding and Data Split:
Categorical features were transformed using one-hot encoding.
The target variable (income) was converted into a binary label.
The dataset was split into training and testing sets using a
stratified split to preserve class distribution.
During target variable encoding, it was observed that income labels
contained leading whitespace due to the original data formatting.
Therefore, string normalization using the strip() function was applied
to ensure correct and consistent binary encoding.


-->Baseline Model:
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



--> Fairness Evaluation by Sex:
Fairness analysis was conducted with respect to the sensitive attribute
'sex'. Although overall accuracy was higher for female instances, this
metric was influenced by class imbalance in the dataset. Analysis of
prediction behavior revealed substantial disparities across groups.

The model predicted high income (>50K) for approximately 46% of male
instances but only about 15% of female instances. Furthermore, among
individuals who truly earned more than 50K, the true positive rate was
lower for females (≈70%) than for males (≈85%). These results indicate
violations of demographic parity and equal opportunity, suggesting that
the model disproportionately favors male instances in high-income
predictions.



-->Bias mitigation:
Bias mitigation through class reweighting led to measurable changes in
model behavior. The positive prediction rate for female instances
increased from approximately 9% to 15%, while the true positive rate
for high-income females improved from about 55% to 70%. Although these
changes reduced disparities, notable gaps between male and female
groups persisted, indicating that simple reweighting alone is
insufficient to fully address structural bias present in the data.


--> Discussion and Limitations:
The fairness analysis demonstrates that the observed disparities in
model predictions are strongly influenced by historical and structural
patterns present in the training data. Prior to mitigation, the model
exhibited substantially lower positive prediction rates and true
positive rates for female instances, despite comparable qualifications.

Applying class reweighting improved outcomes for both groups, with
notable gains for female instances. In particular, the true positive
rate for high-income females increased significantly, indicating that
reweighting can partially mitigate unequal treatment arising from class
imbalance. However, disparities between male and female groups persisted
even after mitigation, suggesting that simple reweighting alone is
insufficient to fully address structural bias.

This study has several limitations. First, sensitive attributes were
analyzed independently, without considering intersectional effects such
as the interaction between sex and race. Second, missing values were
removed rather than imputed, which may affect the representativeness of
the dataset. Finally, the employed fairness metrics capture statistical
disparities but do not establish causal relationships between features
and outcomes.



--> Conclusion and Future Work:
This project investigated fairness in machine learning using the Adult
Income dataset, with a focus on outcome disparities across the sensitive
attribute of sex. Through systematic evaluation, the baseline model was
found to violate demographic parity and equal opportunity, reflecting
inequalities present in the underlying data.

A mitigation strategy based on class reweighting improved predictive
outcomes for female instances, particularly in identifying high-income
individuals. Nevertheless, residual disparities remained, highlighting
the inherent difficulty of achieving fairness using simple statistical
adjustments alone.

Future work may explore more advanced mitigation approaches, including
causal fairness methods, threshold optimization, and intersectional
analysis across multiple sensitive attributes. Additionally, alternative
model architectures and domain-specific fairness constraints could be
investigated to better balance predictive performance and equitable
outcomes in high-stakes decision-making systems.
