# Research Question
How accurately can you predict the number of stars a customer gives based on the review text, business type, location, and other factors given in the review.

# Data
To answer this question, I can use a yelp review data set that has already collected and saved from my company's machine learning S3 bucket. The total population of Yelp reviews is about 990,000 but I will only be using a subset of 300,000 reviews for my analyis because of processing power constraints. Although there are 15 columns (excluding the target column) that can be used, for the initial analysis and model development, I chose to focus on a subset of columns for EDA and model development including:
- Review Text: The content of the customer review.
- Location: The geographical location of the business including postal code, longitude, and latitude.
- Review Factors: The usefulness, whether the review was funny, and the date of the the review
- Star Rating: The target variable, representing the number of stars (ranging from 1 to 5) that a customer assigns to the business.

# Methodology
### 1. Exploratory Data Analysis
The EDA I conducted includes:
- The distribution of reviews with 1-5 stars, with the majority of reviews being 5 star reviews
- Analyzing the the length of reviews, with shorter reviews being most common (about 100 words in length)
- Displaying the word clouds of positive and negative reviews using sentiment analysis. 'Place' and 'food' were the most common words in all reviews and they showed up in both positive and negative reviews.
- A distribution of the mean stars by year and month. On average, the mean stars was around 3.5 - 4.0 stars but in 2019 there is a sharp increase in the mean to almost 5 stars. On a monthly basis, the average stars is around 3.7 each month.

### 2. Data Pre-Processing
I applied the below pre-processing functions to the dataset. To make this process faster and easier, the dataframe will be transformed to a Dask dataframe with a specified number of partitions based on a chunk size of 10,000.
- Lowercase conversion
- Remove HTML tags
- Remove stopwords
- Remove punctuation
- Tokenize words
- Stem words using PorterStemmer

# Models
Several machine learning models were tested to determine which provides the best performance for predicting the star rating:

### 1. Decision Trees:
The Decision Tree model is a very simple and interpretable model that splits the data into branches based on values within the features. Although this model can be interpreted very easily, it had the lowest predictive accuracy of all the models.

### 2. K-Nearest Neighbors (KNN):
The K-Nearest Neighbors model is able to classify a data point based on the majority class of its nearest neighbors. KNN had low predictive accuracy but performed slightly better than the Decision Tree model. 

### 3. Random Forest:
Similar to Decision Trees, the Random Forest Classifier builds multiple decision trees and aggregates their results. The Random Forest model performed better than a single decision tree but still the predictive accuracy was not much higher than the decision tree model.

## Recommended Model: Neural Network
The best-performing model in this study was a Neural Network, achieving a predictive classification accuracy of approximately 63%. The neural network was chosen due to its ability to handle complex, non-linear relationships in the data, particularly when dealing with high-dimensional inputs like text data.

Architecture:
- Input Layer: Inputs the preprocessed features including TF-IDF vectors from review text, encoded categorical, and scaled numerical variables.
- Hidden Layers: A dense layer helping the network learn intricate patterns in the data.
- Output Layer: Multi-class classification, predicting the probability distribution over the 5 possible star ratings.

# Why This Model Is Useful for Business Owners
The ability to predict star ratings based on review text and other features is incredibly valuable for business owners. With this model, business owners can:

1. Anticipate Customer Feedback: By analyzing customer reviews, business owners can anticipate how customers might rate their services, allowing them to address potential issues before they escalate.
2. Improve Customer Experience: Insights from the model can highlight which aspects of a business are positively or negatively impacting customer satisfaction, guiding improvements.
3. Strategic Decision Making: Understanding the factors that influence star ratings can help businesses tailor their offerings, marketing strategies, and customer service to align more closely with customer expectations.

## Next Steps & Recommendations
- Targeted Improvement Areas: Add in new features such as business type or business attributes and see if the model's accuracy improves. This will flag if those features contribute to higher or lower ratings and implement changes to address these specific issues.
- Customer Feedback Management: Implement a system where the predicted ratings from the model trigger proactive customer service responses. For instance, if a low rating is predicted, the business could reach out to the customer for feedback or offer a resolution before the review is posted.
- Enhancing Customer Experience: Analyze the features that the model identifies as most influential in determining star ratings using a SHAP Analysis or something similar. This information can be used to enhance the customer experience in these areas.
- Data-Driven Marketing Strategies: Utilize the model's insights to segment your customers based on predicted satisfaction levels. Tailor marketing campaigns to target different segments, such as offering loyalty programs to highly satisfied customers or sending personalized offers to those predicted to give lower ratings.
Leverage predicted high ratings to promote your business.

# Link to Code
(https://github.com/srishtikama/Python_Projects/blob/91b50bcb0dd6f01262fb01270989afb0648234f3/Final%20Capstone%20Script.ipynb)

