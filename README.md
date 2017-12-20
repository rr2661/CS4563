# CS4563 - Final Project

### Problem Formulation
Data:	NYPD Complaint Data 2006- October 2017

Goal: 	To find the risk of being at a certain place and time.

Machine learning problem: 
If a crime is to occur at a certain time and place, what type of crime will it be (assault, robbery, etc.)

* Given: Date, Time, Location
* Predict: Crime Type (Classification)

Limitations: False complaints, crimes that go unreported, etc.

### Past Solutions
There was challenge issued at https://www.kaggle.com/c/sf-crime for a similar problem. Given date, time, and location information for San Francisco crimes predict the type of crime that occured.

Their metric for success was not with accuracy like my project but with the 'multi-class logarithmic loss'. This take a list of probabilities for a classification and punishes the wrong ones. I used a hard classifier which makes it hard to compare results.

I have found two sources that performed the same problem and returned their accuracy.
* https://www.kaggle.com/nitinvijay23/predict-the-crime-category-knn-logistic/notebook

This source used the 'K-nearest neighbor algorithm' to recieve an accuracy of 27%.
* http://cs229.stanford.edu/proj2015/254_report.pdf

This source was not part of that competitions but did act on the same problem. They tried a number or different test and cross referenced other data and got an accuracy of 39%.


### Solution
[Solution](Crime_Project.ipynb)
Accuracy rate ~20%. Only uses location, date, and time information from past complaints.

### Evaluation

### Presentation
[Presentation](ML_Presentation.pdf)
