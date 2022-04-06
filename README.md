# Subreddit Classification

The notebook classifies reddit posts to its respective subreddit using different machine learning models and Compares the performance of these models. And finds the best model. Further different models are analysed. A hypothesis is made, as to why certain models performed better than others

This was done as a part of coursework. 

Experiments are conducted using the following combinations of classifier models and feature representations and evaluation of each model is done on the test set:
1.	Dummy Classifier with strategy="most_frequent"
2.	Dummy Classifier with strategy="stratified"
3.	LogisticRegression with One-hot vectorization 
4.	LogisticRegression with TF-IDF vectorization (default settings)
5.	SVC Classifier with  One-hot vectorization (SVM with RBF kernel, default settings))

<ins>**Using my own Model**</ins>:

I have then trained a model using the SGDClassifier which is equivalent to a Linear Support Vector Machine, which  is considered one of the best algorithms for text classification. TFIDF was the chosen method for vectorisation.
SGD is a very efficient approach to discriminative learning of linear classifiers under convex loss functions. SGD performs significantly better for large-scale problems, and second order stochastic gradient and averaged stochastic gradient are asymptotically efficient after a single pass on the training set.

SGD in comparison to other 5 models performs the best.

Further, a pipeline was created to tune the parameters for TF-IDF Vectoriser and Linear Regression Classifier. 
The optimised classifier performed fairly well and a notable increase in the precision, recall and f1-score values was observed. When analysing the classification report, it was observed that label 0 (PS4) ,s precision was low (0.37) and it’s f1-score of 0.50 indicates that half of the predictions were correctly made while the rest were incorrect. Similarly for label 1 (pcgaming) , the recall (0.36) was found to be significantly lower than its precision (0.71) with an f1-score of 0.48. 

Predictions for other labels performed fairly well without any noticeable anomaly in the classification report. The precision and recall values were nearly the same, which signifies that the model is performing better for labels other than 0 and 1.  

The errors are occurring probably because of the following reasons:
1.	Slight Imbalance in dataset of different labels(subreddits). 
2.	Contents of Subreddit 0 and 1 i.e PS4 and pcgaming are similar.

<ins>**Feature Engineering**</ins>:

Two new features, the addition of which would improve the performance of the model, would be ‘post_length’ and ‘title’. The ‘title’ is usually a great indicator, and summary of the contents of the post and therefore the subreddit it belongs to. For example, In a meme subreddit like ‘r/me_irl’, the titles of all the post are same i.e, me_irl. Similarly,’post_length’ can be a great indicator as well because a subreddit like ‘r/askphilosophy’ or ‘r/askhistorians’ usually attracts posts which are tens of thousands of words long while for a subreddit like ‘r/dadjokes’, the posts are usually made up of few lines. 

Addition of the two new features into the model has substantially increased the performance of the Logistic Regression models. The value of precision, recall and f1-score was found to be 0.85 each respectively. The overall accuracy significantly increased to 85%. The classification performance for label 0(r/PS4) and 1(r/pcgaming) also improved significantly and the precision, recall values for both the labels was found to be similar.

**To run the code** [![Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://www.kaggle.com/srishtibhat/subreddit-classification)
