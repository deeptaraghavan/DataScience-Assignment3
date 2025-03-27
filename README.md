# CS1656-A3

# Assignment #3: Recommender System

### Description
This is the **third assignment** for Introduction to Data Science

### Goal
The goal of this assignment is to familiarize you with the User-based Recommender System and also expose you to model evaluation on real data.

### What to do -- recommender.py
You are asked to complete a Python program, called `recommender.py` that will
* [Task 1] Calculate user similarity weights among users using four different metrics, including Euclidean distance, Manhattan distance, Pearson correlation, and Cosine similarity
* [Task 2] Use user similarity weights from top k users to predict movies ratings for selected users 
* [Task 3] Evaluate the performances of combinations of different metrics and different values of k 

We present the details of each task next. 

### Task 1
In this task, you will need to implement four methods to calculate user similarity weight. Each method has two arguments, the first argument should be  the training dataset, in the form of a DataFrame, and the second argument should be the selected userId. <br />

<font size="2">**Method #1**</font>:  train_user_cosine<br />
This method calculates the user similarity using the Cosine similarity.

<font size="2">**Method #2**</font>: train_user_euclidean<br />
This method calculates the user similarity using the Euclidean distance.

<font size="2">**Method #3**</font>: train_user_manhattan<br />
This method calculates the user similarity using the Manhanttan distance.

<font size="2">**Method #4**</font>: train_user_pearsons<br />
This method calculates the user similarity using the Pearson correlation.

### Task 2
In this task, you need to use the user similarity weights that you get from **Task 1** to make predictions of movie ratings for selected users. You should use the similarity from top k users. You should try combinations of different metrics with different values of k. To make predictions, you need to use two datasets: `small_test.csv` and `medium_test.csv`. **Note you should only make predictions for not null ratings in the two test datasets. There's no need to predict missing ratings.**  <br />

In this task, you need to implement two methods. <br /> 

<font size="2">**Method #1**</font>: get_user_existing_ratings <br />

This method returns the existing movie ratings of the selected userId from given dataset. 

This method has two arguments.
* data_set: this argument should be the test dataset, in the form of a DataFrame
* userId: this argument is the selected userId that you need to retrieve the ratings for

The return value should be a list of tuples, each of which has the movie id and the rating for that movie, for example [(32, 4.0), (50, 4.0)]

<font size="2">**Method #2**</font>: predict_user_existing_ratings_top_k <br />
The purpose of this method is to predict the selected user's movie ratings. Note that we don't calculate the user's missing ratings, but the ratings that the user ALREADY has, in order to compare the predicted ratings to the existing ratings we get by calling `get_user_existing_ratings`
The return value should be a list of tuples, each of which has the movie id and the rating for that movie, for example [(32, 4.0), (50, 4.0)].

This method has four arguments. 

* data_set: this argument should be the test dataset, in the form of a DataFrame
* sim_weights: this argument should be the similarity weights you get from **Task 1**; there should be four types of similarity weights, one for each metric
* userId: this argument is the selected userId that you need to make the prediction
* k: this argument is the number of top k users 




### Task 3: 
In this task, you need to evaluate the prediction performance of combinations different user similarity metrics and different values of k. You should compare the predicted ratings with the existing ratings of selected users in the test datasets. To evaluate the performance, you should calculate the root mean square error (rmse) of the predicted ratings and existing ratings. <br />
In this task, you need to implement method **evaluate**. This method has two arguments, in the form of a list of (movieId, rating) tuples. The first argument list that contains existing ratings of a user, and the second argument is a list that contains predicted ratings of the same user. The return value should be a small dictionary that contains the root square error and the ratio, like {'rmse':0.5, 'ratio':0.9}.

We give the definition of ratio as follow:

When comparing two sets of ratings for evaluation, the baseline set and the predicted set, the ratio is the number of movies that BOTH sets have ratings for, over the number of movies that the baseline set has ratings for.

For example, If for user1 we have ratings for movie1, movie3, and movie5, and our top-k prediction only produces ratings for movie1 and movie3, the ratio would be 2/3. Only for two out of the three movies we have a predicted rating. This is important, as if we choose a low k value, we might only get a prediction for a very small number of movies, which is bad, even if those ratings come close to the real ones. You can think of it as the recall vs accuracy.



The provided skeleton code already has implemented methods that perform multiple predictions and evaluations for different combinations of distance metrics and k values. They should help you to test your code and make sure your methods return the right type of values.



### Allowed Python Libraries (Updated)
You are allowed to use the following Python libraries (although a fraction of these will actually be needed):
```
pandas
csv
requests 
json
datetime 
numpy 
scipy
re
argparse
collections
glob
math
os
string
sys
time
xml
random
```
If you would like to use any other libraries, you must ask permission within a maximum of one week after the assignment was released
