# Capstone: Sentiment Analysis of Airline Tweets 

### Introduction

Sentiment analysis is the interpretation and classification of emotions within text. Businesses today rely heavily on data and sentiment analysis enables them to identify customer sentiment towards their brands or services. Recent statistics have also shown that social media has become a huge part of people's lives; with the average time spent on social media worldwide amounting to 144 minutes per day in 2019. Data on social media is largely unstructured and can be time-consuming to sieve through. The use of sentiment analysis can help businesses to analyse customer feedback to better tailor services to meet their needs. 

In this project, we will make use of the tweets collected on 6 major US airlines in Feb 2015 to develop a model that predicts the sentiment of the text so as to enable businesses to better target their responses to customers feedback. 

### Problem Statement 

How can airlines exploit twitter data to better respond to customer’s needs? 

### About The Data

The [data](https://www.kaggle.com/crowdflower/twitter-airline-sentiment) is obtained from kaggle. Unstructured data from sources such as Twitter pose challenges where users are free to express themselves using short forms and emoticons as such the main challenge is to process the data. In the coming segment, we will analysis some of the techniques used. 

### EDA, Cleaning and Pre-processing

##### General Approach for ML models: 

1. Convert text to lowercase 
2. Removal of weblinks, tags and parses
3. Emoji was converted to text using the emoji library. As seen during the EDA, some of the top words that came out were actually emojis and it would be valuable to retain the meaning 
4. Tokeniser, Lemmatizer and Porter Stemmer were use
5. The tweets were cleaned differently with one set removing stopwords while the other retaining stopwords to see if it will impact the model's performance

##### Some Findings:

<u>More Tweets were Labelled as Negative</u>

- Amongst all the tweets, 62% of the tweets were labelled negative. It can imply that people tend to tweet more when they have a negative review.

<u>Incorrect Tagging of Original Dataset</u>

- Out of the 2222 tweets labelled as Delta, all of the tweets carried the tag @JetBlue/@jetblue. As such it could be a possible mislabeling. The implications are not large in this case as we know that all the Delta tags actually refer to JetBlue.

<u>Types of Customer Feedback</u>

- Some customers make use of twitter to communicate back and forth with the airline. In one instance, the same user had 32 tweets over a span of 8 days on flight related queries.
- Some tweets can be classified as spam since they were asking for the airlines to 'follow them'.
- Some tweets were posts related to the latest news regarding the airline.

### Feature Engineering

##### <u>Airline as a feature</u>

Airline was included as a feature during one of the simulations to see if the model performance will improve. 

### Modeling: To Determine Sentiment of Tweet

##### General Approach: 

1. The baseline accuracy was 62% (percent of negative tweets). The observations were classified into negative (class 0), neutral (class 1) and positive (class 2)

2. Train-test-split will be applied on train set for model validation and selection. 

3. The following models were used: 

   ​		a) Logistic Regression 

   ​		b) Naive Bayes 

   ​		c) Decision Tree

   ​		d) Random Forest Classifier 

   ​        e) Ada Boost 
   
   ​        f) Gradient Boost 
   
   ​        g) XG Boost 
   
   ​        h) RNN 
   
   ​        i) RNN with LSTM 
   
   ​        j) RNN with LSTM and Dropout Layer

##### Metric Used to Validate Models:

- Mean Accuracy Score of Model

##### Findings:

1. Logistic Regression (LR) Model performed the best and was selected. 
2. The inclusion of stopwords helped to improve model accuracy by 2%.
3. Using airline as a feature did not help to improve the score. 
4. As the classes were unbalanced, the use of balanced class weights did not help to improve the Logistic Regression Model. 
5. The performance of the RNN models were comparable to the ML models and hence I decided to focus on further data cleaning to improve the LR model.
6. Looking at the metrics for the individual classes, the LR model has the poorest performance on neutral posts, only being able to accurately classify the neutral posts 58.5% of the time (recall). Future work would be to increase the positive and neutral scores to get a more balanced dataset and to see if scores can be improved. 

| Model                    | Accuracy Score |
| ------------------------ | -------------- |
| Logistic Regression      | 0\.801         |
| Multinomial Naive Bayes  | 0\.748         |
| Decision Tree            | 0\.681         |
| Random Forest Classifier | 0\.761         |
| Ada Boost                | 0.755          |
| Gradient Boost           | 0.751          |
| XG Boost                 | 0.774          |

### Conclusion & Recommendations

1. The model is able to accurately classify 80.1% of the tweets according to sentiment. As the model is only developed based on 14,000 observations, there is a need to train the model on a larger dataset for deployment. 

2. The model currently performs well on negative tweets which is a priority as businesses would tend to prioritize responses to negative feedback. Future work includes gathering more tweets that have positive and neutral tags to see how the model performs with a more balanced dataset. 

3. During the EDA, it can be seen that some tweets constitutes spam and to further support deployment, a classifier for spam tweets can be introduced to help filter out spam messages that need not tax the sentiment analysis model. 

4. Understanding and responding to customer feedback is multi-faceted. The above sentiment analysis model helps businesses to respond to negative tweets to mitigate the negative experiences. Future work can include topic analysis of the tweets to help businesses identify the common topics or themes that arise in customer feedback so that they can understand what is being done well and to identify areas for improvement. 

   
