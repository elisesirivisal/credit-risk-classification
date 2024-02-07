# Module 20 Report: Credit Risk Classification

## Overview
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).


In this analysis, we are exploring loan data, which comes with data on each loan's size, the interest rate, borrower income, debt to income, number of accounts, deragatory marks, total debt, and finally the loan status - whether healthy or high-risk. In this, we are reading in the data to train a logistic regression model to predict the loan status of said loan, based on other factors given in the data.
<br><br>
After importing our raw data, our variables were first separated as "y" vs "X" with our "y" values as "loan_status" (ie. healthy status - 0 or high-risk status - 1) and our X-values as all the rest of the data columns. The data is then split into train and test X and y values- a total of 4 variables to work with: X_train, y_train, X_test, y_test. A logistic regression model is created and fitted with the training X and y values, which we can then use to create predictions using the X test values. By comparing these results to the "actual" y-test results, we can get a balanced accuracy score of how much of our data was predicted correctly. In the LogisticRegression function, the program will be able to figure out the "best-fit line" that would allow the program to predict if a loan's status is healthy of high-risk.
<br><br>
In a second logistic regressional model fitted to random over-sampled data, such that the number of data for healthy loans and high-risk loans are equal, the same streps would be repeated to train the model to predict the healthy vs high-risk loans.

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Balanced Accuracy Score : 0.9696852964585789
	* Precision: 1 - 1.00, 0 - 0.85
	* Recall:    1 - 0.99, 0 - 0.95
 and Recall scores.

* Machine Learning Model 2:
  * Balanced Accuracy Score : 0.9946686570347071
	* Precision: 1 - 0.99, 0 - 0.99
	* Recall:    1 - 0.99, 0 - 0.99

## Summary

In the initial stage of training the data, the "value_counts" variable were not balanced, leaving the number of healthy loans at 75036 and high-risk loans at 2500. That is, there was more data to train the model to predict the healthy loans versus the high-risk loans, so the accuracy of the model to be able to predict if a loan was high-risk was lower. Though later, the data will be resampled to have an equal number of values for healthy and high-risk loans (56271 each) to create a better foundation to train our logistic regression model, and thus a more accurate model to predict loan status.
<br><br>
Taking a closer look at the classification report and balanced accuracy score, we are able to see the effect of using the random over sampler on the accuracy of the program to correctly predict a healthy loan versus a high-risk loan. Before the random over sampler was used, the precision for predicting a healthy loan was 100%, and high-risk loans was 85%. The balanced accuracy score was approximately 96%. The logisitic regressional model 1 was able to predict the loans quite well, though not very reliable in predicting high-risk loans.
<br><br>
After using the random over sampler, precision for predicting bot healthy and high-risk loans was 99%, while the balanced accuracy score rose to approximately 99%. Thus, the second logistic regression model is able to predict both the healthy loan (0) and high-risk loans (1) reliably. Though accuracy of predicting the healthy loans decreased by 1%, the precision of predicting a high-risk loan was able to increase by about 14% - a significant improvement.
<br><br>
In this case,  the second model that used the random over-sampled data was more reliable in terms of being able to correctly predict the status of a given loan, leveling a 99% accuracy score for predicting the loan status. Without the random over-sampeld data, the first model was able to predict the healthy loans 100% of the time, but had a slightly lower score of 95% for predicting the high-risk loans. In this case, it would be more important to predict the `1`'s since with greater risk comes greater losses, should a "high-risk loan" be classified as a  "healthy loan". If a loan is incorrectly predicted as healthy, loss of about 3x the amount of the original loan could be lost in the process as stated by the American Bankers Association.
- "... every dollar of fraud now costs banks and credit unions roughly $2.92 ..."(https://www.cutimes.com/2018/09/27/fis-spending-2-92-for-every-dollar-of-fraud-in-201/?slreturn=20230220122458#:~:text=Every%20dollar%20of%20fraud%20now,data%20from%20LexisNexis%20Risk%20Solutions.)
