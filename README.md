# Ai-6
Part 1: 

1. Problem Definition 

AI Problem:
Predicting employee attrition risk in large organizations.

Objectives:

1. Identify high-risk employees likely to resign in the next 6 months.


2. Help HR design better retention strategies.


3. Reduce turnover-related costs.



Stakeholders:

HR Department

Department Managers


Key Performance Indicator (KPI):

Attrition prediction accuracy (e.g., F1-score > 85%)





2. Data Collection & Preprocessing

Data Sources:

1. Employee records (age, role, performance, tenure)


2. Exit interviews and HR logs



Potential Bias:
If past exits were influenced by discriminatory practices (e.g., gender bias), the model may learn and replicate this bias.

Preprocessing Steps:

1. Handle missing values in performance and exit reason columns.


2. Normalize continuous features like salary and tenure.


3. Encode categorical variables like job role or department.






3. Model Development

Model Choice:
Random Forest – suitable for tabular HR data, handles non-linearity, interpretable feature importance.

Data Split Strategy:

70% training

15% validation

15% test


Hyperparameters to Tune:

1. max_depth: controls overfitting.


2. n_estimators: number of trees; affects performance and stability.





4. Evaluation & Deployment 

Evaluation Metrics:

1. F1-score – balances precision and recall, important when both false positives and false negatives are costly.


2. ROC-AUC – measures ability to distinguish between classes.



Concept Drift:
It refers to changes in data patterns over time.
Monitoring: Periodically retrain the model using recent data and track performance metrics.

Technical Challenge:
Scalability: Model must handle real-time predictions across thousands of employees simultaneously.




Part 2: 

1. Problem Scope 

Problem:
Predict the risk of patient readmission within 30 days of discharge.

Objectives:

1. Reduce preventable readmissions.


2. Improve post-discharge care planning.


3. Optimize hospital resource allocation.



Stakeholders:

Hospital administrators

Doctors/Nurses





2. Data Strategy 

Data Sources:

1. Electronic Health Records (EHRs)


2. Demographic and socio-economic data



Ethical Concerns:

1. Patient privacy and data leaks


2. Potential algorithmic discrimination (e.g., underestimating risk in minority populations)



Preprocessing Pipeline:

Remove personally identifiable information (de-identification)

Feature engineering (e.g., days since last admission, number of chronic illnesses)

Normalize lab results, impute missing vitals, one-hot encode diagnoses




3. Model Development 

Model Choice:
XGBoost – handles imbalanced classes well, fast, interpretable with SHAP.

Confusion Matrix (hypothetical):
|               | Predicted: No Readmit | Predicted: Readmit |
|---------------|-----------------------|--------------------|
| Actual: No    | 80                    | 20                 |
| Actual: Yes   | 15                    | 85                 |

Precision: 85 / (85 + 20) = 0.81

Recall: 85 / (85 + 15) = 0.85





4. Deployment

Integration Steps:

1. Deploy model via hospital’s internal API


2. Embed into EHR interface for doctors to view risk score


3. Schedule batch updates for retraining weekly



Regulatory Compliance:

Encrypt all patient data

Follow HIPAA for U.S. or Data Protection Act in Kenya

Audit data access and maintain logs




5. Optimization

Method to Address Overfitting:
Apply regularization (lambda, alpha) in XGBoost or use dropout in neural networks if applicable.




Part 3: 

1. Ethics & Bias 

Impact of Biased Data:
If the model is trained on data with historical biases (e.g., fewer readmissions recorded for low-income patients due to poor follow-up), it may underpredict risks in those groups, worsening health inequalities.

Mitigation Strategy:
Perform fairness audits (e.g., compare predictions across age, gender, income) and apply reweighting or adversarial debiasing.



2. Trade-offs

Interpretability vs Accuracy:
In healthcare, interpretable models (e.g., decision trees) are safer and more trusted, even if slightly less accurate. Deep learning may perform better but lacks transparency.

Limited Resources Impact:
A computationally light model (like logistic regression or decision trees) would be preferred over resource-heavy neural networks due to hardware constraints and the need for quick inference times.




Part 4: 

1. Reflection 

Most Challenging Part:
Designing the preprocessing pipeline – ensuring data is clean and ethical while preserving signal.

Improvements with More Resources:

Access to diverse datasets across hospitals

Deploy ensemble models

Hire data ethicists for fairness auditing




2. AI Workflow Diagram 

Problem Definition
        ↓
Data Collection
        ↓
Preprocessing & Feature Engineering
        ↓
Model Selection & Training
        ↓
Evaluation (Validation/Test Sets)
        ↓
Deployment
        ↓
Monitoring & Maintenance


