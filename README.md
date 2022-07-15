# Bankruptcy-Prediction

Predicting Bankruptcy Of Polish Companies Using Machine Learning
Project description
The notebook uses multiple machine learning algortithms such as Logistic regression, random forest, XG boost, support vector machines, etc. to predict the bankruptcy of Polish companies based on financial predictors. The data was collected for the period 2007-2013 and credits go to Emerging Markets Information Service and Sebastian Tomczak from Department of Operations Research, Wroclaw University, Poland. The dataset contains all the financial features (all are numerical in nature) of the polish companies and the feature descriptions can be found in the link provided. The problem type is a binary class classification and each instance belongs to either bankrupt ('class 1') or Non-Bankrupt (calss 0).

The flow of the project follows 3 experimental settings and is as below:

- Reading the data in arff files.
- Target variable distribution analysis .
- Basic data exploration.
- Missing values treatment.
- Sampling (SMOTE & random), scaling and K-fold cross validation.
- Application of multiple classification algorithms based on different time horizons.
- Comparision of Recall scores on testing datasets.
- Result discussion.
Notebook runtime:
Dataset link : https://archive.ics.uci.edu/ml/datasets/Polish+companies+bankruptcy+data#
