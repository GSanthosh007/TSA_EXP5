# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 13.05.26


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
# EXP 5

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
from statsmodels.tsa.seasonal import seasonal_decompose

df = pd.read_csv("/content/final_website_stats.csv")

df['timestamp'] = pd.to_datetime(df['timestamp'], format='%d-%m-%Y')

df.set_index('timestamp', inplace=True)

website_data = df['page_views']

decomposition = seasonal_decompose(
    website_data,
    model='additive',
    period=30
)

trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

# ---------------- ORIGINAL DATA ---------------- #
plt.figure(figsize=(12, 6))

plt.plot(website_data, label='Original Website Data')

plt.title('Original Website Page Views')
plt.legend()

plt.show()

# ---------------- SEASONAL COMPONENT ---------------- #
plt.figure(figsize=(12, 6))

plt.plot(seasonal, label='Seasonal Component', color='orange')

plt.title('Seasonal Component')
plt.legend()

plt.show()

# ---------------- TREND COMPONENT ---------------- #
plt.figure(figsize=(12, 6))

plt.plot(trend, label='Trend Component', color='green')

plt.title('Trend Component')
plt.legend()

plt.show()

# ---------------- RESIDUALS ---------------- #
plt.figure(figsize=(12, 6))

plt.plot(residuals, label='Residuals', color='red')

plt.title('Residuals')
plt.legend()

plt.show()

# ---------------- COMPLETE DECOMPOSITION ---------------- #
plt.figure(figsize=(12, 8))

decomposition.plot()

plt.show()
```



### OUTPUT:

# PLOTTING THE DATA:
<img width="1245" height="652" alt="image" src="https://github.com/user-attachments/assets/e4ba96a2-8896-4282-a0a6-37ca885115b8" />


# SEASONAL PLOT REPRESENTATION :
<img width="1231" height="652" alt="image" src="https://github.com/user-attachments/assets/fa67e89f-316d-4a67-b247-954eb59f97a1" />



# TREND PLOT REPRESENTATION :
<img width="1242" height="657" alt="image" src="https://github.com/user-attachments/assets/6a0abdd4-ee27-40c8-bed2-2c85695e12d0" />

# RESIDUALS:

<img width="1252" height="657" alt="image" src="https://github.com/user-attachments/assets/3e01ae5b-f79a-4ed6-bb89-6aea27da8fea" />


# OVERAL REPRESENTATION:

<img width="827" height="616" alt="image" src="https://github.com/user-attachments/assets/f4a152a1-fd21-4202-a966-ae79ee65080a" />




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
