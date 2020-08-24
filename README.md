# Cyber-bullying-detection

Cyber bullying on SNS is becoming a serious problem these days. Here, I define "Cyber bullying" as basically to bully other persons on the electronic communication such as SNS especially by sending messages. 
What I created as a final project is to detect those cyber-bullying. 


source file link:
https://colab.research.google.com/drive/1BFo1MY1BE8Eoj7kz0h6Fvpqs9epSkWvX?usp=sharing
dataset can be downloaded from here:
https://github.com/Kenta-max/Cyber-bullying-detection/blob/master/train_data.csv


The dataset: includes 1066 tweets and each tweet is already labeled with Bullying or Non-Bullying. 

Method:
Load the dataset: Load the dataset. Divide the training set or the test set by 8:2.
Tokenize the word: Then tokenize the word with removing the stop words, lemmatizing. Also, all of the words are converted into uppercase letters.


Naive Bayes Classifier with bow(Bag-of-words): Vectorize each text in the dataset. Then, train the model with those dataset. After that, vectorize the test data in the same way. Then, get the score. The f-score is around 0.54.

Naive Bayes Classifier with tf-idf(term frequency and inverse document frequency): Last one did not perform well, so I tried this one. In here, instead of bow, tf-idf is used. The f-score is around 0.50.

Logistic Regression with bow(Bag-of-words): Above 2 models do not perform well, so I tried this one. The f-score is around 0.56. Improved!

Logistic Regression with tf-idf(term frequency and inverse document frequency): I tried tf-idf as well, but f-score is around 0.55. Does not change so much.

Naive Bayes Classifier with bow(Bag-of-words with bigrams): In here, I used the bow with bigrams because the unigrams did not work really well. But, the f-score is only 0.32 terrible.

Logistic Regression with bow(Bag-of-words with bigrams):

Logistic Regression with Word2Vec: Use logistic regression with word2vec. First, I create a Word2vec vocabulary list based on train data, then I calculate the mean of all the values, then use it as the vector value which represents that sentence. But this model classifies all with 0, so the f-score is 0 which is horrible.

Support Vector Machine with bow: This one performs best.

Support Vector Machine with tf-idf

Neural Network with bow, Neural Network with tf-idf


The below is a example of  the f1-score of all the methods:
Naive Bayes Classifier with bow:  0.5847412314134025
Naive Bayes Classifier with tf-idf: 0.6536755570707165
Logistic Regression with bow:  0.6843438846896197
Logistic Regression with tf-idf:  0.6217927577370651
Naive Bayes Classifier with bow(bigrams):  0.5552126743563153
Logistic Regression with bow(bigrams):  0.5588888597961179
Logistic Regression with word2vec:  0.3633530209913002
Support Vector Machine with bow:  0.6426490248557489
Support Vector Machine with tf-idf  0.5842450606130969
Neural Network with bow:  0.6226000369025579
Neural Network with tf-idf  0.6015988571702857

From the f1-score above, I select the Logistic Regression with bow, SVM with bow, Neural Network with bow for the detecting model. The model can be passed with a string, and it will be categorized as "Bullying" or "Non-Bullying" by the majority vote.(ex: if 2 models determined "Bullying" and 1 model determined "Non-Bullying", the output is "Bullying").
