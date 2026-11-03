# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

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
```import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

data = pd.read_csv('/content/gld_price_data.csv')

data = data['GLD'].dropna().values

N = len(data)

lags = range(35)

autocorr_values = []

mean_data = np.mean(data)
variance_data = np.var(data)

normalized_data = (data - mean_data) / np.sqrt(variance_data)

# Go through lag components one-by-one
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Display the graph
plt.figure(figsize=(10, 6))

plt.stem(lags, autocorr_values)

plt.axhline(y=0, color='red', linewidth=1.5)

plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')

plt.grid(True)

plt.show()
```

### OUTPUT:
<img width="1002" height="655" alt="image" src="https://github.com/user-attachments/assets/502fad90-b301-435c-a025-dea357ae4705" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
