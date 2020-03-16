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
The first baseline Decision Tree model provided a low -insert evaluation - score.
Very small improvements were made using a combinatory hyperparameter optimisation.

A logistic Regression model performed much better giving a roc_auc score of 0.89.
Random Forest ensemble began with a roc_auc score of 0.89 but was increased to 0.93 using hyperparameter optimisation through Random and Grid Search CV.

##  Conclusions:
There was a slight increase in model performance when using ensemble models (Random Forest) over Logistic Regression. 
The Grid Search Parameter optimsation was paramount in obtaining the highest roc_auc score in our random forest model

A Key component of our model was incoroporating the costs (penalties for getting predictions wrong or right)
Once we selected the threshold (0.43) that took those costs into account we were able to obtain :  a Precision score = 0.7 and Recall score = 0.63

##  Recommendations:
Based on the model performance we can go ahead and provide the feature engineer team with the data needed to build a chat box model. The Chat Box will certainly benefit from the results of this model but work can be done to increase the model performance.
