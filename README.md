## Background:

This project considers modelling one of the most famous sentiment analysis datasets: the Stanford Sentiment Treebank1. This dataset contains 9, 645 sentences and a sentiment score is provided numerically between 0 to 1.
Per the authors’ suggestion, we can bucketize them into either two classes or five classes: {negative and positive}
or {very negative, negative, neutral, positive, and very positive}, respectively. Some examples can be found in the table below:
Table 1: Examples from Stanford Sentiment Treebank
| Review Sentence                                  | Regression Label | Two-Class Label | Five-Class Label |
|--------------------------------------------------|------------------|-----------------|------------------|
| It’s worth taking the kids to.                   | 0.83             | positive        | very positive    |
| a portrait of an artist.                         | 0.58             | positive        | neutral          |
| final verdict: you’ve seen it all before.        | 0.18             | negative        | very negative    |
Language Modeling2: One of the difficulties of modeling languages is how to transform them into numerical vectors so we can apply machine learning methods to them. Using ”It’s worth taking the kids to” as an example, two common practices are:
• Bag-of-Words first define a ”dictionary” of k words and transform each sentence into a length-k vector depending on the existence of each word in the sentence to embed. For instance, if the dictionary is {artist, worth, kids, verdict} then the vector expression for the example sentence is [0, 1, 1, 0].
• Word Embedding, instead, has a look-up projection matrix3 for most of the words, and we can simplify the sentence embedding as the pooling average across embedding over words. Assuming the word vectors in the example are [v1, v2, v3, v4, v5, v6] then the corresponding sentence embedding is 1 6 P6 i=1 vi.

## Methodology

Throughout the project multiple statistical methods will be used to analyze the Stanford Sentiment Treebank (SST) dataset, which was created for the purpose of sentiment analysis research. Sentiment analysis involves determining the sentiment or emotional tone expressed in a selection of text, such as whether it is very positive, positive, neutral, negative, or very negative. We will use statistical methods to identify the most significant words for sentiment analysis in Part I, then we will use various methods for two-class sentiment
classification prediction in Part II, and will conclude by using di!erent methods for five-class sentiment classification prediction in Part III.
In order to prepare our data for analysis, we began by preprocessing the data in order to remove punctuation and numbers, and to convert uppercase letters to lowercase. This allowed us to create a corpus which we could then transform into a document-term matrix by utilizing the DocumentTermMatrix and data.table functions. Additionally, we reduced the dimensionality by removing stop words and sparse words.

### Part 1 

#### Forward Stepwise Selection
This output shows the top 20 words for both the training and testing sets. We used forward selection due
to the large nature of the datasets. Forward selection starts from the null model rather than working from
the full model, and adds variables that would best support the model until 20 words are hit. This saved us
runtime, and is most practical in this situation. We note that the words selected in each of these models
mostly are polarizing, strong, emotional words, such as “best”, “wonderful”, “worst”, “mess”, etc. This
seems practical, as those polarizing words tend consistently represent opposite ends of the spectrum (one
would not use the word “worst” to typically describe something positive, and so on).

#### Lasso and Ridge Regression
We ran Lasso and Ridge regression on both the training and test sets. To find the top words, we compared
their magnitude and selected the top 20 most influential words in each model. We see a similar pattern to
that of the forward stepwise selection method, where extremely polarizing words seem to be common choices,
such as “crap”, “insulting”, “amazing”, “breathtaking”, etc.

### Part 2
#### Logistic Regression
Logistic regression is a classification technique that is most often used for binary classification, where it
models the probability of a particular class.

#### Linear Discriminant Analysis
LDA is a classification method that seeks to find linear combinations of features that best separate multiple
classes.

#### Quadratic Discriminant Analysis
QDA is a classification technique similar to LDA, but it allows for for non-linear decision boundaries.

#### Naive Bayes Model
Naive Bayes is a classification method based on Bayes’ theorem.

#### Principal Component Classification with Logistic Regression
In order to carry out PCA, we found the principal component directions from the training set and transformed
all the three sets on the basis of these loadings. We then performed a validation on these components by
taking the top PCs.

#### Partial Least Squares
The hyperparameter ncomp was used in initial training. The best number of components was determined to
be 3.

### Part 3
The models we have chosen for Part III for five-class prediction of sentence sentiment 

#### Classification Trees - Pruning
Classification trees can be a useful method for classification because they are conceptually simple and can
be easily interpreted by the general public, but can still be powerful tools for interpretation and prediction.

#### Bagging
Both bagging and random forests are a forms of classification where we build many trees and then combine
these in order to obtain one final prediction. They are also known as a general learning method called
ensemble learning. These methods take the majority vote over all the trees.
In bagging, we grow deep and complex trees which have high variance, but low bias. However, when we take
the majority vote over many trees, the bias stays the same and the variance decreases.


#### Random Forests
Random forests is an improvement over bagging because it accounts for the possibility that predictors can
be highly correlated. It accomplishes this by using only a subset of the predictors of size m at each split.
For random forests, we typically select a value of m by taking the square root of the number of predictors.
Therefore, we will use a value of 10 for mtry. We will determine the value of ntree using the same process
as above for bagging.


#### Boosting
Boosting is also an ensemble learning method, but this method evolves over time. Boosting starts with a
weak model and improves its performance by continuing to build new trees sequentially. Each new tree
attempts to improve the previous tree by looking at errors.


#### Suport Vector Machines
Support vector machines can relax the strict boundary of the linear partition model by incorporating some
cost to the misclassified data points; however, the total cost must not exceed a prescribed value. Hence,
SVM is making the linear partition flexible to extreme values. We have used a linear kernel in this instance.

