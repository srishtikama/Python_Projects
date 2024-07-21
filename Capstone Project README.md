# Research Question
How accurately can you predict the number of stars a customer gives based on the review text, business type, location, and other factors given in the review.

# Data
To answer this question, I can use a yelp review data set that has already collected and saved from my company's machine learning S3 bucket. The total population of Yelp reviews is about 6.3 million but I will only be using a subset of 990,000 reviews for my analyis because of processing power constraints. Although there are 15 columns (excluding the target column) that can be used, for the initial analysis and model development, I chose to focus solely on the Yelp review text (r_text) column to conduct EDA and develop my models. 

# Methodology
### 1. Exploratory Data Analysis
The EDA I conducted includes:
- The distribution of reviews with 1-5 stars, with the majority of reviews being 5 star reviews
- Analyzing the the length of reviews, with shorter reviews being most common (about 100 words in length)
- Displaying the word clouds of positive and negative reviews using sentiment analysis. 'Place' and 'food' were the most common words in all reviews and they showed up in both positive and negative reviews.

### 2. Data Pre-Processing
I applied the below pre-processing functions to the dataset. To make this process easier, the dataframe will be changed from pandas df to Dask df with a specified number of partitions based on chunk size (10,000). Within each pre-processing step, a new dataframe will be created that will be referenced in the next step.
- Lowercase conversion
- Remove HTML tags
- Remove stopwords
- Remove punctuation
- Tokenize words
- Stem words using PorterStemmer

## Statistical Model Findings
For each model, I applied the TF-IDF vectorizer to transform the review text into numerical vectors indicating the importance of each word in the text. To then classify and predict the number of stars for each review, I applied Logistic Regression, SVM, and Random Forest models and below is a summary of my results:
### 1. Logistic Regression
### 2. SVM
### 3. Random Forest

### Final Findings


# Next Steps
Although the statistical models listed above had reasonably good accuracy scores, I am hoping to improve my accuracy scores first by using Gensim's Word2Vec instead of TF-IDF and seeing whether the Cross Bag-of-Words or the Skipgram methods provide a better accuracy. Then, I am also hoping to see if using a Keras Neural Network will improve my accuracy score. 

# Link to Code
[prompt.ipynb](https://github.com/srishtikama/Python_Projects/blob/main/prompt.ipynb)
