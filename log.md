# Good Feet Review Analysis and Classification Log
--- 

5/15/2022
* I started this project as a way to keep up my machine learning skills and to generate independent projects for a work related portfolio.
* Utilized Outscraper to scrape the raw review data from Google Reviews.
* Deleted variables not relevant to my analysis.
* Uploaded some exploratory analysis and the raw data

5/15/2022
* Preparing the data into a Document Term Matrix to be used with a Naive Bayes Classifier
* Trained the Naive Bayes Classifier
* The classifier had a 64% error rate which is too high for my liking. I think I will instead try to combine 4 and 5 star ratings as "good" and 1, 2, and 3 star ratings as bad. 
* I want to utilize the other variables in the data by finding a way to visualize the review dates

5/18/2022
* I visualized the review dates by splitting up the years and months and plotting them individually
* I added the wordclouds
* Added inital crosstable results of my naive bayes model

5/19/2022
* Used 10 fold cross validation on my model using the caret package
* Calculated the ROC instead of Accuracy since the target class is imbalanced

5/21/2022
* I changed the test and training data to about 60/40
