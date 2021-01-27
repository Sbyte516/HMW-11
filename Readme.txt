Balanced Random Forest Classifier:

The model tends to favor the low risk data making this an exaample of overfitting as the precision would show it predicts these values 100% of the time, which determines the data is imbalanced, and would require more data to for the values that were high risk to be generated, making this a problem of class imbalance.

When looking at the value counts for the y variable we can see the low risk heavily outweighs the high risk class. 
low_risk     51352
high_risk      260
Name: loan_status, dtype: int64

Accuracy:0.66

66% of the time the model makes accurate predictions.
(TP+TN)/total

array([[   29,    58],
       [   11, 17107]], dtype=int64)
The confusion matrix reveals the True Positives (17107), False positives (58), True Negatives (29), and False Negatives (11)


                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.72      0.33      1.00      0.46      0.58      0.31        87
   low_risk       1.00      1.00      0.33      1.00      0.58      0.36     17118

avg / total       1.00      1.00      0.34      1.00      0.58      0.36     17205

Most important features:
(0.07739539556196139, 'total_rec_int'),
(0.07493064532483105, 'total_rec_prncp'),
(0.07254881456165256, 'last_pymnt_amnt'),



Easy Ensemble Classifier:

Accuracy: 0.92
Accuracy score is 92% for this model, but overall classification report is identical for all features, this model seems to do better when making predictions for the False Negatives, but gives a recall of 72% for high risk predictions.   

array([[   79,     8],
       [  906, 16212]], dtype=int64)
         

		 pre       rec       spe        f1       geo       iba       sup

  high_risk       0.72      0.33      1.00      0.46      0.58      0.31        87
   low_risk       1.00      1.00      0.33      1.00      0.58      0.36     17118

avg / total       1.00      1.00      0.34      1.00      0.58      0.36     17205


Naive Random Oversampling:

This is done by oversampling of the minority group of the data, while duplicating the set, although this does give us a more balanced data set this does not give the model the necessary preditcion we are aiming for. Accuracy is low being 64%, a prefered score would be in the 80% range. The issue of overfit data is present as the precision for low list is 100% and the high_risk is 10%.

Accucracy : 0.64




		pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.63      0.67      0.02      0.65      0.42        87
   low_risk       1.00      0.67      0.63      0.80      0.65      0.42     17118

avg / total       0.99      0.67      0.63      0.80      0.65      0.42     17205


SMOTE:
This model creates sythetic examples the from the minority. The examples are created from the original data. This method of data augmentation can be useful when there are too few examples of the minority class. SMOTE uses K nearest neighbors when chossing examples from the minority class.In after adding the examples to the minority we see the values are now equal. 

high_risk    51352
low_risk     51352
Name: loan_status, dtype: int64

Accuracy: 0.64

array([[   53,    34],
       [ 5774, 11344]], dtype=int64)

A total of 17,205 predictions 64% were correct, the models misclassfication rate was 33%. this is how often the model was wrong.
Misclassification Rate:(FP+FN)/total  

      		   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.63      0.67      0.02      0.65      0.42        87
   low_risk       1.00      0.67      0.63      0.80      0.65      0.42     17118

avg / total       0.99      0.67      0.63      0.80      0.65      0.42     17205

                   
Undersampling:

The Undersampling Cluster Centroids samples the  majority class by replacing a cluster of a majority samples by the cluster centroid of a k means algorithim. The model shows the majority data is now equal to the minority. Accuracy is 51%, our predictions are wrong 49% of the time. Recall is less 
accurate in this model 40% for the low_risk data,this is a less accuracte model. 

low_risk     260
high_risk    260
Name: loan_status, dtype: int64


  high_risk       0.01      0.63      0.40      0.01      0.50      0.26        87
   low_risk       1.00      0.40      0.63      0.57      0.50      0.24     17118

avg / total       0.99      0.40      0.63      0.56      0.50      0.24     17205



SMOTE ENN:

SMOTE can be combined with many different undersampling techniques. SOMTEEN uses a rule involving using k=3 nearest neighbors to locate examples in a dataset that are misclassified and removes them. Regatrding SMOTEEN this is considered more agressive at down sampling the majority class, provding more in-depth cleaning. 

Insight 

I conclude the models in all occasions did not perform as desired, the low accuracy, overfitting and a poor abaility to predict False negatives, I would not recommend the models, and would to try a different strategy and approach in order to obtain the desired results. 