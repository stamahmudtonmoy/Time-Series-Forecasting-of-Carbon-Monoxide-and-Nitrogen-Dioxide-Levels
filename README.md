# Time-Series Forecasting of Carbon Monoxide and Nitrogen Dioxide Levels

## Project Overview

This project implements a time-series forecasting solution for daily or hourly concentrations of Carbon Monoxide (CO) and Nitrogen Dioxide (NO₂). The goal is to build predictive models that can forecast future gas levels based on historical data.

The workflow is structured into six main steps, from data preparation to model evaluation and visualization.

## Project Workflow

### Step 1: Data Preprocessing

* #### Objective: Prepare the raw dataset for analysis and modeling.

* #### Actions:

* Combined the Date and Time columns into a single datetime column.

* Set the datetime column as the index for the DataFrame, which is a crucial step for time-series analysis.

* Replaced any invalid or missing data points (represented as -200 in the dataset) with NaN.

* Handled missing values for the target variables (CO(GT) and NO2(GT)) using linear interpolation to maintain data continuity.

* Resampled the data to a daily frequency by taking the average of all hourly measurements within a day. This reduces noise and makes long-term trend analysis more manageable.

* Detected and handled outliers in CO(GT) and NO2(GT) by using the Interquartile Range (IQR) method and capping extreme values to prevent them from skewing the model's training.

### Step 2: Exploratory Data Analysis (EDA)

* #### Objective: Understand the underlying patterns and characteristics of the data.

* #### Actions:

* ##### Trend Analysis: Visualized the long-term trends of CO(GT) and NO2(GT) to identify any overall increases or decreases over time.

* ##### Seasonality: Plotted the average daily concentrations of CO(GT) and NO2(GT) to identify daily seasonal patterns. This helps in understanding peak pollution hours.

* ##### Correlation Analysis: Generated a correlation heatmap to explore the relationships between CO(GT), NO2(GT), and other environmental factors like temperature, relative humidity, and absolute humidity.

### Step 3: Feature Engineering

* #### Objective: Create new variables from the existing data to improve model performance.

* #### Actions:

* Created lag features for both CO(GT) and NO2(GT). These features capture the values from previous time steps, allowing the model to learn from the past.

* Added time-based features such as the hour of the day, day of the week, and month. These help the model identify and learn daily and monthly seasonal patterns.

* Incorporated external environmental factors (T, RH, AH) as additional predictors.

### Step 4: Time-Series Forecasting

* #### Objective: Train predictive models to forecast future gas levels using various approaches.

* #### Actions:

* Split the dataset into a training set and a testing set.

* Trained a Linear Regression model (Machine Learning) for CO(GT).

* Trained an ARIMA model (Statistical) for NO2(GT).

* Trained a Deep Learning model, specifically a Long Short-Term Memory (LSTM) network, for CO(GT). This model is particularly effective at learning long-term dependencies in sequential data.

### Step 5: Model Evaluation

* #### Objective: Assess the performance of the trained models.

* #### Actions:

* Evaluated all three models (Linear Regression, ARIMA, and LSTM) using standard time-series forecasting metrics:

* Mean Absolute Error (MAE): The average absolute difference between actual and predicted values.

* Root Mean Squared Error (RMSE): The square root of the average of squared differences. This penalizes larger errors more.

* Mean Absolute Percentage Error (MAPE): The average percentage error of the predictions, providing an intuitive measure of accuracy.

* R-squared (R^2): The proportion of variance in the dependent variable that is predictable from the independent variable(s).

* The metrics are printed to the console for a quantitative comparison of the models' accuracy.

### Step 6: Visualization and Insights

* #### Objective: Visualize the model's predictions and gain insights from the results.

* #### Actions:

* Plotted the actual values against the predicted values for each of the three models on the test set. This visual comparison helps in understanding how well the models are performing.

* Generated and visualized forecasts for a period of 30 future days, extending the model's predictions beyond the historical data.

* Highlighted seasonal patterns and provided actionable recommendations based on the predicted trends, offering practical insights from the project's findings.

## Conclusion

This project successfully demonstrates a complete workflow for time-series forecasting, comparing different modeling approaches. While the models used here are a good starting point, future work could involve exploring more advanced techniques, using more sophisticated feature engineering, and conducting hyperparameter tuning to further improve forecasting accuracy.
