# NYCTaxiFarePrediction
New York City Taxi Fare Prediction - Kaggle Challenge
https://www.kaggle.com/c/new-york-city-taxi-fare-prediction

# Goal 
the taxi fare problem is one of several real-world problems that are used as case studies in the series of courses. Here, we are predicting the fare amount (inclusive of tolls) for a taxi ride in New York City given the pickup and dropoff locations. While you can get a basic estimate based on just the distance between the two points, this will result in an RMSE of $5-$8, depending on the base line linear model. Challenge is to do better than this using Machine Learning techniques!

# Data Cleaning and Extra Features Added
a) Converting datatype of pickup_datetime from object type to datetime Datatype for further processing.
b) For pre-processing, I identified the vincenty distance from given longitudes and latitudes.
c) Converted UTC to ET (Easterm Time ) and subsequently to EDT and EST. Assumed that EST is valid from Nov-Feb and EDT is valid from Mar-Oct.
d) In the final dataset, I kept only those rows which had either their pickup location or the drop off location in the NYC co-ordinates. Found the boundary of co-ordinates of NYC from mapdevelopers.com (Ref: https://www.mapdevelopers.com/geocode_bounding_box.php
e)	I created three more columsns as 
          - Season: Winter,Spring, Summer, Fall (Season Codes: 1, 2, 3, 4)
          - Day of Week: Monday through Sunday (Day of Week Code: 0-6)
          - Time of Day: Categorized time of day into 6 classes – Midnight[12AM-4AM], Dawn[5AM-6AM], Morning[7AM-11AM], Afternoon[12PM-             15PM], Evening[16PM-19PM],Night [20PM-23PM] to see f the time of day has any impact upon fare prices or number of rides.


# Approach
I have used three ML models:
a) Logistic Regression (Root Mean Square Error: 5.84)
b) Decision Tree (Root Mean Square Error: 4.19)
c) Random Forest (Root Mean Square Error: 3.5)

Out of these three, Random Forest based model is giving the least RMSE (3.5 approx).

# Parameter Tuning in Random Forest Algorithm
The RMSE got decreased significantly when I increase the number of trees  and increased the depth of the tree as well in the Random Forest based Model. Since higher the number of trees the better to learn the data but a slow down in the training process was observed. So, I finally kept the number of trees to be 20 and depth of the tree to be 20. 


# Interesting Finding
The graph between year of the ride taken and the distance travelled by the taxi, shows an interesting relationship. As it can be seen that people used to take many rides in the year of 2009, 2010 and 2011. But after 2011, a decline in data points can be seen which speaks about people not taking Yellow and Green taxis to travel. In May 2011, Uber was launched in NYC and lured many customers with its low prices. Hence, instead of taking Yellow Cab or Green Cab, people preferred taking Uber which resulted in decline of taxi rides in the year 2012, 2013, 2014 and 2015.

