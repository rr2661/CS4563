# CS4563 - Final Project

## Table of Contents  
* [Problem Formulation](#problem-formulation)
* [Past Solutions](#past-solutions)
* [Solution](#solution)
* [Evaluation](#evaluation)
* [Presentation](#presentation)


### Problem Formulation
Data:	NYPD Complaint Data 2006 - October 2017

Goal: 	To find the risk of being at a certain place and time.

Machine learning problem: 
If a crime is to occur at a certain time and place, what type of crime will it be (assault, robbery, etc.)

* Given: Date, Time, Location
* Predict: Crime Type (Classification)

Limitations: False complaints, crimes that go unreported, etc.

### Past Solutions

There was a challenge issued at https://www.kaggle.com/c/sf-crime for a similar problem. Given date, time, and location information for San Francisco crimes the challenge is to predict the type of crime that occurred.

Their metric for success was the 'multi-class logarithmic loss'. This takes a list of probabilities for a classification and punishes the wrong ones. I used a hard classifier and computed the accuracy of the classifications. This makes it hard to compare results. Even still, their challenge inspired a lot of people to act on the same problem which leads to the sources below.

I have found two sources that performed the same problem and returned their accuracy:

* https://www.kaggle.com/nitinvijay23/predict-the-crime-category-knn-logistic/notebook
This source used the 'K-nearest neighbor algorithm' to receive an accuracy of 22.7%.

* http://cs229.stanford.edu/proj2015/254_report.pdf
This source was not part of that competitions but did act on the very same problem as the competition. They tried a number of different tests (many not learned in this class), cross referenced other data, and got an accuracy of 39%.

Both sources had ~30 classes.

### Solution
[Notebook](Crime_Project.ipynb)

(Code in part 3 is heavily derived from lab 6)

Data for 2006-2017: 5 million records.

Data for this year: 300,000 records.

Solution used SVM Classification. Due to time constraints it was only run on 20% of this years data, which is around 70,000 records.

Project Information:
* Accuracy rate ~20%. 
* Around 80 classes (Types of crime)
* Uses location, date, and time information from past complaints.

### Evaluation

Given the accuracy rate of past solutions, the accuracy of this project may be acceptable. It is worth noting that they had considerably less classes, so it would probably be beneficial to condense the amount of classes. By combining similar classes together, one can get a higher accuracy with a slight loss to classification specificity.

Note: This project used NYC data, the other sources used SF data.

In hindsight:
- I should have built this project on top of one of those SF solutions so that I take theirs further and ultimately hit a higher classification rate.
- I should have condensed my classes down into a more manageable amount (This would be manual and would take some time). Looking at the confusion matrix you can see that certain classes are magnets for misclassification. If we reduced the amount of classes that would reduce the misclassification rate and it would also allow us to look at misclassification trends.
  - Why are violent crimes misclassified as theft a lot?
 -> Misclassification commonly occurs in this region -> Further improvement.
- I should have run the classification on the whole dataset (Takes over 14 hours). This would allow for a higher classification rate as the following would detected:
  - Monthly trends
  - Seasonal trends
  - More data on area trends
- Maybe I should have started this project on the SF data. The NY data was not very clean and was ripe with typos and nans in weird areas. Looking at past solutions, the SF data seems to be cleaner and there were more results to compare to. If I had used the SF data instead I could have spent less time cleaning the data and more time predicting and analyzing results

### Presentation
[Presentation given in class.](ML_Presentation.pdf)

Notes: The reason for many of the flaws in this project is because of a misunderstanding I had with one of the features I used. As shown in the third slide, I had confused the column 'PD_CD' for the code for the police department the complaint was made to when it was really just another code for the crime type. When I first attempted this project, I was incorrectly getting high accuracies. This lead me to believe that my project was successful and did not need any improvement. It was not until further inspection that I realized that this feature was throwing off my results. Had I not done this I would have implemented some of the things listed in "In hindsight"

To clarify: PD_CD is a more granular version of crime type. If you try to predict crime type with a more specific version of crime type as a feature then the classifier with just use that feature and get a high accuracy every time. You are teaching the classifier about the mapping between say violent crimes and assault 2 instead of teaching it about the mapping between date, time, location and violent crimes.
