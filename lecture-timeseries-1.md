# Lecture Timeseries (1)

## Lesson goals

- The student recognizes time series data as a distinct type of data and knows the techniques for making predictions using this type of data.
	- Bloom: weten
	- Miller: weten
	- Final qualifications:
		C. Data analytics: 
            > The Master's graduates apply appropriate data science and machine learning algorithms and techniques for complex data analysis. They prepare data, including selecting, cleaning, and combining data from various sources. They determine algorithms suitable for data analysis and establish the test design. They build models and evaluate them by interpreting model results, predefined success criteria, and the test design. They decide on follow-up actions based on the evaluation results of the model.
        
## Preparation

- Read Géron ch. 15 from "Forecasting a time series" until but not including "Preparing the Data for Machine Learning Models".

## Lesson duration

- 2:30 including 3 15 min breaks

## Block 1 (50 min)

- Energizer: what did you read in Géron?
  - What is a time series? data with values at different time steps, usually (should be: always except in *very* special circumstances) at regular intervals.
  - Used for forecasting
  - Example application: forecast number of passengers of a public transport system
  - Seasonality: pattern repeats.
  - Naive forecasting: copying a past value to make forecasts.
  - Lagged time series
  - Measure the quality of a forecast: calculate mean absolute error / mean absolute percentage error
  - ARMA Model (autoregressive moving average): weighted sum of lagged values, adds moving average
  - Differencing: approximates the derivative (gives slope at each time step). This eliminates linear trends. $d$ consecutive rounds of differencing computes an approximation of the $d^{th}$ order derivative of the time series.
  - ARMA is a family of models. Examples of other ARMA models: SARIMA (seasonal ARIMA)

- Overview
  - A time series is a sequence of observations of one or more variables. These observations occur in successive order over some period of time, usually (but occasionally not) at regular intervals.
  - In many time series observations are closely related to each other.
  - This means an observation made at some point in the past can help predict an observation that is made at some later point in time: forecasting.
  - The default forecasting technique is to simply state that the next observation will be identical to the last observation. This works surprisingly well. Later on during this lesson we will learn what to do when it doesn't.

- Demonstration: naive forecast with example.

- Slightly less naive forecasting: ARMA
  - Apply some function to all previous observations or to a subset of previous observations (only the last 10 observations, for example): $y_t = f(y_1, ..., y_{t-1}) + \epsilon_t$ ($\epsilon$ is some error). The forecast value is $\hat{y}_{t+1} = f(y1, ..., yt)$.
  - This technique is called **ARMA**: **a**uto**r**egressive **m**oving **a**verage:
    - AR: $Yt = \beta_1 y_{t - 1} + \beta_2 y_{t - 2} ... + \beta_k y_{t -k}$
    - MA: $Yt = \alpha_1 \epsilon_{t-1} + \alpha_2 \epsilon_{t-2} ... + \alpha_k \epsilon_{t-k}$ : this is the sum of the residuals / errors for each observation done at time $t - k$ (the difference between the observed value and the predicted value).
    - ARMA combines the two, by summing them: $Yt = \beta_1 y_{t - 1} + \alpha_1 \epsilon_{t-1} + \beta_2 y_{t - 2} + \alpha_1 \epsilon_{t-2}... + \beta_k y_{t -k} + \alpha_k \epsilon_{t-k}$ 
    - Demonstration: show an example of ARMA that works and an example where seasonality makes it not work.
    - ARMA assumes the time series is *stationary*. "Stationary" means there is no *seasonality* (recurring pattern) in the data. In the second example there was seasonality, which is why it didn't work.

- DOEN: hoe haal je seasonality weg?
- DAn: demo Raoul laten zien


## Block 2 (50 min)

- Reminder: how to measure the quality of a forecast? MAPE, MAE
- Seasonality
- Differencing

## Block 3 (50 min)

- TODO

## Material to cover

### Application of time series

### ARMA

### Seasonality

### MAPE

### MAE

### Naive forecasting

### Differencing

### Sources

Gebruik materiaal Raoul MADS-DAV les 3
	- Basis: https://github.com/raoulg/MADS-DAV/blob/main/notebooks/03.2-statistics-of-time.ipynb
	- Les Raoul gaat ook in op Fourier (mss andere les)
