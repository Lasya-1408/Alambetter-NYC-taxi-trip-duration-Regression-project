# NYC-taxi-trip-duration-prediction
The given dataset contains trip duration in seconds of rides taken by a taxi company in New York City (NYC) which includes id, vendor_id, pickup_datetime, dropoff_datetime,passenger_count, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude, store_and_fwd_flag. Here, target variable is trip duration and all other variables are considered independent variables. The correlation between few variables can be found to analyse the trip duration. From the provided dataset, univariate and bivariate analyses is performed to determine which factors have contributed to maximum trip duration, at what time of the day there were more number of bookings, which month they had most rides and many other factors which effect number of rides. After performing exploratory data analysis (EDA), we perform tasks like feature engineering, feature selection, splitting the data into train and test, model building, fit the data to algorithm of selected model, predict the outputs, calculating the error and r2 score, concluding whether the model is predicting accurate results or not.
# Table of contents
* Data cleaning and manipulation
* Data Visualizations
* Feature Engineering
* Model implementation and feature importance
* Conclusion 
* Tools
# Data cleaning and manipulation
Before data manipulation, the dataset has 1458644 rows and 11 columns. Firstly, id column is removed as it contains as many number of rows as unique numbers. Secondly, in the dataset we have pickup_latitudes, pickup_longitudes, dropoff_latitudes, and dropoff_longitudes from which we have extracted the distance between them. Further we have pickup_time and dropoff_time from which day, month, time are extracted. Then we copied the dataset to nyc_df so that the original data is not lost. Finally, we have removed pickup_time and dropoff_time from nyc_df as they are no longer useful in visualization and model building. Now the new dataset has 1458644 rows and 21 columns.
# Data Visualizations
* Trip duration distribution
* Vendor id distribution
* Passenger count distribution
* Stored and fwd flag distribution
* Distance distribution
* Pickup month number distribution
* Pickup day name distribution
* Pickup time distribution
* Number of trips made by vendors
* Sub plots of number of passengers travelled and distance covered in each trip
* Pickup day name vs Trip duration
* Pickup time vs Trip duration
* Trips per pickup month number
* Distance travelled by vendors
* Passenger count vs distance
* Distance travelled per day
* Distance travelled per time of the day
* Distance travelled per month
* Vendor id vs Passenger count
# Feature Engineering & Data Pre-processing
## Multicollinearity  
* Distribution plots of all numerical variables including mean and median.
* From the Heatmap, we notice that distance, pickup_longitude, pickup_latitude, drop_off latitude, dropoff_longitude, pickup_month_number, dropoff_month_number, dropoff_daynum, pickup_hour, and dropoff_hour are having significant correlation with trip duration. Also, we conclude that dropoff_hour, dropoff_daynum, dropoff_month_number, dropoff_weekday and trip_duration_split are strongly correlated to pickup_hour, pickup_daynum, pickup_month_number, and trip_duration respectively. Hence, they can be removed from the dataset during building a model. 
* To understand whether there is a correlation among the numerical variables, we apply variance inflation factor.
* passenger_count, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude, and distance are finalised as numerical columns.
## Handling outliers
* From the boxplots, we notice that there are outliers in passenger count, distance, and trip duration variables. Hence we treat them using quantile method. Outliers are nothing but those points which doesn't follow the trend.
* After treating outliers, the new dataset has 1136749 rows and 22 columns.
## Categorical encoding
* From the dataset, we see that store_and_fwd_flag, pickup_time, and pickup_dayname are the categorical variables. As there are more categories, instead of manually assigning integers, we used one hot coding and converted these columns to numerical variables.
* Therefore, now the dataset has 1136749 rows and 32 columns.
## Feature Selection
vendor_id, passenger_count, distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude, Day_Friday, Day_Monday, Day_Saturday, Day_Tuesday, Day_Wednesday, Day_Thursday, Day_Sunday, store_and_fwd_flag_Y, store_and_fwd_flag_N, pickup_month_number, and pickup_hour are selected as X variables.
# Model Implementation
Now coming to the model implementation, following are the models used.
* Linear regression
* Decision tree
* Decision tree with cross validation
* Random forest
* Random forest with cross validation
* XGBoost
* XGBoost with cross validation
# Feature Importance
* From the feature importance plot, we see that distance is the most important variable for trip duration as they are directly proportional. Also, along with that Day_sunday, Day_saturday, pickup_hour, day_monday, and dropoff_latitude are the other top 5 variables which effect trip duration.
# Conclusion
## Conclusion from EDA
After performing few analysis for the given dataset, it can be concluded that
* From the analysis, trip duration column is plotted by applying log transformation on it which shows a normal distribution.
* Most of the trips had single passenger.
* Most of the records in the distance column are noted zero which will lead to a difficult situation when performing data analysis.
* Evenings are the busiest as we can see that maximum rides are booked around evening.
* Most of the long rides have taken place on weekends as they are holidays for everyone, people often plan for longer trips.
* Maximum trips had trip duration of about 30 minutes.
Also, strategies to increase the passengers could be by offering weekly or monthly memberships, giving discounts on weekends, and ensuring safety so that customers are more attracted to book taxi.
## Conclusion from Model building
First we performed feature engineering which involves
* In multicollinearity section, we finalised numerical columns with the help of correlation values and variance inflation factor.
* Then we found outliers in passenger_count, distance, and trip_duration columns, using quantile method we removed them.
* Then performed categorical encoding for store_and_fwd_flag and pickup_dayname.
* Vendor_id, passenger_count, distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude, Day_Friday, Day_Monday, Day_Saturday, Day_Tuesday, Day_Wednesday, Day_Thursday, Day_Sunday, store_and_fwd_flag_Y, store_and_fwd_flag_N, pickup_month_number, and pickup_hour are selected for model building.
* Now coming to the model implementation and their respective evaluation metrics for test data. Here we considered MSE and r2 score as evaluation metrics.
* On comparing the models built, we noticed that XGBoost performed better with low MSE and high r2 score. Also, looking at the feature importance, we can say that distance had the highest contribution followed by day_sunday, day_saturday, pick_hour, and day_monday.
# Tool
Google colab 
