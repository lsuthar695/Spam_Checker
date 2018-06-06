# Spam_Checker
 SMS-spam detector with Scikit-learn
 
Introduction
Solving problems with using machine learning is popular now. Maybe you have seen Competitions on Kaggle, courses on Coursera or EdX. For ML we have many tools like Scikit-learn, Tensor-flow, Caffe, Spark MLib and another.
One of the basic and popular tasks is classification any data (text or images). In this article, you can read about using Scikit-learn for detecting SMS-spam in a text.

The Basic algorithm for solving a task like this is:

Collect data and classify it
Divide data-set to teach-set and test-set
Collect classifiers and vectorizers
Fit each classifier with teach-set and calculate accuracy with test-set
Find classifier with the biggest accuracy
Write API
Starting
For this example, I will write a script for task SMS Spam Collection Dataset on kaggle.com.

Click on link, log in and download file spam.csv. This file contains a set of 5,574 SMS tagged messages in English. Each message is tagged as ‘ham’ (legitimate) or ‘spam’.


For classification, I will use library Scikit-learn. It contains many methods for:

classification, regression and anomaly detection
implements the k-nearest neighbors algorithm
decision tree-based models for classification and regression
implements Naive Bayes algorithms and other modules.
Documentation http://scikit-learn.org/stable/modules/classes.html

Each of this module is a black box with the same interface.

Fit() — method for teaching classifier
Score() — method that returns the mean accuracy on the given test data and labels.
Predict() — method for making prediction. For example: ‘ham’ or ‘spam’
Predict_score() — method that returns probability estimates for each predictions. For example: 0.8 for ‘ham’ and 0.2 for ‘spam’.
Vectorizers
But every of this module does not understand plain text; they need an array of features. How to build feature vectors from plain text?
For it, Scikit-learn has vectorizers: CountVectorizer, TfidfVectorizer, HashingVectorizer.

Example how to work CountVectorizer.
It converts a collection of text documents to a matrix of token of unique words counts. It finds all unique words in text-set and makes one vector. After, it converts each text to an array of unique words counts. And as a result, we have one vector of unique words and many arrays with many count of zero. Example for data-set with 3 messages:

U can call me now
Sorry, I will call later
Ok i am on the way to home hi hi

Another is TfidfVectorizer. It is an implementation of Term Frequency times Inverse Document Frequency algorithm. You can read about it in official documentation.

About test
Another question, how to test score of classification?
There is one way. We need to divide one data-set (spam.csv) to two data-sets (teach-set and test-set) with the ratio 80/20 or 70/30.
We will use teach-set for teaching classifier and test-set for calculating accuracy.

Start coding
After the theory, we can start coding.
Standart python script for running Scikit looks like this:


After running, we can insert all data to CSV-file and find classifier with maximum score.


Combination OneVsRestClassifier with TfidfVectorizer has maximum result of score.
After it, let’s see each prediction more detail and save a report to CSV-file.


After run that script, open test_score.csv and you can see 14 wrong predictions vs 1158 right. It is amazing!

For making accuracy bigger, we can use various stemming like stemming 1.0 for English. Or Mystem from Yandex for Russian. But I don’t want it.

I think, 98,8% is very good and now we can write API. For writing API we will use Flask. Flask is a microframework for Python. It is pretty simple and has many useful features.


Run this script and open http://localhost:5000/ in a browser.


That is all. If you want, you can see additional resources:
github
kaggle

