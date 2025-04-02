# BerkeleyAIML_Practical_3
Berkeley AI/ML Course - Practical 3 - Classifier to model whether customers will subscribe to Term Limit deposit account 

The dataset comes from the UCI Machine Learning repository link. The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns. There is the article accompanying the dataset here for more information on the data and features.

The data has a number of features related to a customer, and some financial macro indicators on the day that a customeris contacted. Also some information about previous contact on the marketing campaign. The business objective is to build a model that will predict whether a customer will subscribe to a term deposit account based on the features. The data indicated that there is an 11.3% success rate.

Doing feature engineering, I got reassigned some unknown values in categorical features. I also dropped the day of the week that a perosn was contacted on, as it did not seem to make much difference. I also basically scored the months of Dec, September and march higher than the other months, as thos 3 months seemd to have a remarkably better success rate than the other months. Finally I also got rid of a macro indicator that seemed to correlate with another one.

Finally I one hot encoded the categorical features, and then scaled the data.

### First Run
I worked out that a baseline for a model would require accuracy of greater than 88%. I then tested the 4 models, and had the following return
           Model  Train Time  Train Accuracy  Test Accuracy  AUC Score
0     LogRegress    0.207999        0.898513       0.895120   0.776760
1            KNN    0.012002        0.912352       0.888201   0.700591
2  Decision Tree    0.391009        0.994871       0.838553   0.625642
3            SVM  167.072834        0.904977       0.898034   0.688228
THey all did better than baseline, but not as good as in original paper, which had AUCof 0.887. Also, it is clear decsion tree was overfitting.

### Second Run
I tried to optimise the data by dropping the campaign data. 
           Model  Train Time  Train Accuracy  Test Accuracy  AUC Score
0     LogRegress    0.146995        0.897845       0.895606   0.776612
1            KNN    0.018000        0.911684       0.888080   0.697407
2  Decision Tree    0.253994        0.987527       0.835397   0.611397
3            SVM  147.808466        0.903338       0.897548   0.691240
THere is a small drop off in AUC score for all the models, except for SVM. However, time taken is reduced so I think it is worth it.

### Third Run
I used a grid search to optimise the parameters. I used gridsearchCV for 3 of the models, but had to use randomised search for the SVM model, as it was taking way to long on my computer. At time of writing this readme, still do not have results.






