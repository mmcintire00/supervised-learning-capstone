## Supervised Machine Learning Capstone
### Project: Predicting Credit Card Default

### IN PROGRESS: Implementation of SMOTE
### Background: When credit companys issue credit cards to consumers, those companies are taking on risk that the customer may not pay back the loan. This is considered a default on the payment. Frequently, lenders use customer information and history to determine credit risk[5].

### Project Goal: The goal of this project is to predict if a customer will default on the next months payment (target variable), given demographic and financial history data.

### Dataset: This study will use a dataset from the UCI machine learning repository. A link to the data can be found in the cited sources section. The data contains 25 variables and 30,000 rows of data. The data was collected over several months in 2005 from credit customers in Tiawan. The variables collected are both categorical and numerical. They include demographic information like age, sex, education level, marriage status. The study also includes credit information about the customers including bill and payment amount, payment status, an credit limit.

### Raw Variables:
* ID: ID of each client
* LIMIT_BAL: Amount of given credit in NT dollars (includes individual and family/supplementary credit
* SEX: Gender (1=male, 2=female)
* EDUCATION: (1=graduate school, 2=university, 3=high school, 4=others, 5=unknown, 6=unknown)
* MARRIAGE: Marital status (1=married, 2=single, 3=others)
* AGE: Age in years
----------------------
* PAY_0: Repayment status in September, 2005 (-1=pay duly, 1=payment delay for one month, 2=payment delay for two months, … 8=payment delay for eight months, 9=payment delay for nine months and above)
* PAY_2: Repayment status in August, 2005 (scale same as above)
* PAY_3: Repayment status in July, 2005 (scale same as above)
* PAY_4: Repayment status in June, 2005 (scale same as above)
* PAY_5: Repayment status in May, 2005 (scale same as above)
* PAY_6: Repayment status in April, 2005 (scale same as above)
----------------------
* BILL_AMT1: Amount of bill statement in September, 2005 (NT dollar)
* BILL_AMT2: Amount of bill statement in August, 2005 (NT dollar)
* BILL_AMT3: Amount of bill statement in July, 2005 (NT dollar)
* BILL_AMT4: Amount of bill statement in June, 2005 (NT dollar)
* BILL_AMT5: Amount of bill statement in May, 2005 (NT dollar)
* BILL_AMT6: Amount of bill statement in April, 2005 (NT dollar)
----------------------
* PAY_AMT1: Amount of previous payment in September, 2005 (NT dollar)
* PAY_AMT2: Amount of previous payment in August, 2005 (NT dollar)
* PAY_AMT3: Amount of previous payment in July, 2005 (NT dollar)
* PAY_AMT4: Amount of previous payment in June, 2005 (NT dollar)
* PAY_AMT5: Amount of previous payment in May, 2005 (NT dollar)
* PAY_AMT6: Amount of previous payment in April, 2005 (NT dollar)
----------------------
* Target Variable: default.payment.next.month: Default payment (1=yes, 0=no)

### Sci-kitlearn models implemented in this project:
* Logistic Regression
* K-Nearest Neighbors Classifier
* Random Forests Classifier
* Gradient Boost

### Workflow:
1. Load csv file into pandas

2. Clean null values and reformat raw table

3. Data Exploration with matplotlib

4. Feature Engineering

5. Principal Components Analysis

6. Implement initial ML models

7. Update model parameters with GridSearchCV

8. Implement final models and compare results

### Cleaning the data: Reclassified multiple ‘Other’ categories into one ‘Other’ category per variable. This will help reduce the number of features.

### Feature Engineering: 
* I created 5 new features: Percent Bill Paid per Month, Total of Bills (sum of all the bills) , Total of Payments (sum of all the payments), Total Percent Bills Paid (total of payments/total of bills), and Credit Utilization per month (monthly bill/credit limit).
* I also used pandas dummies to create dummy variables for all categorical data. 

### Principal Components Analysis: I used PCA to reduce the number of features in the dataset to those which described 95% of the variance in the data. This reduced the number of features from 68 to 39. 
 
### Discussion and Future Work:
* After evaluating 4 models, accuracies ranged from 0.80 to 0.83.
* Since the target variable was imbalanced, I used precision, recall, and AUC to compare model results.
* Overall, the updated models performed poorly in terms of identifying customers that will default on their payments.
* The models that performed the best were the Random Forest and Gradient Boost, with .76 AUC.
* Future work would be to see how the models perform when all data is made categorical. This would mean grouping payment, bill, and credit limit amounts into categories.

## Version 2.0 Update (7-6-21):

**Updated notebook for my supervised learning capstone. Updates include:**
* oversampling data with SMOTE to account for class imbalance of target variable (updates in progress. not final implementation).
* using RandomizedSearchCV paired with GridSearchCV to narrow input values and reduce run time.
* Assessing Precision-recall, focusing on improving recall for people who default


### Sources:

**[1] Raw data:** https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients

**[2] Literature:** [Yeh, I. C., & Lien, C. H. (2009). The comparisons of data mining techniques for the predictive accuracy of probability of default of credit card clients. Expert Systems with Applications, 36(2), 2473-2480.](https://bradzzz.gitbooks.io/ga-seattle-dsi/content/dsi/dsi_05_classification_databases/2.1-lesson/assets/datasets/DefaultCreditCardClients_yeh_2009.pdf)

**[3] Credit Limits:** https://www.nerdwallet.com/article/finance/30-percent-ideal-credit-utilization-ratio-rule

**[4] Exceeding Credit Limits:** https://www.cnbc.com/select/exceeding-credit-limit/

**[5] Credit Risk:** https://www.investopedia.com/terms/c/creditrisk.asp

**[6] Confusion Matrix Code:** http://scikit-learn.org/stable/auto_examples/model_selection/plot_confusion_matrix.html

**[7] Kaggle Variable Discussion:** https://www.kaggle.com/uciml/default-of-credit-card-clients-dataset/discussion/34608
