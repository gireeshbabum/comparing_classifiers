# comparing_classifiers

Business requirement
--------------------

Optimize the efficiency and effectiveness of outbound phone marketing campaigns for bank term deposits by identifying the most predictive customer segments and contact strategies to maximize conversion rates while minimizing marketing costs.

Key Points:

Efficiency: Reduce the number of calls required to convert a lead into a customer.

Effectiveness: Increase the overall conversion rate of phone marketing campaigns.

Customer Segmentation: Identify customer profiles most likely to subscribe to the term deposit.

Contact Strategy Optimization: Determine the optimal number and timing of calls for different customer segments.

Cost Reduction: Minimize marketing expenses by targeting the most promising leads and optimizing call resources.

By achieving these objectives, the bank can improve its return on investment (ROI) for phone marketing campaigns, enhance customer satisfaction, and strengthen its market position.


Dataset location : https://archive.ics.uci.edu/dataset/222/bank+marketing

Input variables:
# bank client data:
1 - age (numeric)
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')
6 - housing: has housing loan? (categorical: 'no','yes','unknown')
7 - loan: has personal loan? (categorical: 'no','yes','unknown')
# related with the last contact of the current campaign:
8 - contact: contact communication type (categorical: 'cellular','telephone')
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
# other attributes:
12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric)
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
# social and economic context attributes
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)
17 - cons.price.idx: consumer price index - monthly indicator (numeric)
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)
20 - nr.employed: number of employees - quarterly indicator (numeric)

Output variable (desired target):
21 - y - has the client subscribed a term deposit? (binary: 'yes','no')

Jupyter notebook :  





Summary of Model Performance
-----------------------------
1. Logistic Regression

Train Time: 0.834 seconds
Train Accuracy: 91.18%
Test Accuracy: 91.14%
Analysis: Logistic Regression is a well-balanced model in this case, providing good performance on both training and test data. It is relatively fast to train and maintains good generalization, making it a reliable choice for this dataset.

2. K-Nearest Neighbors (KNN)

Train Time: 0.001 seconds (very fast)
Train Accuracy: 92.78%
Test Accuracy: 90.07%
Analysis: KNN offers a slightly higher training accuracy than Logistic Regression but shows a slight drop in test accuracy. The model is extremely fast to train, making it suitable for scenarios where training time is critical. However, it may be more prone to overfitting, as indicated by the drop in test accuracy.

3. Decision Tree

Train Time: 0.165 seconds
Train Accuracy: 100%
Test Accuracy: 88.69%
Analysis: The Decision Tree model perfectly fits the training data (100% accuracy), but this comes at the cost of generalization, as seen in the lower test accuracy. This is a classic sign of overfitting, where the model learns the training data too well, leading to poorer performance on unseen data.

4. Support Vector Machine (SVM)

Train Time: 10.45 seconds
Train Accuracy: 92.27%
Test Accuracy: 91.20%
Analysis: SVM achieves a good balance between training and test accuracy, similar to Logistic Regression, but at a significantly higher computational cost (longer training time). SVM can be very powerful, especially with high-dimensional data, but it requires more resources and time to train.

Overall Considerations
----------------------

Handling Imbalanced Classes: None of the models explicitly address imbalanced classes in this summary. For such scenarios, Logistic Regression and SVM can be more easily adapted with class weighting or sampling techniques.

Training Speed: KNN is the fastest to train, making it suitable for quick predictions. However, SVM, despite being the slowest, provides a slightly better test accuracy.

Interpretability: Logistic Regression is the most interpretable model, providing straightforward coefficients that are easy to understand. Decision Trees are also interpretable but can become complex and overfit easily. KNN and SVM are less interpretable, especially SVM, which operates in a transformed feature space.

Recommendation
--------------
Best All-Rounder: Logistic Regression offers a good balance of speed, accuracy, and interpretability. It’s a strong candidate for the best all-rounder model in this context.
High Accuracy (But Risk of Overfitting): If interpretability is less important and overfitting is managed, SVM could be considered due to its slightly higher test accuracy. However, the longer training time is a downside.
When Speed is Critical: If you need quick results and have limited computational resources, KNN could be a practical choice, despite its slight drop in test accuracy.
You can further improve these models by performing hyperparameter tuning, feature engineering, and considering model ensembles to achieve better performance.

