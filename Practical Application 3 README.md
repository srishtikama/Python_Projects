# Assignment
The goal of this assignment is to compare the performance of the classifiers, specifically K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines.

# Data
This data comes from the UCI Machine Learning repository and is from a Portugese banking institution. The data is a collection of the results of multiple marketing campaigns with the target variable being whether or not the customer has subscribed to a term depost from the bank. Within the data, there are multiple numerical and categorical variables describing the customer's banking profile and the bank's campaign for term deposits. There are 10 numerical and 10 categorical columns withing the data.

## Data Changes Made
No columns were dropped as there was no missing data. To prepare the data for classification, I applied One Hot Encoding to the 10 categorical columns and Standard Scaler to the 10 numerical columns.

# Baseline Classification Models
To start my model comparison, I applied the default KNN, Logistic Regression, Decision Trees, and SVM models to the data to understand how the 4 models would perform with no hyperparameter tuning. 

#### Findings
- Logisitic Regression: Had a low training time of .6 seconds and the highest test accuracy of 91.2%.
- Decision Trees: Had the highest training accuracy of 100% but the lowest test accuracy of 88.8% which seems to be overfitting of the training data.
- SVM: Had the highest training time of 24 seconds but the training and testing accuracy were very similar to the Logistic Regression and KNN.
- KNN: Had the lowest training time of 0 seconds (could be a rounding issue) and the training and testing accuracy were very similar to the Logistic Regression and SVM.

# Investigation: Hyperparameter Tuning
For the independent investigation, I chose to do hyperparameter tuning using GridSearchCV. For the 4 models, I analyzed:
- Logisitic Regression: C, Penalty, and Solver
- Decision Trees: Max Depth and Min Samples Split
- SVM: C and Kernel
- KNN: N Neighbors and Weights

#### Hyperparameter Tuning Findings
For all 4 models, the time needed to train the models increased but the training accuracy score decreased. I then found the test accuracy using the best parameters tested in GridSearchCV as:
- Logisitic Regression: 91.2% with C = .3, Penalty = l1, and Solver = saga
- Decision Trees: 90.5% with Max Depth = 300 and Min Samples Split = 60
- SVM: 90.3% with C = .3 and Kernel = linear
- KNN: 90.6% with N Neighbors = 10 and Weights = uniform
The Decision Tree model's test accuracy was better than the default model but for the other 3 models, the test accuracy was about the same. 

# Next Steps
Using the findings listed above, further analysis can be done to see if the hyperparameters can be tuned with more targeted options instead of arbitrarily increasing the options. Also, for faster training, columns can be removed based on level of correlation to the target variable. 

# Link to Code
[prompt_III.ipynb](https://github.com/srishtikama/Python_Projects/blob/e161970e45e65537e84e7213f1279af0428e8dc8/prompt_III.ipynb)

