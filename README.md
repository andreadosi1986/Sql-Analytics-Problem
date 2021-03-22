# Sql-Analytics-Problem

The sources of my application are slow_log.json to get a statistical overview of the problem and to train and test the regressor algorithm and the general_log.json to predict the execution time of the real time queries.

## PROBLEM: Query Analytics

### Data Analytics

Using Python Jupiter lab, I have provided a brief overview of the slow log dataset: first of all I have counted the most common queries and then I have visualized the most frequent tables, operations and fields using bar charts.

### Model Training

In my work, I focused on analyzing only the text of the SQL query using the text query of the slow log dataset. Splitting the query text by words, I have built feature vectors comprising the dataset. The Feature Extraction phase consists in extracting feature vectors from a mass of SQL data. For this purpose, I used the technique of vector representation BoW (Bag-of-Words). After that, I have choosen the GBR (Gradient Boosting Regression) algorithm training it as usual on the 75 % of the slow log dataset, and then testing it on the remaining 15 %. I got a measure of the accuracy using the mean square error, and I've plotted the predicted regression toghether with the original time query points. To prevent possible overfitting, I have choosen the K-Fold validation approach with the R^2 metric. As final step, I have predicted the time execution queries using the general log dataset.

After this introduction, I can consider the following answers:
1.	Machine learning can be appropriate for this problem: the SQL statement samples are represented using a Bag-of-Words (BoW); the Gradient Boosting regression can be performed on the Bow to predict the query time. The Machine Learning approach is not the unique one: machine learning problem treats queries as a black box, but we know what is going on inside the box (inside queries). Other approaches are possible, as the optimizer based approach.
2.	Another critical issue of the Machine Learning approach is that it can suffer the problem of infinite number of unknown queries. To evaluate the accuracy of unknown test queries I have choosen two different metrics : the mean squared error and R^2.   
3.	The predictive query time execution problem can be treated under a supervised learning approach, in particular as a regression problem, since the target variable to be estimated can be described as a continuous one. 
4.	As described in the python code, there are many repeated queries. The slow log dataset should be more diversified: a larger number of different queries should be provided for a better prediction. 
