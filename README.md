# Challenge 17 - Credit Risk Analysis
## Overview of the Analysis
The following report employs different techniques to train and evaluate models with unbalanced classes to determine credit risk.

Libraries Used:
* scikit-learn
* imbalanced-learn

## Deliverable 1 - Use Resampling Models to Predict Credit Risk
For this Deliverable 1, three (3) machine learning models were used to resample the data to improve the model for predicting credit risk. Prior to determining the Basline Model, the preprocessing steps were taken to clean the data. Null values were removed, interest rates were turned into float datatypes, and various data values were labeled. Unnecessary data that only had one value were removed. New columns were created to convert object datatypes into binary columns. Finally the data was scaled to using StandardScaler() to maintain a mean of 0 and a deviation of 1.

* Original Data is extrmely "unbalanced", with only 0.50% of the data represents "high-risk" loans.
</br>low_risk     68470
</br>high_risk      347

* After traiing, testing and spliting the model, our "y_train" shows 0.48% of the data represents "high-risk" loans.
</br>low_risk     51366
</br>high_risk      246

### Baseline Model
Using LogisticsRegressions, the baseline model shows an accuracy score of 99.5% for identifying "low-risk" loans.

![Basline Confusion Matrix Display](Images/basline_confusion_matrix.png)

The Baseline Classification Report shows a very low F1 Score of 33% for identifying high-risk loans, verses 100% for low-risk loans.

![Basline Classification Report](Images/Baseline_Classification_Rpt.png)

### Baseline Imbalanced Classification Report
Based on the Baseline Model, there is a need to try Oversampling in order to create a more balanced and improved model.

![Basline Imbalance Classification Report](Images/Baseline_Imbalanced_Classification_Rpt.png)

### RandomOverSampler Technique
THe Balance Accuracy Socre was 83.25%. 

![RandomOverSampler Confusion Matrix Display](Images/RandomOverSampler_confusion_matrix.png)

This technique deteriorated the model, reducing the F1 score for both high-risk and low-risk accuracy.

![RandomOverSampler  Imbalance Classification Report](Images/RandomOversampler_Rpt.png)

### SMOTE Oversampling Technique
Using IMBLearn's synthetic minority oversampling technique (SMOTE) approach, this technique produced a model with a Balanced Accuracy Score of 84.41%. 

![SMOTE Confusion Matrix Display](Images/SMOTE_confusion_matrix.png)

![SMOTE  Imbalance Classification Report](Images/SMOTE_Oversampling_Rpt.png)

### Cluster Centroids Undersampling Technique
Similar to the SMOTE approach, Cluster Centroid undersampling technique produced a model that was 82.04% accurate. 

![Cluster Centroids Confusion Matrix Display](Images/ClusterCentroids_under_confusion_matrix.png)

![Cluster Centroids  Imbalance Classification Report](Images/ClusterCentroids_Undersampling_Rpt.png)

## Deliverable 2 - Use the SMOTEENN algorithm to Predict Credit Risk
Oversampling and Undersampling did not seem to produce a viable model to accurately predict high-risk. A combinatorial approach such as SMOTE and Edited Nearest Neighbors (ENN) aka SMOTEENN was used. 

The approached produced a Balanced Accuracy Score of 84.40%.

![Cluster Centroids Confusion Matrix Display](Images/SMOTEENN_confusion_matrix.png)

![Cluster Centroids  Imbalance Classification Report](Images/SMOTEENN_Classification_Rpt.png)

## Deliverable 3 - Use Ensemble Classifiers to Predict Credit Risk

### Balanced Random Forest Classifier
The Balanced Accuracy Socre for the Random Forest approach was 75.89%

![Random Forest Classifier Confusion Matrix Display](Images/RandomForestEnsemble_confusion_matrix.png)

![Random Forest Classifier  Imbalance Classification Report](Images/Forest_Rpt.png)

### Balanced Random Forest Classifier
The Balanced Accuracy Socre for the Random Forest approach was 75.89%

![Random Forest Classifier Confusion Matrix Display](Images/RandomForestEnsemble_confusion_matrix.png)

![Random Forest Classifier  Imbalance Classification Report](Images/Forest_Rpt.png)

The top 5 features of importance and bottom 5 features of least importance are as follows. The features of lease important should be removed from the model.

![List of top and bottom features](Images/features.PNG)

### Easy Ensemble AdaBoost Classifier
The Balanced Accuracy Socre for the Easy Ensemble AdaBoost approach was 93.19%

![Easy Ensemble AdaBoost Classifier Confusion Matrix Display](Images/AdaBoostEnsemble_confusion_matrix.png)

![Easy Ensemble AdaBoost Classifier  Imbalance Classification Report](Images/AdaBoost_Rpt.png)

## Summary
None of the techniques performed above helped to improved the accuracy for identifying high-risk loans. The highest F1 Score came from the Easy Ensemble AdaBoost Classifer with a score of 0.16 Unforunately, this is still not adequate. All the other resampling models did poorly with 0.06 or less.