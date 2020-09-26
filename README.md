# Online Shoppers Intent

## Executive Summary:
We are assuming the position of business members at DataScienceDeals.com a company that sells courses on Data Science. We have data related to the visitors that come to our site.

The objective of this project is to predict which visitors are likely to produce revenue. This will feed into our new 1:1 chat help service feature that will be able to aid potential customers.

##  Key Files:
1.  [Link](https://docs.google.com/presentation/d/1Cu6vxCA_1aIgoW1ZqArEayFVPDSDD8eRxzvjWMUvT2I/edit?usp=sharing)
to google slides presentation file
2.  Online_Shoppers_Intent.pdf: PDF of presentation slides
3.  'Online_Shoppers_Intent'.ipynb: Jupyter Notebook
4.  online_shoppers_intention.csv: Raw CSV file with data

##  Methodology:
1. **Executive Summary**  
2. **Import Data**  
3. **Data Cleansing**  
4. **Data Exploration**  
    4.1 Dataset Information  
    4.2 Feature Information  
    4.3 Screening for Categorical Variables
5. **Baseline Model**  
    5.1 Split and transform the training and test data  
    5.2 Decision tree model  
6. **Exploring Improvements on Baseline Model**  
    6.1 Grid Search CV for Decision tree with Entropy impurity  
    6.2 Logistic Regression Classifier  
    6.3 Ensemble Methods - Random Forests  
7. **Threshold Selection** 
8. **Testing our Model** 
9. **Conclusions**  
10. **Recommendations**
    
##  Key Findings:
The initial scores for the baseline decision tree mdoel: F1: 0.5844, Accuracy: 0.8716, Roc_AUC: 0.7587.
Very small improvements were made using a combinatory hyperparameter optimisation.

Below we can get some idea of how important each feature is to the random forest model. I have included only the top 10 important features.
 
### The top 10 Feature importances are:  
PageValues, Score: 0.27  
ProductRelated_Duration, Score: 0.068  
ExitRates, Score: 0.067  
Administrative_Duration, Score: 0.044  
BounceRates, Score: 0.04  
Informational_Duration, Score: 0.021  
Month_Nov, Score: 0.017  
Region_1, Score: 0.011  
Administrative_0, Score: 0.011  
TrafficType_2, Score: 0.01  

In the image below we can observe that the optimal threshold value given associated costs of outcomes,   
was very close to the intersection of Precision and Recall scores.  
![image](https://user-images.githubusercontent.com/40424244/94149035-4a530080-fe6f-11ea-8ac0-6afdbe20b96d.png)

Continuing with a logistic Regression model performed better than the baseline model, giving a roc_auc score of 0.89.
Random Forest ensemble model returned evaluated best at the end of the project with a roc_auc score of 0.89 but was increased to 0.93 using hyperparameter optimisation through Random and Grid Search CV.

##  Conclusions:
There was a slight increase in model performance when using ensemble models (Random Forest) over Logistic Regression. 
The Grid Search Parameter optimsation was paramount in obtaining the highest roc_auc score in our random forest model

Here are the top ten feature importances
- Page Value was the most important feature according to the random forest model. It represents "the average value for a page that a user visited before landing on the goal page or completing an Ecommerce transaction (or both)."
- Product related duration was second most important and represents the duration of time spent on product related pages.
- Exit rate was third most important : "For all pageviews to the page, Exit Rate is the percentage that were the last in the session".  

![image](https://user-images.githubusercontent.com/40424244/94347784-1b838880-002f-11eb-885e-a8c5630badcf.png)

A Key component of our model was incoroporating the costs (penalties for getting predictions wrong or right)
Once we selected the threshold (0.43) that took those costs into account we were able to obtain :  a Precision score = 0.7 and Recall score = 0.63

##  Recommendations:
Feature selection could be implemented at some stage to reduce dimensionality and allow the model to work with more relevant data as an input. 
Only 9 of the 400+ features had an importance score of over 0.1

Based on the model performance we can go ahead and provide the feature engineer team with the data needed to build a chat box model. The Chat Box will certainly benefit from the results of this model but work can be done to increase the model performance.

Feedback to the team can be provided regarding the most important features according to the model. Specifically 'Page Values', 'Exit Rate' and 'Product Related Duration' among a few others would be worth considering to reverse engineer in pursuit of optimising the website and thus increasing the revenue for 'DataScienceDeals.com' 
