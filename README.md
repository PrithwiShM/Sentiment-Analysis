Throughout the following report, multiple statistical methods will be used to analyze the Stanford Sentiment
Treebank (SST) dataset, which was created for the purpose of sentiment analysis research. Sentiment analysis
involves determining the sentiment or emotional tone expressed in a selection of text, such as whether it is
very positive, positive, neutral, negative, or very negative. We will use statistical methods to identify the most
significant words for sentiment analysis in Part I, then we will use various methods for two-class sentiment
classification prediction in Part II, and will conclude by using di!erent methods for five-class sentiment
classification prediction in Part III.
In order to prepare our data for analysis, we began by preprocessing the data in order to remove punctuation
and numbers, and to convert uppercase letters to lowercase. This allowed us to create a corpus which we
could then transform into a document-term matrix by utilizing the DocumentTermMatrix and data.table
functions. Additionally, we reduced the dimensionality by removing stop words and sparse words.

Part 1 contains-
Forward Stepwise Selection
Lasso and Ridge Regression

Part 2 contains-
Logistic Regression
Linear Discriminant Analysis
Quadratic Discriminant Analysis
Naive Bayes Model
Principal Component Classification with Logistic Regressio
Partial Least Squares

Part 3 contains-
Classification Trees - Prunin
Bagging
Random Forests
Boosting
Suport Vector Machines

