# In Progress
## CS4563 - Final Project

### Problem Formulation
Data:	NYPD Complaint Data 2006 - October 2017

Goal: 	To find the risk of being at a certain place and time.

Machine learning problem: 
If a crime is to occur at a certain time and place, what type of crime will it be (assault, robbery, etc.)

* Given: Date, Time, Location
* Predict: Crime Type (Classification)

Limitations: False complaints, crimes that go unreported, etc.

### Past Solutions
There was a challenge issued at https://www.kaggle.com/c/sf-crime for a similar problem. Given date, time, and location information for San Francisco crimes predict the type of crime that occured.

Their metric for success was not with accuracy like my project but with the 'multi-class logarithmic loss'. This takes a list of probabilities for a classification and punishes the wrong ones. I used a hard classifier which makes it hard to compare results.

I have found two sources that performed the same problem and returned their accuracy:

* https://www.kaggle.com/nitinvijay23/predict-the-crime-category-knn-logistic/notebook
This source used the 'K-nearest neighbor algorithm' to receive an accuracy of 22.7%.

* http://cs229.stanford.edu/proj2015/254_report.pdf
This source was not part of that competitions but did act on the very same problem as the competition. They tried a number of different tests (many not learned in this class), cross referenced other data, and got an accuracy of 39%.

Both sources had ~30 classes.

### Solution
[Solution](Crime_Project.ipynb)

Data for 2006-2017: 5 million records.

Data for this year: 300,000 records.

Solution used SVM Classification. Due to time constraints it was only run on 20% of this years data, which is around 70,000 records.

Accuracy rate ~20%. 

Around 80 classes (Types of crime)

Only uses location, date, and time information from past complaints.


### Evaluation

Given the accuracy rate of past solutions this accuracy might be acceptable. It is worth noting that they had considerably less classes so it would probably be benefitial to condense the amount of classes. By combining similar classes together one can get a higher accuracy with a slight loss to classification specificity.

Note: This project used NY data, the other sources used SF data.

In hindsight:
- I should have built this project on top of one of those SF solutions so that I take theirs further and ultimately hit a higher classfication rate.
- I should have condensed my classes down into a more manageable amount. Looking at the confusion matrix you can see that certain classes are magnets for misclassification. If we reduced the amount of classes that would reduce the misclassification and it would also allow us to look at misclassification trends.
* Like why are violent crimes misclassified as theft a lot?
 -> Misclassification commonly occurs in this region -> Further improvement.

### Presentation
[Presentation](ML_Presentation.pdf)
