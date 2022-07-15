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
<br>
Notebook runtime:
<br>
Dataset link : https://archive.ics.uci.edu/ml/datasets/Polish+companies+bankruptcy+data#


## Result Discussion

The dataset has large number of target class as Non-Bankrupt companies and very few companies going bankrupt each year. This resulted in an imbalanced dataset on whihc all of the algorithms struggled to perform.

1. **Train & Test Splitting**: 80/20 split was done before undertaking any kind of data transformations to avoid data leakage.
2. **Missing value analysis**: Features with missing value % more than 10% was dropped and imputations were done based on 'mean' strategy.
3. **Sampling**: Two sampling methods experimented were - SMOTE & Randomoversampling whihc generated sysnthetic minority class instances. The models performed better except for RF on the over sampled datasets across all prediction horizons (1 yr and 5 yr and all data).
4. **Rescaling**: Features had different scale and since some of the algorithms used distance based metrics for classification, min-max scaler was used to scale the data across features.
5. **Modelling**: 5 models were used such as Logistic regression, SVM (linear & RBF kernels), random forest, XG boost and adaptive boosting. Hyperparameter tuning was carried over using Gridsearch methodology. The best parameters were noted down and later replaced in the models for faster replication. 10-Fold crossvalidation was also used while training and models were evaluated based on their Recall scores for each of the 3 experimental settings - Year 1 data, Year 5 data and with all the data at once.

6. **Evaluation**: Since we have an imbalanced data set, all models gave high accuracy, but performed poor when predicting a ‘class 1'. Prediction of bankrupt(positive class) companies has more weight than wrongly predicting companies as bankrupt, hence **Recall**(True positive or sensitivity) metric was selected for visualization. Gradient boosting and random forest methods have performed best on original data (with class imbalance present) however on the oversampled data, LR and SVM had comparable recall. The performance of the models degraded when all the 5 years data was considered in comparision with just taking the 2011 year data.

7. **Challenges**: Support vector machines run time was very long on the concatenated dataset and it's oversampled version (> 44,000 instances) and this is becasue the training complexity of SVM is tied with the number of instances the dataset has. SVM kernels calculate distance between each point in the dataset and this is why it is not suggested to use SVMs for large datasets and hence they were omitted for the experimental setting 3.
It is not possible to accurately learn which company is performing poorly financially as there is no feature to identify any particular company to analyze it over the 5 year period. As mentioned in Feng Mai et al. 2019 and Theil et al. 2019 that leveraging natural language components such as earnings calls and yearly performance reports of companies can improve the models' predeiction performacne[**Reference below**]. Hence the dataset is limited to application of traditional ML methods in contrast to natural language models such as embedding models and LSTMs.

8. **COnclusion**: Performance of all the algorithms was better when predicting with 1 year time horizon (experiment setting 2) and performed poorly when predicting with 5 years time horizon. Meaning models could not generalize well or predict the bankruptcy for larger time horizons.

9. **Scope for improvment** : Neural networks were not implemented on this dataset which usually show better performance compared with traditional ML methods when there is large amount of data.

**Feng Mai et al. 2019** : https://www.sciencedirect.com/science/article/abs/pii/S0377221718308774
<br>
**Theil et al.2019** : https://www.ijcai.org/proceedings/2019/0724.pdf
