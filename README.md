# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
# Date: 06-09-25
# Name: A.Nabithra

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Load Tesla data (make sure file path is correct)
data = pd.read_csv("Tesla.csv", parse_dates=['Date'], index_col='Date')

# Extract the 'Close' price
close_prices = data['Close'].dropna().values
N = len(close_prices)

# Define lags
lags = range(35)
autocorr_values = []

# Mean and variance
mean_data = np.mean(close_prices)
variance_data = np.var(close_prices)

# Autocorrelation calculation
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((close_prices[:-lag] - mean_data) * (close_prices[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)  # Normalize

# Plot
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Tesla Close Prices')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```
### OUTPUT:

<img width="1252" height="710" alt="image" src="https://github.com/user-attachments/assets/60c93439-68d0-473f-924e-faf0f2cfef6f" />


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
