# Sarcasm In Headlines (CAIS++ Winter Project)
By: Aditya Kumar (akumar35@usc.edu)

## Abstract

The aim of this project is to create an LSTM model that detects sarcasm in news headlines, using existing headlines from HuffPost and The Onion for non-sarcastic and sarcastic headlines, respectively. 

## The Dataset
The [News Headlines Dataset For Sarcasm Detection](https://www.kaggle.com/datasets/rmisra/news-headlines-dataset-for-sarcasm-detection) dataset was used to train the model. For preprocessing, all text was made into lowercase, stop words (common words with little significance) were removed, and all punctuation and numeric digits were also removed. These decisions were made to try to preserve the meaning and emotions behind a news headline while also normalizing the headlines.

## Model Development
A Word2Vec model was used to convert the words into vectors that the LSTM can 'understand'. The LSTM's first model is an embedding layer to convert each word to its embedding. An LSTM seems to be the correct choice for this task due to the sequential nature of text data; the model can essentially 'remember' earlier context as it analyzes a headline. And finally, after tuning hyperparameters, the dropout and recurrent dropout values were both set to 0.15. 

## Results
3-Fold Cross Validation was used with a batch size of 2048, and the second fold resulted in the best accuracy metrics. These were the metrics:

### Confusion Matrix
True Positives: 3993

False Negatives: 1038

False Positives: 932

True Negatives: 2940


### Additional Metrics
              precision    recall  f1-score   support

           0       0.79      0.81      0.80      4925
           1       0.76      0.74      0.75      3978

        accuracy                           0.78      8903
       macro avg       0.78      0.77      0.78      8903 
    weighted avg       0.78      0.78      0.78      8903


AUC: 0.7749131390158562


## Discussion
The model architecture fits the task well due to the sequential data: text data often works well with recurrent neural networks. The dataset is also a good fit for sarcasm detection because we can say with certainty that headlines from HuffPost are not sarcastic while headlines from The Onion are sarcastic. On the other hand, options such as using a dataset of tweets would be much more difficult due to the subjective nature of sarcasm in tweets. A tweet by itself could be considered either way; context and the nature of replies would need to be studied somehow to gain a bigger picture.

Continued work in this task could be helpful in detecting misinformation online. With how quickly headlines can go viral online, it is important to ensure that the general public is not misled. Therefore, a form of sarcasm detection could be used to help people understand the true intentions behind text that is posted online. However, major limitations do exist because usually, headlines are rooted on real-life and up-to-date context. For example, a model trained in 2019 would fail to understand many of the headlines (whether sarcastic or not) that were about the COVID-19 pandemic. Therefore, it would be important to keep such a sarcasm detection model up to date on latest events.

A possible next step would be to continue to train the model by tuning hyperparameters even more. Additionally, it could be beneficial to explore data outside of just HuffPost and The Onion (such as other news sites) in order to broaden the data that the model is trained on. In fact, one option could be to attempt to incorporate tweets from established accounts (for example, The Onion has a twitter account) in order to train for more than just news headlines; however, this might make the data too broad for the model to be successful.
