# Capstone - Stock Price Predictor using Twitter (Trump's tweets) Sentiment Analysis

## Background & Problem Statement

<b> Social media: Twitter</b>

In this contemporary era, the use of social media has reached unprecedented levels. On social media, the information about public feelings has become abundant and has transformed to a preferred platform by many to share public emotions about any topic, which has had a significant impact on overall public opinion. Being in our generation where social media is highly integrated in our lives, hence I wanted to explore social media (specifically Twitter) as the medium for news (instead from the traditional news agencies) sentiment. 

Among all social media, Twitter is a popular micro-blogging application that allows users to follow, comment other user’s thoughts or/and share short messages in real time about events or express their own opinion. More than million users post over 140 million tweets every day. This situation makes Twitter like a corpus with valuable data for researchers. Each tweet is of 140 characters long and speaks public opinion on a topic concisely. The information exploited from tweets are very useful for making predictions. Sentiment analysis of twitter data and sentiment classification is the task of judging opinion in a piece of text as positive, negative or neutral. Sentiment analysis of the collected tweets can then be used for prediction model for finding and analysing correlation between contents of news articles and stock prices and then making predictions for future prices will be developed by using machine learning.

Previous research has shown that tweets posted on their personal twitter account from a prominent figure like the President of the United States (i.e. Donald Trump who currently has 77.8m followers), Tesla founder Elon Musk (who currently has 33.2m followers) and current UK Prime Minister Boris Johnson (who currently has 2.4m followers) are able to influence investor confidence and may be useful as a signal for traders. For this project, I have decided to analyse President Trump’s tweets specifically as he has one of the highest number of followers amongst these prominent figures. 

<b> Stock market: S&P500 Index </b>

To measure the effect these tweets have on stock market returns, I have decided to use the S&P500 Index (a weighted average of the 500 leading and largest companies trading on the US stock exchange, with over USD 7.8 trillion benchmarked to the index) specifically, as the S&P500 Index is commonly used as a measure of the general level of stock prices, as it includes both growth stocks and value stocks. Also, the S&P500 Index is generally regarded as the best single measure of large-cap U.S. equities, which will be relevant as Donald Trump is the President of the U.S. Additionally, the S&P500 index captures around 80% coverage of available market capitalisation and a history of information since it began on March 4, 1957. Technology has allowed the index to be calculated and disseminated in real time. 

<b> The Efficient Market Hypothesis</b>

In a broad sense, traders and portfolio managers make decisions on whether to buy, sell or hold specific equities (shares of a company) based on the fundamentals of the firm, its management, and expected value in the future. It is therefore essential to keep up with company news, which may involve earnings calls, new product announcements, and in recent times, news delivered by tweets. 

This ties in with an idea called the Efficient Market Hypothesis (EMH). The EMH maintains that shares trade at their intrinsic value on stock exchanges i.e. all information about a company, its management, and its valuation are continuously expressed in the current share price. This implies that when Trump tweets, this information will be reflected in financial markets even before it hits headlines. 

<b> Problem statement </b>

Therefore, this project analyses the effectiveness of using President Trump’s tweets as a signal for predicting changes (rise / fall / stays the same) in S&P500 prices. 

Social media makes the spreading of news faster and broader, but at the same time, brings volatility to the stock market. Making predictions on the news events and react quickly gives comparative advantage in making more profits or reduce losses. Therefore, in this project, I try to understand and predict the impact of a very unique kind of news, tweets from President Trump, which has become the most uncertainty in the market. I try to model the market’s reaction to his tweets sentiment in the short term using machine learning.

To analyse the effectiveness of using President Trump’s tweets as a signal for predicting changes (rise / fall / stays the same) in S&P500 prices in the short term, the following models were performed:
- Linear regression;
- Long Short Term Memory Recurrent Neural Network(LSTM) and;
- Classification models (Naives Bayes)

## Executive Summary

The challenge of this project is to accurately predict the future closing value of a given stock across a given period of time in the future. 

For this project I explored the use of various machine learning methods to predict the closing price of the S&P 500 Index using a dataset of past prices based on closing price of the Trump Twitter Index. 

### Data Collection & Cleaning & Exploratory Data Analysis
1. Data Collection 
 - President Trump’s tweets (excluding retweets by him) were collected Jan 20 2017 (Trump sworn in as the President of U.S.) to Jan 20, 2020. A total of 13,020 tweets  were collected from [this source](http://www.trumptwitterarchive.com/)
 - S&P 500 Index information for the same period collected from Yahoo! Finance
 
2. Data Cleaning & EDA
 - Clean tweet corpus
    - Handling missing data, if any
 - Natural Language Processing
    - Tokenisation
    - Stop words removal
    - Stemming/Lemmetisation
    
3. Tweet Sentimental Analysis (using VADER) i.e. each tweet was assigned a sentiment score 
 - Sentiment analysis task is very much field specific. Tweets are classified as positive, negative and neutral based on the sentiment present. Tweets are annotated as 1 for Positive, 0 for Neutral and -1 for Negative emotions. 
 - Compute tweet mood and generate data set for stock prediction

### Pre-processing & Modeling & Evaluation
4. Preprocessing/Feature Engineering
 - Generate feature set and data set from processed tweet
    
5. Model (Train and Validate) & Evaluate
 - Predict stock market trend / reaction of the market (rise / fall / stays the same) over a certain time after Trump makes a tweet (using tweet sentiment analysis) using different models:
    - Linear Regression
    - LSTM
    - Classification model (Naives Bayes and Logistic Regression)

### Conclusions and Recommendations
Finally, recommendations and limitations were discussed.

# Data Dictionary
| Feature           | Type   | Description                       |
| ----------------- | ------ | --------------------------------- |
| **source**        | object | Source of tweet posted            |
| **text**          | object | Tweet post                        |
| **created_at**    | object | Date of tweet created             |
| **retweet_count** | int64  | Number of re-tweet counts         |
| **favorite_count**| int64  | Number of likes counts            |
| **is_retweet**    | object | Check to see if tweet was retweet |
| **id_str**        | int64  | Tweet ID                          |
| **Date**          | object | Date                              |
| **High**          | float  | S&P500 Daily Highest Price        |
| **Low**           | float  | S&P500 Daily Lowest Price         |
| **Open**          | float  | S&P500 Daily Opening Price        |
| **Close**         | float  | S&P500 Daily Closing Price        |
| **Volume**        | int64  | S&P500 Daily Volume               |
| **Adj Close**     | float  | S&P500 Daily Adjusted Close Price |

# Directory Structure
```
Capstone
|__ codes
|   |__ 1_Problem Statement.ipynb
|   |__ 2.1_Data Cleaning_Trump Tweets.ipynb
|   |__ 2.2_Prepocessing_Combined_Data_Trump Index.ipynb
|   |__ 3.1_Model_Linear Regression.ipynb
|   |__ 3.2_Model_ARIMA.ipynb
|   |__ 3.3_Model_LSTM.ipynb
|   |__ 3.4a_Model_Classification.ipynb
|   |__ 3.4b_Unseen_data.ipynb
|   |__ 4_Evaluation & Limitations.ipynb
|__ datasets
|   |__ trading
|   |__ |__SP500.csv
|   |__ tweets
|   |__ |__cleaned_tweets.csv
|   |__ |__cleaned_tweets_sum_df.csv
|   |__ |__combined_trump_index.csv
|   |__ |__Trump Tweets 20.01.2017_20.01.2020.csv
|   |__ unseen
|   |__ |__combined_unseen.csv
|   |__ |__SP500_unseen_data.csv
|   |__ |__tweets_unseen_data_part1.csv
|   |__ |__tweets_unseen_data_part2.csv
|__ presentation.pdf
|__ README.md
```






