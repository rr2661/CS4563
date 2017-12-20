# CS4563 - Final Project

### Problem Formulation
Data:	NYPD Complaint Data 2006- October 2017

Goal: 	To find the risk of being at a certain place and time.

Machine learning problem: 
If a crime is to occur at a certain time and place, what type of crime will it be (assault, robbery, etc.)

Given: Date, Time, Location
Predict: Crime Type (Classification)

Limitations: False complaints, crimes that go unreported, etc.

### Past Solutions
There was challenge issued at https://www.kaggle.com/c/sf-crime for a similar problem. Given date, time, and location information for San Francisco crimes predict the type of crime that occured.

Their metric for success was not with accuracy like my project but with
>log loss = -\frac{1}{N}\sum_{i=1}^N\sum_{j=1}^My_{ij}\log(p_{ij}),

### Solution
[Solution](Crime_Project.ipynb)
Accuracy rate ~20%. Only uses location, date, and time information from past complaints.

### Evaluation

### Presentation
[Presentation](ML_Presentation.pdf)
