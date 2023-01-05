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
