# Assignment 1: Bag of Words, Naive Bayes, Support Vector Machines, Decision/Regression Trees

Deadline: Sunday, October 26th, 2025, 23:59

Environment: Python, numpy, pandas, matplotlib, scikit-learn, ntlk, ISLP.

---

## Part A: Binary Classification on Text Data

In this part, you will implement several machine learning techniques from class to perform classification on text data. Throughout the problem, we will be working with the **NLP with Disaster Tweets** Kaggle competition data; the task is to predict whether or not a tweet is about a real disaster.

1. **Data Loading and Splitting**
  Load the dataset; its path in the repository is `data/disaster_tweets.csv`.

  * What percentage of the data are of real disasters, and what percentage is not? The description of each column is explained in the `README.md` contained in the `data` folder.
  * Split the data into 70% training and 30% testing.

2. **Data Pre-processing**
  Since the data consists of tweets, they may contain significant amounts of noise and unprocessed content. You **may or may not** want to do one or all of the following. Explain the reasons for each of your decisions (why/why not).

  * Convert all the words to lowercase.
  * Lemmatize/stem all the words (you can use `nltk` as we did in the practical session).
  * Strip punctuation.
  * Strip stop words.
  * Strip "@" and urls.
  * You may come up with your own extra procedures (explain them if you do).

3. **Bag of Words Model**
  Your next tast is to extract features in order to represent each tweet using the binary "bag of words" model, as discussed in the practical session. The idea is to build a vocabulary of the words appearing in the dataset, and the to represent each tweet by a feature vector $x$ whose length is the same as the size of the vocabulary, where $x_i=1$ if the $i$'th vocabulary word appear in that tweet, and $x_i=0$ otherwise. Using `CountVectorizer`:
  
  * Set the option `binary=True` to ensure the feature vectors are binary.
  * Pick a threshold $M$ (using option `min_df=M`) such that only words that appear in at least $M$ are included in the vocabulary.
  * Make sure you fit `CountVectorizer` only on your training set, and use the same instance to process both training and testing observations.
  * **Note**: Only construct feature vectors using the text in the `text` column. Ignore `keyword` and `location` for now.
  * Report the total number of words in your vocabulary.

4. **Logistic Regression**
  We will train and evaluate several logistic regression models. We will specifically be using the F1 score for evaluation.

  * Train a logistic regression model without regularization terms. By default, `sklearn` uses L2 regularization, but you can turn it off using the `penalty` parameter. Report the F1 score for the training and testing set. Comment whether you observe any issues with overfitting or underfitting.
  * Train a logistic regression model with L1 regularization, making sure to use *some* procedure to pick the optimal penalty parameter. Report the performance of the final model and comment.
  * Same as the previous point, but now with L2 regularization.
  * Which one of the three classifiers performed best on your training and testing set? Did you observe any overfitting and did regularization help reduce it? Support your answers with the classifier performance you got.
  * Inspect the weight vector of the classifier with L1 regularization. What are the most important words for deciding whether a tweet is about a real disaster or not?

5. **Bernoulli Naive Bayes**
  Just like point 4, but now using the Bernoulli Naive Bayes algorithm for prediction.

  * Write the necessary funtions to perform the Bernoulli Naive Bayes procedure, like we did in the practical session. Use Laplace smoothing with $\alpha=1$.
  * Report the F1 score for the training and testing sets. Comment.

6. **N-gram model**
  We will extend what we learned in class. The $N$-gram model uses contiguous sequences of words; e.g., for $N=2$, the text "Alice fell down the rabbit hole" consists creates a vocabulary with the 2-grams ["Alice fell", "fell down", "down the", "the rabbit", "rabbit hole"] **may also** contain the 1-grams ["Alice", "fell", "down", "the", "rabbit", "hole"].

  * Use `CountVectorizer` to create 2-grams. You may set the option `ngram_range=(2,2)` to use only sequences of two words.
  * Again, choose a threshold $M$ too use only 2-grams that appear in at least $M$ tweets. Justify your choice of $M$.
  * Report the total number of 2-grams in your vocabulary.
  * Take 10 2-grams from your vocabulary and print them out.
  * Implement a logistic regression (choose one of any of the specifications, i.e. the type of regularization, if any) and a Bernouli classifier to train on 2-grams (you may reuse code from parts 4 and 5).
  * Report your results on the training and the testing set.
  * Do these results differ significantly from those using the bag of words model? Discuss.

## Part B: Support Vector Machine and Overfitting.

We will examine whether a low or high $C$ parameter for the objective function of the SVM algorithm can lead to overfitting.

1. **Generate Data**
  
  * Generate data with two features and two classes, such that the classes are barely linearly separable.

2. **Test a Variety of C's**

  * Compute the cross-validation error rates for support vector classifiers with a range of $C$ values. How many training observations are misclassified for each value of $C$ considered, and how does this relate to the cross-validation errors obtained?
  * Generate an appropriate test data set, and compute the test errors corresponding to each of the values of $C$ considered. Which value of $C$ leads to the fewest test errors, and how does this compare to the values of C that yield the fewest training errors and the fewest cross-validation errors?
  * Discuss your results

## Part C: Regression trees on Carseats data.

We will be using more data from the `ISLP` package. In this case, the data corresponds to children's car seats sales. More information can be found in the `README.md` file of the `data` folder. We seek to predict the values in the `Sales` column using regression trees.

1. **Process Data**
  You will need the `ISLP` package installed. With it, you can run `from ISLP import load_data()` to load the function that will gather the data for you.

  * Load the data using `load_data("Carseats")`
  * Split the data into a training set (70%) and a testing set (30%).

2. **Fitting the Trees**

  * Fit a regression tree to the training set. Plot the tree and interpret the results. Report the test MSE.
  * Use cross-validation in order to determine the optimal level of tree complexity. Does pruning the tree improve the test MSE?

---

## Deliverables

* You must fork the [original repository](https://github.com/RodrigoGrijalba/ENEI-2025-ML2-Tarea1), and turn in a link to your group's repository.
* This fork must have a Jupyter notebook in the `src` folder, which contains all the code to solve each of the problems.
* For the written commentary, you may choose between presenting it in Markdown cells within the Jupyter notebook or creating a separate `README.md` inside the `src` folder.
