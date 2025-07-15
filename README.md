# CIND-820-Project
Big data analytics (CIND820) final project for TMU Certificate in Data Analytics

# CPI Inflation Forecasting for the Canadian Economy

## Project Overview

This repository contains the code and analysis for a research project focused on forecasting the Consumer Price Index (CPI) inflation rate for the Canadian economy using various Machine Learning (ML) techniques. The project involves comprehensive data preprocessing, feature engineering tailored for time series data, exploratory data analysis, and the development and evaluation of multiple forecasting models.

## Project Stages

The project was executed through the following key stages:

1.  **Data Acquisition and Initial Filtering**:
    * Loading the raw CPI dataset.
    * Filtering data for "Canada," "All-items," and "2002=100" base, within the 2015-2025 period.
    * Parsing dates and setting the time series index.

2.  **Data Preprocessing (Log Transformation, Differencing)**:
    * Applying a natural logarithm transformation to the CPI series.
    * Calculating the first difference of the log-transformed CPI to derive the monthly inflation rate (`log_diff_cpi`), which serves as the target variable. This step was crucial for achieving stationarity.

3.  **Feature Engineering**:
    * **Lagged Inflation Values**: Creation of lagged features (up to 12 months) to capture temporal dependencies.
    * **Rolling Statistics**: Calculation of 3, 6, and 12-month rolling means and standard deviations. These features were carefully lagged by one period to prevent data leakage and provide insights into recent trends and volatility.
    * **Seasonal Components**: Inclusion of sine and cosine terms (Fourier series) with a 12-month period to explicitly model annual seasonality.

4.  **Exploratory Data Analysis and Stationarity Testing**:
    * Visualization of the monthly inflation rate and its 12-month rolling standard deviation to understand trends and volatility.
    * Q-Q plot to assess the normality of the variable distribution.
    * Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots for both the raw CPI and transformed series to analyze temporal correlations and confirm stationarity.
    * Augmented Dickey-Fuller (ADF) test to formally confirm the stationarity of the transformed series.

5.  **Model Development and Training**:
    * Splitting the dataset into training and testing sets chronologically (last 24 months for testing) to ensure realistic evaluation.
    * Standardizing all engineered features using `StandardScaler`.
    * Training four forecasting models:
        * **Naive Forecast**: A simple baseline predicting the current value as the previous month's actual value.
        * **Random Forest Regressor**: A powerful ensemble tree-based model.
        * **Gradient Boosting Regressor**: Another robust ensemble tree-based model.
        * **K-Nearest Neighbors (kNN) Regressor**: A non-parametric, instance-based learning algorithm.


