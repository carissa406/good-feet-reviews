# Good Feet Review Analysis; Star Rating Classification
 Analysis of customer reviews from the Good Feet Milwaukee store to predict review score

[Link to Google Reviews of Good Feet Milwaukee](https://www.google.com/search?q=good+feet+milwaukee&rlz=1C1ONGR_enUS943US943&oq=good+feet+milwaukee&aqs=chrome..69i57j46i175i199i512j0i22i30l3j0i390.10964j0j4&sourceid=chrome&ie=UTF-8#lrd=0x88050f83400a8a39:0x37af811d2176cae,1,,,)

[Link to Outscraper](https://outscraper.com/)

[Click to see my progress log](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/log.md)

[Click to see my code](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/Good_Feet_Analysis.Rmd)

# Problem Definition and Goals
The purpose of this analysis is to classify reviews by their star rating given their text review using a Naive Bayes Classifier. This data was scraped from the Good Feet Milwaukee location's Google reviews page using Outscraper. The raw data was then cleaned to only contain the following variables of 121 observations:
- review_ID
- review_text
- review_rating
- review_datetime_utc
- review_likes

# Data Exploration and Preprocessing
The distribution of the review ratings can be shown by the below barplot. To improve the accuracy of the model since we have a small amount of observations, the star ratings were combined into "good" and "bad" ratings. 4 stars and below are considered good, while 3 stars and below are considered bad for these purposes. The next figure shows the combined binary ratings. It is shown that there are much more good ratings than bad ones. 

### Original Barplot of 1-5 Star Ratings

![Original_Review_Rating](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/review_rating_table_barplot.png)

### Modified "Good" and "Bad" Ratings
![Modified_Review_Rating](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/review_rating_good_bad.PNG)

I also took a look at the distribution of the dates of each review by individually plotting the year of review and month of review. It is shown that the majority of reviews were made in 2019 and the month of October in the below figures.

### Review Years
![Review_Year](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/review_year.PNG)

### Review Months
![Review_Month](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/review_month.PNG)

Next the good and bad review frequent words were visualized using the WordCloud package. 

### Good Reviews WordCloud
![Good Reviews WordCloud](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/good_wordcloud.PNG)

### Bad Reviews WordCloud
![Bad Reviews WordCloud](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/bad_wordcloud.PNG)

Before training the Naive Bayes Classifier the data was converted into a text corpus. The corpus was cleaned by converting all words to lowercase, removing all numbers, stopwords, replacing punctuations with spaces, stemming, and striping the remaining white space. The clean corpus was then converted into a document term matrix to get the frequencies of each word. The matrix is very sparse so words that appeared less than five times were also removed. The text was then split into about 80% training and 20% testing data initially, then into 60% and 40% to view any changes. We obtained the best model using 10-fold cross validation and evaluted using AUC/ROC. 

# Data Analysis and Experimental Results

The data was trained using a Naive Bayes Classifier. Below are the initial results before using 10-fold cross validation and with 80/20 training/test data. This model did not do as well with predicting Bad reviews: 

![Initial Results CrossTable](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/crosstab_results.PNG)

Below are the results of the final model using 60/40 training/testing data and using 10-fold cross validation evaluated with ROC. We can see that this model did a better job at classifying bad reviews. 

![Final Model](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/nb_results_cv.PNG)
![Final_CrossTable](https://github.com/carissa406/Good-Feet-Review-Analysis/blob/main/gf_test_labels_results.PNG)
