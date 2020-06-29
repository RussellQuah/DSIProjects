# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Reddit Web APIs & NLP Classification 

## Problem statement
As part of the marketing and research team for a series of Popular Science/ History books, my current goal is to increase the **science** book sales and online readership. In order to do that, i have to find out the type of science questions that people ask.  Reddit has a good repository of questions that users ask on r/askscience. However, due to a server error the web scraping from r/askscience got mixed up with the data from r/askhistorians as well!

Thankfully i happen to be a part time data scientiest as well. What i would need to do is to build two classification models in order to help differentiate the subreddits:
- 1 Naive Bayes Classifier
- 1 Support Vector Machine Classifier
- Evaluate the models based on:
    - accuracy (% predictions the model gets correct, both askscience and askhistorians)
    - precision (% predicted askscience when it is actually askscience)
    - sensitivity (% predicted askscience out of all correct predictions)
- choose the best performing model to test it on the holdout csv

## Executive Summary

Web scraping was done on subreddits r/askscience and r/askhistorians with a training dataset of 1454. Preliminary findings show that questions submitted to AskScience orbit around the **How's** while AskHistorians seek the **Why's** and **Would's**.

The best classification model was show to be a TfidfVectorizer into Naive Bayes with an accuracy score of 0.94.

## Web scraping and API
The web scrapping process can be found in the other [jupyter notebook here](.codes/Project_3_webscraping.ipynb)

## Classification notebook
The two subreddits chosen for web scraping and classification are:
- [Ask Historians](https://www.reddit.com/r/AskHistorians/)
    - A subreddit that allows users to post discussions or questions on any topic regarding history.
    - The subreddit has an active user base of 1.2Million redditors.



- [Ask Science](https://www.reddit.com/r/askscience/)
    - Another subreddit that allows users to ask a science question and get a science answer.
    - The subreddit is validated by an informal panel of redditors who are scientists or traing to be.
    - Panelists chosen would have a graduate level baseline of understanding in their specialised field.
    - The subreddit has a member count of 19Million.


Both subreddits have similar types of posts by reddit users:
- Self posts (questions submitted by users)
- Mod posts (regarding the state of the subreddit)
- Bot posts (recurring weekly or daily posts)
- Ask Me Anything posts (invited named scientist/ historians to have an open discuss)


## Conclusion


The best model to use to differentiate the two subreddits is gs2, **TfidfVectorizer into Naive Bayes**. The best hyperparameters:
- 'nb__alpha': 1,
- 'tfid__max_df': 0.85,
- 'tfid__max_features': 4000,
- 'tfid__min_df': 2,
- 'tfid__ngram_range': (1, 1)




It manages to outperform the other models across all metrics as well as the baseline (score of 0.496):


|Model|Accuracy Score on train|Accuracy Score on test|Precision|Sensitivity|
|---|---|---|---|---|
|**gs1** CountVectorizer->Naive Bayes|0.990|0.955|0.94|0.97|
|**gs2** TfidfVectorizer->Naive Bayes|0.991|0.961|0.95|0.97|
|**gs3** CountVectorizer->Support Vector Machines|1.000|0.915|0.89|0.93|
|**gs4** TfidfVectorizer->Support Vector Machines|0.998|0.940|0.93|0.95|
|---|---|---|---|---|
|**gs2 on holdout**|---|**0.94**|**0.94**|**0.94**|


On unseen data, the gs2 model has an **accuracy score of 0.94**, **precision of 0.94** and **sensitivity of 0.94** and an **ROC AU of 0.977**. We can conclude that it will be able to differentiate between the two subreddits, askscience and askhistorians inorder for us to find out more questions the general public has on science topics. This will help us with our goal of increasing book sales and online viewership.

### Further improvements to the model

- Improvements can be made my increasing the number of data points. As reddit limits the API webscrape to 1000, our training set is limited to 1454 posts. Having scrapped more will result in lower variance and less overfitting.
- Further tune my gridsearch to reduce hyperparamters
- Other models could be used for comparison as well, logistic regression, random forest classifiers etc.
- Use an ensemble of models to reduce overfitting.
- As all four models have high accuracy, precision and sensitivity score, it leads me to conclude that the datasets of askscience vs ask historians are quite different despite them being both an 'ask expert' subreddit. The model could be tested on a dataset that is more similar.
