# Predicting the Fare of a Taxi Ride in Chicago, Illinois.

Experimenting with different features to build a Linear Regression model and tuning its hyperparameters to get as close to ground value as possible.

## Project Workflow

1. **Data Ingestion**
   - Load dataset into a Pandas DataFrame
   - Select relevant features for analysis

2. **Exploratory Data Analysis (EDA)**
   - Generate descriptive statistics
   - Compute correlation matrix to identify feature importance
   - Visualize relationships using pair plots

3. **Model Development**
   - Train baseline model using a single feature (`TRIP_MILES`)
   - Extend model with additional feature (`TRIP_MINUTES`)

4. **Hyperparameter Analysis**
   - Evaluate impact of learning rate on convergence
   - Study effect of batch size on training dynamics

5. **Model Comparison**
   - Compare single-feature vs multi-feature models using RMSE
   - Analyze performance improvements

6. **Prediction & Evaluation**
   - Generate predictions on sample data
   - Measure error using L1 loss and RMSE

## Tech Stack

#### Core Libraries
- Python
- NumPy — numerical computation
- Pandas — data loading and manipulation

#### Machine Learning
- TensorFlow — backend for model training
- Keras — model definition and training interface

#### Data Visualization
- Plotly — interactive visualizations (pair plots, scatter matrices)
- Matplotlib — training metrics and loss curves

## DataSet

The [dataset](https://www.google.com/url?q=https%3A%2F%2Fstorage.mtls.cloud.google.com%2Fmlcc-nextgen-internal%2Fchicago_taxi_train.csv)

- subset of [Taxi Trips](https://data.cityofchicago.org/Transportation/Taxi-Trips-2013-2023-/wrvz-psew/about_data)
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

## Model Training

A simple **linear regression model** is implemented using Keras.

#### Model Architecture
- Single dense layer
- One output unit
- Represents a linear mapping from input features to fare

#### Training Objective
- Loss Function: Mean Squared Error (MSE)
- Optimization Goal: Minimize prediction error between actual and predicted fares

### w/ 1 feature

TRIP_MILES - since strongest correlation with FARE (label) - for first training run
- took 5 epochs to converge on final model
- model fit data fairly well
- Root Mean Square Error (RMSE) = $3.8228
  
### w/ 2 features

let’s see if we can do better with 2 features now:
TRIP_MILES as before with the addition of:
TRIP_MINUTES
→ derived from the feature TRIP_SECONDS in the dataset.

- we see the model with 2 features performs a bit better than that of one feature alone. After hyperparameter tuning we see that the RMSE values are, for:
    - 1 feature model = 3.6411
    - 2 features model = 3.4978   <br>
      → which puts the second model predictions $0.143 closer to the actual observed values on             average.   <br>
we observe the same in the cmoparison plots as well.
- we use TRIP_MINUTES > TRIP_SECONDS since the mean:
   - TRIP_MILES = 8.3 miles
   - TRIP_SECONDS = 1320 seconds
   - TRIP_MINUTES = 22 minutes   <br>
      → order of magnitude of TRIP_MILES and TRIP_MINUTES is closer.

#### Scatter Plot

To see how well the training of the model is with both features.

Scatter plot of the features vs the label is a 3D plot → TRIP_MILES, TRIP_MINUTES (x, y) vs FARE (z-axis).

## Making Predictions

Model seems to do fairly well in predicting fare for a taxi ride in Chicago, Illinois in May of 2022.

Most of the predicted values do not vary significantly from the observed value judging by the L1_LOSS data.



#



## Further Research

Chicago Taxi fares are calculated, in the atuality, w/ this formula:   <br>
FARE = 2.25 * TRIP_MILES + 0.12 * TRIP_MINUTES + 3.25

Let's see if our model sensed the same:   <br>
Model's output → the weights and bias
⇒ 

## Next Steps

[] Run model on TRIP_SECONDS instead of TRIP_MINUTES   <br>
[] Split Data into Training and Test Sets
