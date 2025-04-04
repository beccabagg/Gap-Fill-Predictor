# Gap-Fill-Predictor
Overview
The USGS Discharge Analyzer is an R Shiny application designed to retrieve, analyze, and model USGS stream discharge data. The app specializes in predicting values for specified time periods by automatically evaluating multiple time series models and selecting the most accurate one based on error metrics.

Features
USGS Data Retrieval: Easily retrieve discharge data from any USGS monitoring station by site number
Multi-Model Prediction: Apply multiple time series models to predict discharge values for specified date ranges
Automatic Model Selection: The app evaluates multiple models and selects the best one based on RMSE and other error metrics
Interactive Visualization: Compare model performances with interactive plots
Boundary Continuity: Option to ensure smooth transitions at the boundaries of predicted sections
Customizable Training: Control how many data points before and after the target range to use for model training
Data Export: Download raw data and model prediction results for further analysis
Models Included
The app tests multiple time series models on your data:

ARIMA: Auto-regressive integrated moving average model
Moving Average: Simple moving average imputation
Kalman Filter: State space model using Kalman filtering
Spline: Cubic spline interpolation
Stine: Stineman interpolation
Exponential Smoothing: Time series forecasting method
Installation and Dependencies
Required R Packages
The app requires the following R packages:

Installation
To run the app locally:

Clone this repository or download the script
Open R or RStudio
Install required packages (if not already installed):
Run the app:
Usage Guide
Data Retrieval
Enter a valid USGS site number (e.g., "01646500")
Select date range and parameter code (discharge or gage height)
Click "Get Data" to retrieve data from USGS
Model Prediction
Select a date range for which you want to replace or predict values
Specify training parameters:
How many data points before/after the range to use for model training
Whether to ensure continuity at boundaries
Click "Run All Models" to execute all time series models
View the results with either the best model or all models displayed
Compare model performance metrics in the table
Downloading Results
Use "Download Data" to save the raw USGS data
Use "Download Best Model Results" to save the model prediction results, including:
Model comparison metrics
Best model prediction values
Metadata about the analysis
How It Works
The Model Prediction Process
The app identifies the time period specified for prediction
It temporarily removes existing data in this period to simulate a gap
Multiple time series models are applied to predict values for this period
Each model's predictions are compared to the original values
Performance metrics (RMSE, MAE, bias, correlation) are calculated
The best-performing model is identified and highlighted
Results are displayed in interactive visualizations and tables
Boundary Continuity
When boundary continuity is enabled, the app ensures that the predicted values connect smoothly with the existing data at the boundaries of the prediction range, preventing artificial discontinuities.

Use Cases
Data Quality Control: Identify and replace erroneous measurements
Gap Filling: Predict missing data in discharge records
Comparative Analysis: Compare the performance of different time series models on hydrological data
Data Exploration: Interactive exploration of USGS discharge data
Method Selection: Determine which time series method works best for a specific stream or time period
Notes
The app connects to the USGS National Water Information System (NWIS) to retrieve data
Performance may vary depending on the station and time period selected
Larger date ranges may take longer to process when running models
Credits
Uses the USGS dataRetrieval R package for data access
Implements models from the imputeTS and forecast packages
Visualizations created with ggplot2 and plotly
