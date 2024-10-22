# NVIDIA Stock Price Analysis and Forecasting

## Project Overview

This project aims to explore the historical trends and patterns in NVIDIA's stock price using a dataset spanning 20 years. By employing technical analysis and machine learning techniques, we seek to identify significant trends, patterns, and potential future price movements.

### Dataset

The dataset provides daily stock price data for NVIDIA from January 2, 2004, to January 1, 2024. It includes the following attributes:

- **Date**: The date of the stock price record.
- **Open**: The opening price of the stock on that day.
- **High**: The highest price reached during the day.
- **Low**: The lowest price reached during the day.
- **Close**: The closing price of the stock on that day.
- **Volume**: The total number of shares traded on that day.

### Outcome Variable

The **Close** (Close Price) was selected as the most suitable outcome variable for the following reasons:

1. **End-of-Day Value**: The close price represents the final price at which the stock traded during the day, reflecting the market’s consensus value.
2. **Widely Used**: It is commonly used in financial analysis, technical indicators, and trading strategies.
3. **Stability**: Compared to intraday prices (Open, High, Low), the close price is less volatile and more stable, making it a reliable indicator for trends and patterns.

## Model Training and Evaluation

Various models were trained and compared, including Polynomial Regression, Random Forest, and LSTM. The Polynomial Regression model emerged as the best performer with the following metrics:

- **Mean Squared Error (MSE)**: 0.6738
- **R² Score**: 0.9950

### Time Series Forecasting

The code below performs time series forecasting of stock closing prices using a polynomial regression model. The process begins by filtering the dataset to include only data after January 1, 2020, and selecting relevant features such as Low, High, Open, 200_MA, and ATR.

The data is then scaled using `StandardScaler` to ensure that each feature contributes equally to the model. A polynomial regression model is created and fitted to the scaled data, allowing for capturing non-linear relationships between the features and the target variable, Close.

Future timestamps are generated for a 6-month period, during which the model predicts future closing prices based on the last known features. To simulate market variability, random multipliers are applied to the predicted values, adjusting the Low, High, and Open features for each iteration. The model also recalculates the 200-day moving average and Average True Range (ATR) for the updated features.

Historical predictions are generated to assess model performance against actual closing prices. The predicted historical and future values are combined for visualisation, with actual prices shown alongside historical predictions and future forecasts.

## Conclusion

Overall, this approach leverages polynomial regression and random sampling techniques to provide insights into stock price movements, highlighting the model's capacity to capture variability in financial data.
