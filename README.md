# Airbnb New User Booking Prediction
## Helnaz Soltani
### May 15th, 2020


### Objectives:
- Predicting new Airbnb users' first reservation location.

### Dataset information:
- Number of Instances: 250k
- Number of Attributes: 15
- Data Set Characteristics: Multivariate classification with 12 classes
- 12 possible outcomes of the destination country: 'US', 'FR', 'CA', 'GB', 'ES', 'IT', 'PT', 'NL','DE', 'AU', 'NDF' (no destination found), and 'other'
- Area: Business

### Data cleaning:
- Duplicated entries
- Null values
- Incorrect datatype
- Inconsistent values for some of the columns
- One-hot encoding for categorical feature

### Feature engineering:
- Number of actions
- Number of unique action type
- Number of devices
- Seconds elapsed mean between each activity for each user 
- All of the above features are calculated based on the data in users’ web session records (sessions.csv) with respect to their first activity on website.

### Exploratory data analysis:
- 58% of the users in the dataset did not end up booking (labeled as 'NDF'). This brought up another interesting question to answer: Are the first users book any reservation?
- Airbnb users tend to use Apple products more. Apple products are among the top 5 most popular devices.
- The mean and std of 'age' are 37 and 9, respectively.
- The null values in 'secs elapsed mean' were filled based on the observed corresponding EDA to make sure it does not affect the original statistics.
- English is the dominant language within the users and that make sense because the data were collected from the users in US.
- Signup method is dominated by 'basic' and 'facebook'.
- About 45% of the users did not reveal their gender.

### Question 1: Is a new Airbnb user book any reservation?
- To answer this, I considered 'NDF as one class and the rest as another class which make the problem of binary classification type. 
- 7 machine learning algorithm were modeled (Logistic Regression, Decision Tree, Random Forest, Gradient Boosting, Ada Boosting, XGBoosting, and multi-layer Perceptron.
- Based on AUC curve, Xgboosting and Gradient Boosting have highest performances.
- Hyperparameter tuning for these two algotithm was performed.
- Feature importance was extracted for these two algorithms.

### Question 2: Where a new Airbnb user will book reservation?
- To answer this, I extracted 'NDF as one class and nd focused on the users that ended up booking. 
- The dataset was highly imbalanced, so I used under sampling for the US observations, and then used oversampling for the rest of the target variables. However, it turns out that these techniques did not improve my models.
- 7 machine learning algorithm were modeled (Logistic Regression, Decision Tree, Random Forest, Gradient Boosting, Ada Boosting, XGBoosting, and multi-layer Perceptron.
- The evaluation metric for this problem according to Airbnb is NDCG.
- Based on NDCG score, Logistic Regression, Xgboosting and Gradient Boosting have highest performances.
- Hyperparameter tuning for Xgboosting was performed.
- Feature importance was extracted for Xgboosting and Gradient Boosting.

### Conclusions:
- Predicting whether or not a user will book a reservation combined with the marketing strategy is beneficial for business purposes.
- Predicting which countries are more popular for accommodation booking is beneficial for demand forecasting.
- Airbnb can build a recommendation system based on these predictions. Suggesting the destinations which are similar to the user’s choice (in terms of climate, nature, and things-to-do)

