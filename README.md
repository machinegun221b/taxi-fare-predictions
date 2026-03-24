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

1. Loading the Dataset to pandas DataFrame
2. Exploring the dataset
    1. Generate Correlation matrix
    2. Visualise relationships in DS
3. Train Model
    1. w/ 1 feature
    2. w/ 2 features
4. Compare Experiments
5. Model Validation

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

#### Evaluation
- RMSE (Root Mean Squared Error) — model performance metric
- Loss curves — training convergence analysis

compare training run using RMSE and loss curves
several python libraries for - data manipulation, ML tasks and data visualisation.

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

## Training the Model

Model Topography: Simple Linear Regression Model 
i.e., single node in a single layer.

w/ keras
minimising MSE

### w/ 1 feature

TRIP_MILES - since strongest correlation with FARE (label) - for first training run
- took 5 epochs to converge on final model
- model fit data fairly well
- Root Mean Square Error (RMSE) = $3.8228

### Experimenting with Hyperparameters

To find the best set of hyperparameters to train our model.

1. LR = 1                          BS = 50
    - impact on model training - 
2. LR = 0.0001                BS = 50
    - impact on model training -
3. LR = 0.001                  BS = 500
    - impact on training results -
  
### w/ 2 features

let’s see if we can do better with 2 features now:
TRIP_MILES as before with the addition of:
TRIP_MINUTES
→ derived from the feature TRIP_SECONDS in the dataset.

- 2 features better than 1?
- TRIP_SECONDS > TRIP_MINUTES?
- Model Accuracy in real world?

