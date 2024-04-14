# Tree-based-methods-for-classification

### Dataset
the APS Failure data from: https://archive.ics.uci.edu/ml/datasets/APS+Failure+at+Scania+Trucks
A seriously imbalanced dataset with a large number of features and data points. Had to use SMOTE. 
The dataset contains a training set and a test set. The training set contains 60,000 rows, of which 1,000 belong to the positive class and 171 columns, of which one is the class column. All attributes are numeric.

### Tasks Performed
I found out my data was missing some pieces. Since there were a lot of missing spots, I decided not to just throw them out. First, I looked up ways to fix missing data problems and picked one method to use.

Then, for each of the 170 different things I was looking at in my data, I figured out a special number called the coefficient of variation (CV), which helps me understand how spread out my data is.

After that, I made a big chart to see how all these things are related to each other using a tool called pandas.

I picked a few of the things with the biggest CV numbers and made some scatter plots and box plots, kind of like examples I saw in a book. This helped me think about which of these things might be important, but I didn't decide to only use these in my next steps.

I also counted how many of my data points were positive and how many were negative to see if there were a lot more of one than the other, which would mean my data wasn't balanced.

Next, I trained a machine called a random forest to classify my data without worrying about the imbalance. I checked how well it did by looking at different scores and errors, including something called the Out of Bag error.

Then, I learned about ways to make my random forest work better when the data isn't balanced. I tried one of these ways and did the training again to see if it worked better.

I tackled the challenge of understanding XGBoost and model trees, diving into the differences between univariate and multivariate trees. In a univariate tree, I learned that each split in the tree is based on just one input dimension. However, when I explored multivariate or model trees, I found that decisions at each node could consider all input dimensions, offering a broader perspective.

For decision-making in univariate classification trees, I used majority polling at each node to determine the split. But with model trees, I adopted a more sophisticated approach by using a linear model that relied on all variables to decide how to split at each node. This was a departure from the simple threshold method I was accustomed to, allowing for a more nuanced decision rule involving the sum of the product of coefficients and variables being greater than a threshold.

In the case of regression trees, instead of settling for the average value within a node's region, I utilized a linear regression model to predict the node's value, a method that proved more accurate for continuous data.

I encountered the concept of using Logistic Regression at each node, which was particularly useful given the large number of variables in my data. I opted for L1-penalized logistic regression, which helped in selecting features by reducing some coefficients to zero.

I chose XGBoost for its capability to efficiently fit model trees, including those using penalized logistic regression. To fine-tune the model, I determined the best regularization term (\(\alpha\)) through cross-validation. I trained the model on the APS dataset without compensating for class imbalance at first, using different cross-validation methods like 5-fold, 10-fold, and leave-one-out to estimate and compare errors.

Reporting the Confusion Matrix, ROC, and AUC for both the training and test sets helped me gauge the model's effectiveness.

Recognizing the challenge posed by class imbalance, I preprocessed my data with SMOTE (Synthetic Minority Over-sampling Technique), which balanced the dataset by creating synthetic samples for the minority class.

I then retrained the XGBoost model with L1-penalized logistic regression at each node using the SMOTE-preprocessed data. It was crucial to apply SMOTE correctly during cross-validation to avoid introducing bias. Finally, I compared the outcomes from the models trained with and without SMOTE preprocessing, which illuminated how significantly class imbalance could affect model performance.
