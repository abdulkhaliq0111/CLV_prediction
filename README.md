# CLV_prediction


## Screenshot of POWER BI Dashboard:
![Test Image 4](https://github.com/abdulkhaliq0111/CLV_prediction/blob/master/power%20bi%20dashboard%20snapshot.JPG)


# INDEX

1. Introduction

2. Pre Processing of Data

a. Feature Selection

b. Co-relations

c. Visualisation of Data

3. Feature Interpretation

a. Minimizing Variables
 
b. Stratified Shuffle-split
 
4. Model Selection

5. Result

# INTRODUCTION

# GENERAL OVERVIEW:
Customer Life Time Value is the net profit attributed to the company for a certain amount
of period by the customer. There are two ways to grow bussiness, The first to acquire new
customers and The second is to focus on retaining existing clients and increasing their
lifetime value. Retaining the customers is the main focus of the companies now a days as
high CLV brings in high revenue from each customer, it means the company can afford to
spend more to acquire new clients and retain the existing ones.It’s solution involves
analysing the data,possible prediction of the CLV.

# DATA:
● Data available for training this model comprised of data of different customers who
took different policies.

● The data includes customers who took insurance policies on various vehicle classes
such as SUV,sports car etc and their corresponding monthly policy details like
monthly premium auto etc and thier total claim amount.

● There was no missing data in the training set or the test set, thus simplifying the
overall pre-processing.

● CLV :Net profit attributed to the company for a certain
amount of period by the customer.

● Coverage :Amount of risk or liability that is covered for an
idividual by way of insurance services.

● Monthly Premium Auto :The amount you pay for the insurance company on
a monthly basis.

● Months since Policy Inception :No.of months since the start of the insurance
policy.

● Sales Channel :The modes by which the company brings the
policies to the customers.

● Months since Last claim :No.of months since the customer claimed the last
policy.

● Total Claim Amount :The sum payable at the end of the policy(/when
claimed by company to the customer.

# TARGET:
The target variables are,

1. Making a good estimate of Customer Life Time Value (CLV) and stating CLV as a
periodic value

2. Predicting the type of customers that would generally give the company more
revenue

# PRE PROCESSING

Here we used some of the imported libraries Numpy ,Pandas ,MatplotLib ,Seaborn,
Sklearn.

we used a Standard Scaler to standardize our data.After data standardization,We’ll employ PCA to reduce the number of features in our data set.

We incorporate the newly obtained PCA scores in the K-means algorithm. That’s how we can perform segmentation based on principal components scores instead of the original features.

Before all else, we create a new data frame. It allows us to add in the values of the separate components to our segmentation data set. The components’ scores are stored in the ‘scores P C A’ variable. Let’s label them Component 1, 2 and 3. In addition, we also append the ‘K means P C A’ labels to the new data frame.

![Test Image 4](https://github.com/abdulkhaliq0111/CLV_prediction/blob/master/pca%20clusster.png)

Added 4 new features to the dataset by applying a mixture of PCA and Kmeans on highly correlated features which decreased MAPE more than 0.2.



ALSo applied ISOLATION FOREST technique for anamoly and outlier detection. for preventing loss of data log-transformed few features to remove outliers and reduce skewness of data.

# FEATURE SELECTION:

❖ Firstly we removed the features ‘ Customer ’ and ‘Effective to Date ’ because of the
insignificance in the prediction of the CLV .

❖ From the remaining features we formed a hypothesis that the following feautures
were more significant.

➢ Monthly Premium Auto

➢ Total Claim Amount

➢ Policy

➢ Policy Type

➢ Location Code


# CO-RELATIONS:

Firstly, we plotted a Heat map to get a co-relation between the feautures.

# FEAUTURE INTERPRETATION
MINIMIZING VARIABLES:

● By observing the Heat Map , we noticed some of feautures have a very less
corelations with each other.So,we removed the feautures :’Education’ ,’ State’ , ’
Number of Open Complaints’, ’Vehicle Size’, ‘Months Since Policy Inception’.

● We also removed the feauture ‘Employment Status’ as Unemployment is the major
part in Employment Status which is also covered in ‘Income’ feauture.

FEATURE IMPORTANCES:
Used Featuretools library specially adopted for feature engineering and found features with zero importances,high importances etc by fitting a gradient boosting regression model.

![Test Image 4](https://github.com/abdulkhaliq0111/CLV_prediction/blob/master/feat.png)

# STRATIFIED SHUFFLE-SPLIT:

● To split dataset into train set and test set,we used stratified shuffle-split function
from scikit-learn imported library .

● This cross-validation object is a merge of StratifiedKFold and ShuffleSplit, which
returns stratified randomized folds.

● The folds are made by preserving the percentage of samples for each class.

● We shuffle-split basis on ‘Response’ to get equal percentages in both the train and
test set to train accurately.

# MODEL SELECTION
After trying linear regression,decision tree,bagging models, we’ve built a random forest model to solve our machine learning problem but we’re not too impressed by the results.

so,our first step should be to gather more data and perform feature engineering.

next we moved to other techniques like-

Using Scikit-Learn’s RandomizedSearchCV method, we defined a grid of hyperparameter ranges, and randomly sample from the grid, performing K-Fold CV with each combination of values.

The most important arguments in RandomizedSearchCV are n_iter, which controls the number of different combinations to try, and cv which is the number of folds to use for cross validation. More iterations will cover a wider search space and more cv folds reduces the chances of overfitting, but raising each will increase the run time. Machine learning is a field of trade-offs, and performance vs time is one of the most fundamental.

From these results, we able to narrow the range of values for each hyperparameter.

MAPE of the final randomized searched model was 10.935 from initially 11.1537.We achieved an unspectacular improvement in accuracy. Depending on the application though, this could be a significant benefit.








