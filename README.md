# Online Shoppers Intent

## Executive Summary:
We are assuming the position of data scientists at 'DataScienceDeals.com' a company that sells courses on Data Science. We have data related to the visitors that come to our site.

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
    4.4 Pairwise Associations and correlation of Variables  
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
The initial scores for the baseline decision tree model: F1: 0.5728, Accuracy: 0.8691, Roc_AUC: 0.7498.  
Very small improvements were made using a combinatory hyperparameter optimisation.

Below we can get some idea of how important each feature is to the random forest model. I have included only the top 10 important features.
 
### The top ten feature importances
- PageValues, Score: 0.316  
- ExitRates, Score: 0.081  
- ProductRelated_Duration, Score: 0.08  
- ProductRelated, Score: 0.071  
- Administrative_Duration, Score: 0.052  
- BounceRates, Score: 0.051  
- Administrative, Score: 0.041  
- Informational_Duration, Score: 0.026  
- Month_Nov, Score: 0.019  
- Informational, Score: 0.019 

In the image below we can observe that the optimal threshold value given associated costs of confusion matrix outcomes:    

![image](https://user-images.githubusercontent.com/40424244/94539026-a1c0ea00-023c-11eb-926a-2f2954b9c0c9.png)  


As you can see the optimal threshold is at a point that favours recall over precision. Which reflects the nature of our business as we want to cpture the highest proportion of customers that come to our site in the model predictions.

An out-of-box logistic regression model performed better than the baseline model, giving a roc_auc score of 0.90.

The random forest ensemble model returned evaluated best at the end of the project with a roc_auc score of 0.89 but was increased to 0.933 using hyperparameter optimisation through Random and Grid Search CV (6 iterations).

##  Conclusions:
Our model favours recall over precision so we can capture a higher proportion of customers to our site. 
The optimal threshold chosen reflects the costs involved for predicting false negatives and false positives where the cost of a false negative is higher than a false positive.

There was a slight increase in model performance when using ensemble models (Random Forest) over Logistic Regression. The Grid Search Parameter optimsation was paramount in obtaining the highest roc_auc score in our random forest model


Page Value was the most important feature according to the random forest model. It represents "the average value for a page that a user visited before landing on the goal page or completing an Ecommerce transaction (or both)."  
Product related duration was second most important and represents the duration of time spent on product related pages. Exit rate was third most important : "For all pageviews to the page, Exit Rate is the percentage that were the last in the session".  

![image](https://user-images.githubusercontent.com/40424244/94539390-109e4300-023d-11eb-8dae-40b453c106ec.png)


A key component of our model was incoroporating the costs (penalties for getting predictions wrong or right) Once we selected the threshold (0.34) that took those costs into account we were able to obtain : a Precision score = 0.66 and Recall score = 0.72
##  Recommendations:
The logistic regression model could be explored further as it did have a high -Out of box- Roc_AUC score = 0.90

Feature selection could be implemented at some stage to reduce dimensionality and allow the model to work with more relevant data as an input. 
Only 9 of the 400+ features had an importance score of over 0.1

Based on the model performance we can go ahead and provide the feature engineer team with the data needed to build a chat box model. The Chat Box will certainly benefit from the results of this model but work can be done to increase the model performance.

Feedback to the team can be provided regarding the most important features according to the model. Specifically 'Page Values', 'Exit Rate' and 'Product Related Duration' among a few others would be worth considering to reverse engineer in pursuit of optimising the website and thus increasing the revenue for 'DataScienceDeals.com'
