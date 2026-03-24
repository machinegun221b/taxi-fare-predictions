# Predicting the Fare of a Taxi Ride in Chicago, Illinois.

Experimenting with different features to build a Linear Regression model and tuning its hyperparameters to get as close to ground value as possible.

## Project Workflow

1. Loading the Dataset to pandas DataFrame
2. Exploring the dataset
    1. Generate Correlation matrix
    2. Visualise relationships in DS
3. Train Model
    1. w/ 1 feature
    2. w/ 2 features
4. Compare Experiments
5. Model Validation

## DataSet

The dataset - https://www.google.com/url?q=https%3A%2F%2Fstorage.mtls.cloud.google.com%2Fmlcc-nextgen-internal%2Fchicago_taxi_train.csv 

- subset of Taxi Trips https://data.cityofchicago.org/Transportation/Taxi-Trips-2013-2023-/wrvz-psew/about_data
- 2 day period from May 2022.

### DataSet Exploration

Using the `DataFrame.describe` method, we see that:
- the max fare = $159.25
- mean distance across all trips = 8.2895 miles
- total number of cab companies in DS = 31
- most frequent payment type = credit card
- missing features in the data = None
in the dataset.

### w/ Correlation Matrix

We see the TRIP_MILES correlation to FARE is 0.9753 being the highest of the 3 features.
Hence, the strongest feature correlation to label.

### w/ Pair Plot to Visualise relationships in the Dataset

Grid of pairwise plots - to visualise the relationship of each feature with all the other features.

