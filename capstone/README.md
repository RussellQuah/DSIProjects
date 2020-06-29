# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project 1: Trump, Tweets and the Stock Market

### Russell Quah, DSI-14 Singapore

## Problem statement

The US market team at a local bank has seen literature on models that are able to predict market movement based on tweets by Donald Trump:
- [JP Morgan creating a 'Volfefe index to track tweets vs bond interest rates](https://www.marketwatch.com/story/are-trump-tweets-influencing-bond-volatility-jp-morgans-volfefe-index-aims-to-find-out-2019-09-09)
- [On days when President Trump tweets a lot, the stock market falls, Bank of America](https://www.cnbc.com/2019/09/03/on-days-when-president-trump-tweets-a-lot-the-stock-market-falls-investment-bank-finds.html)

They have tasked the data science team to build a classification model using Natural Language Processing to predict if Donald Trump's tweets are market moving. The models used are:
- Logistic Regression
- XGBoost
- Long Short Term Memory Neural Network
- Evaluate the models based on:
    - accuracy (% predictions the model gets correct, both a significant movement and a non-significant movement)
    - precision (% predicted significant movement when it is actually significant movement)
    - sensitivity (% predicted significant movement out of all correct predictions)
- choose the best performing model to test it on the holdout csv

## Recommendation to the US market team at the bank
- On days of positive class, Trump tends to tweet more on average
- The model is able to accurately predict when his tweets will not move the market.

## Conclusion and Recommendations
The best model to use would be Countvectorizer into XGBoost, with an accuracy of 0.906 on the holdout dataset.
The best hyperparameters:
- 'cvec__max_df': 0.85,
- 'cvec__max_features': 75,
- 'cvec__min_df': 2,
- 'cvec__ngram_range': (1, 2),
- 'smote__k_neighbors': 5,
- 'smote__sampling_strategy': 'minority',
- 'xgb__colsample_bytree': 1.0,
- 'xgb__gamma': 0.5,
- 'xgb__learning_rate': 0.1,
- 'xgb__max_depth': 13,
- 'xgb__min_child_weight': 1,
- 'xgb__n_estimators': 100,
- 'xgb__objective': 'binary:logistic',
- 'xgb__random_state': 42,
- xgb__subsample': 1.0}

## Limitations

However, the model suffers in terms of precision, correctly predicitng the positive class as the posivite class. More work needs to be done on:
- XGBoost being non-parametric plus the features i engineered are not readable to the lay person
- Feature engineering, a tweet after closing could impact the following day's one.
- Collection of more data on the positive class, or even change the parameters of a positive class
- Try additional an ensemble of machine learning models
- Feed the whole feature set into the neural network
- More work can be done on the LSTM model,from optimisation of hyperparameters to including a timeseries generator
- Additional work can be further done on the topic modelling



### Datasets:
- Tweets from Donald Trump 2009 till June 2020
    - sourced from https://www.kaggle.com/austinreese/trump-tweets
    - 43352 recorded tweets since May 2009
- Historical S&P500 stock price from Yahoo Finance
- Loughran McDonald financial sentiment library
    - sourced from https://sraf.nd.edu/textual-analysis/resources/#Master%20Dictionary

## Data Dictionary
| Feature     	| Type 	| Description|                                                  
|:------------------	|:----------	|:----------------------------------------------------------------------------------|
| content	| object | Raw tweets from therealdonaldtrump |
| date	| object | Date of his tweet. YYYY-MM-DD-HH-MM-SS format |
| retweets	| int64 | Number of retweets by others at the time of data collection |
| favorites	| int64 | Number of favourites at the time of data collection |
| cleaned_tweets | object | Pre-processed tweets |
| tweet_day	| datetime64[ns] | Date of tweet YYYY-MM-DD format |
| month_sin	| float64 | Cycial sin month feature engineered. Range of -1 to 1 |
| month_cos	| float64 | Cycical cosine month feature engineered. Range of -1 to 1 |
| day_sin	| float64 | Cycical sin day feature engineered. Range of -1 to 1 |
| day_cos	| float64 | Cycical cosine day feature engineered. Range of -1 to 1 |
| hour_sin	| float64 | Cycical sin hour feature engineered. Range of -1 to 1 |
| hour_cos	| float64 | Cycical cosine hour feature engineered. Range of -1 to 1 |
| min_sin	| float64 | Cycical sin min feature engineered. Range of -1 to 1 |
| min_cos	| float64 | Cycical cosine min feature engineered. Range of -1 to 1 |
| time_to_open	| float64 | Time before the stock market opens on that day. In seconds | 	
| time_after_close	| float64 | Time after the stock market closes on that day. In seconds |
| potus_status	| int64 | President of the United States status |
| vader_negative	| float64 | Negative sentiment analysis using Vader. Scale of 0 to 1 |
| vader_neutral	| float64 | Neutral sentiment analysis using Vader. Scale of 0 to 1 |
| vader_positive	| float64 | Positive sentiment analysis using Vader. Scale of 0 to 1 |
| vader_compound	| float64 | Overall sentiment analysis using Vader. Scale of 0 to 1 |
| negative_word	| int64 | Negative word count using Loughran McDonald Financial sentiment analysis |
| positive_word	| int64 | Positive word count using Loughran McDonald Financial sentiment analysis |
| uncertainty_word	| int64 | Uncertainty word count using Loughran McDonald Financial sentiment analysis |
| litigious_word	| int64 | Litigious word count using Loughran McDonald Financial sentiment analysis |
| constraining_word	| int64 | Constraining word count using Loughran McDonald Financial sentiment analysis |
| interesting_word	| int64 | Interesting word count using Loughran McDonald Financial sentiment analysis |
| modal_strong_word	| int64 | Modal Strong word count using Loughran McDonald Financial sentiment analysis |
| modal_neutral_word	| int64 | Modal Neutral word count using Loughran McDonald Financial sentiment analysis |
| modal_weak_word	| int64 | Modal Weak word count using Loughran McDonald Financial sentiment analysis |
| difference	| float64 | Intra-day difference between opening and closing S&P500 stock price  	
| target	| int64 | Target variable |
