# [Python Project: Build Machine Learning Models for the Instagram Top Post Dataset](https://github.com/JoySeedhe/-Instagram-Top-Posts-Machine-Learning-Model/blob/main/python/Instagram%20Top%20Post.ipynb)

### Abstract
In the digital age, smartphones and social media have become integral to daily life, with platforms like Instagram serving as key spaces for both personal expression and business engagement. The COVID-19 pandemic further accelerated this shift, making online interaction more vital than ever. As Instagram's ecosystem grows increasingly competitive, understanding what drives a post to become a "Top Post" is crucial for users and brands alike.

This project explores the underlying patterns behind Instagram's top-performing content by analyzing post-level data. Using machine learning models—Logistic Regression and Random Forest—it identifies the most influential features that contribute to a post's visibility. The goal is to uncover actionable insights into which variables (such as like count, comment count, and follower count) significantly impact a post’s chances of surfacing at the top, offering a data-driven approach to navigating Instagram’s dynamic algorithm.

###### Top Posts in the Explore and Home tabs
![What is an Instagram Top Post](https://github.com/JoySeedhe/-Instagram-Top-Posts-Machine-Learning-Model/blob/main/python/images/What%20is%20an%20Insta%20Top%20Post.png)</br></br>
---

### Dataset Introduction
The [Instagram Top Post Dataset](https://www.kaggle.com/rezaunderfit/instagram-top-post) contains a total of 2,170 entries and is designed to support binary classification tasks. It includes 16 independent variables capturing various post and user-level attributes such as:


### 📘 Data Dictionary

| Feature Name         | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `like_count`         | Number of likes the post received                                           |
| `comments_count`     | Number of comments on the post                                              |
| `hashtag_count`      | Number of hashtags used in the post                                         |
| `is_verified`        | Whether the user is verified (`1` = Yes, `0` = No)                          |
| `is_video`           | Whether the post is a video (`1` = Yes, `0` = No)                           |
| `followers_count`    | Number of followers the user has                                            |
| `following_count`    | Number of accounts the user is following                                    |
| `caption_length`     | Length of the post caption (in characters or words)                         |
| `caption_sentiment`  | Sentiment score of the caption (e.g., positive, neutral, negative)          |
| `post_hour`          | Hour of the day the post was published (0–23)                               |
| `post_day`           | Day of the week the post was published (0 = Sunday, 6 = Saturday)           |
| `engagement_rate`    | Engagement metric based on likes/comments relative to followers             |
| `media_type`         | Type of media (e.g., image, video, carousel)                                |
| `location_tagged`    | Whether a location was tagged in the post (`1` = Yes, `0` = No)             |
| `user_type`          | Type of user (e.g., influencer, brand, individual)                          |
| `post_length`        | Total number of characters in the post (caption + hashtags)                 |
| `is_top`             | Target variable: whether the post is a top post (`Y` or `N`)                |

The target variable is is_top, which indicates whether a post is a top post (Y) or not (N). The dataset is balanced, ensuring an equal distribution of both classes, which is ideal for training supervised machine learning models without bias toward one outcome

</br></br>
---
### Problem Statement
**Which variables hold higher weightage in making a post come up on top?** The dataset has a target column of `is_top`, with binary data of "Y" or "N". This project adopts a supervised learning approach, using Machine Learning Models of `Logistic Regression` and `Random Forest` in sifting out the "super" variables.</br></br>

### Process Workflow
The dataset was checked and clean of missing values, datatypes were streamlined into two types (object, and non-object) to enable easy visualizations for the purpose of exploratory data analysis. Data was then pre-processed using label-encoding and one-hot-encoding, and then data was split and model trained. Due to the data being previously categorical and numerical, the range of the encoding was wide and so I scaled the data using `sklearn.preprocessing`'s `StandardScaler`, then fitted it to the training data and applied transformations to the data.

I warmed up by doing a baseline model using Logistic Regression and took note of the F1 Score.

After which I got down to serious business by setting up my first machine learning model `(Logistic Regression)`, then getting down and dirty with hyperparameter tuning. Using the best hyperparameters and estimators (from my tuning), I fitted them to the training data, predicted with the test data, to obtain the classification report for the model. The machine learning Logistic Regression model's F1 Score topped the baseline model. I am happy.

Next, I carried out the same steps with my second machine learning model `(Random Forest)` - Setup the classifier, hyperparameter tuning, fitting... you get the drift. This new model's F1 Score topped the previous (Logistic Regression). With **Random Forest as my best model**, I moved on to predicting and evaluating using my test data.

###### Comparison of Random Forest and Logistic Regression Model's Metrics
![ML model comparison](https://github.com/JoySeedhe/-Instagram-Top-Posts-Machine-Learning-Model/blob/main/python/images/ML%20Models%20Comparison.JPG)</br></br>

### Results
Fortunately, the model metrics for the test data did not vary significantly (vs the training data). 
###### Classification Report of Test Data using Random Forest
![random forest test data classification report](https://github.com/JoySeedhe/-Instagram-Top-Posts-Machine-Learning-Model/blob/main/python/images/RF%20on%20Test%20Data.JPG)</br></br>

The results look good as well with immaterial FPs and FNs.

###### Results in a Confusion Matrix Visualization
![confusion matrix](https://github.com/JoySeedhe/-Instagram-Top-Posts-Machine-Learning-Model/blob/main/python/images/Confusion%20Matrix.JPG)</br></br>

Having plotted the features importance into a visualization, we can deduce that the top "super" variables are `like_count`, `comments_count`, and `followers_count`.

![features importance](https://github.com/JoySeedhe/-Instagram-Top-Posts-Machine-Learning-Model/blob/main/python/images/Features%20Importance.JPG)

The data-driven approach suggests to focus on creating content which:
* aim to provide instant gratification --> `like_count`
* encourages engagement --> `comments_count`
* is addictive --> `followers`

While the data highlights the key variables that influence post performance, it's worth remembering that success on platforms like Instagram isn't purely mathematical. Creativity, timing, and human connection play just as important a role—because not everything that matters can be measured.
</br></br>:)
