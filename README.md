# Fraud-Detect-Transaction

Please see the coding file attached or reach the link below: https://colab.research.google.com/drive/1dU1tPZ11zKKXg9GjjUbGRmtl3EGokUZ8#scrollTo=T5RNNg9EccMo

# I. Introduction
Detect Fraudulent Credit Card transactions using different Machine Learning models and compare performances
In this notebook, I explore various Machine Learning models to detect fraudulent use of Credit cards. I compare each model performance and results. The best results are achieved using a fine-tuned Random Forest, selected via GridSearchCV with balanced accuracy scoring.
## 1. Problem Statement
In this project we want to identify fraudulent transactions with Credit Cards. Our objective is to build a Fraud detection system using Machine learning techniques. In the past, such systems were rule-based. Machine learning offers powerful new ways.

The project uses a dataset of 98000 fully anonymized transactions. Each transation is labelled either fraudulent or not fraudulent. Note that prevalence of fraudulent transactions is very low in the dataset.

## 2. Dataset
The dataset contains real time transaction details of customers as it is entered into a credit card traansaction database. Dataset include these following main fields:
- trans_date_trans_time: The date and time of the transaction.
- cc_num: credit card number.
-  merchant: Merchant who was getting paid.
-  category: In what area does that merchant deal.
-  amt: Amount of money in American Dollars.
-  first: First name of the card holder.
-  last: Last name of the card holder.
-  gender: Gender of the cardholder.Just male and female!
-  street: Street of card holder residence
-  city: City of card holder residence
-  state: State of card holder residence
-  zip: ZIP code of card holder residence
-  lat: Latitude of card holder
-  long: Longitude of card holder
-  city_pop: Population of the city
-  job: Trade of the card holder
-  dob: Date of birth of the card holder

However, due to the computer's limited capacity, I won't utilize all of these columns; instead, I'll focus on only the most influential ones.

# II. Techniques
The project compares the results of different techniques :
  - Random Forest
  - Logistic Regression

The project pipeline can be briefly summarized in the following five steps:
## 1. Data Understanding
   
Here, we need to load the data and understand the features present in it. This would help us choose the features that we will need for your final model.
## 2. Feature Engineering & Encoding:
- I engineer several informative features:
  + Age based on date of birth
  + tns_hour extracted from transaction timestamp
  + distance between user and merchant location using the haversine formula
    
- For encoding:
  + Target Encoding is applied to high-cardinality categorical columns (merchant, street, city, job) using Stratified K-Fold to avoid data leakage.
  + One-Hot Encoding is applied to low-cardinality categorical columns (category, gender, state) to preserve clear separation
## 3. Train / Validation / Test Split
- The data is split into:
  - Training set (70%)
  - Validation set (15%)
  - Test set (15%)
- All sets are standardized using StandardScaler. This setup allows for controlled model development, tuning, and unbiased evaluation.
## 4. Model Building & Hyperparameter Tuning

I train two models: Logistic Regression, Random Forest. I fine-tune Random Forest using GridSearchCV over multiple hyperparameters (max_depth, n_estimators) and cross-validation. The selection is based on balanced accuracy, ideal for imbalanced classification.

## 5. Model Evaluation

Evaluation is done using multiple metrics: Balanced Accuracy, Precision, Recall, F1-Score, Confusion Matrix
# III. Results
- Accuracy: 0.99 → The model correctly classified 99% of the test samples.
- Weighted F1 Score: 0.99 → Excellent overall balance between precision and recall across classes.
This model is excellent at minimizing false alarms and strong overall, making it deployment-ready for real-world fraud detection.

<img width="598" height="93" alt="image" src="https://github.com/user-attachments/assets/d32d1268-b1dd-4221-820a-d0b5c66404e1" />

<img width="528" height="195" alt="image" src="https://github.com/user-attachments/assets/b3678175-0db5-4f2c-94e5-6a2458290c42" />















