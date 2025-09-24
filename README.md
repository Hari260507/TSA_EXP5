# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 24/09/2025


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
# === Import libraries ===
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# === Step 1: Load Tomato dataset ===
data = pd.read_csv("Tomato.csv")

# Convert 'Date' to datetime & set as index
data['Date'] = pd.to_datetime(data['Date'])
data = data.sort_values('Date')
data = data.set_index('Date')

# === Step 2: Perform seasonal decomposition ===
# Assuming daily data → roughly 365 days in a year.
# If your data is weekly/monthly, change the period accordingly.
decomposition = seasonal_decompose(data['Average'], model='additive', period=365)

# === Step 3: Plot the decomposition manually ===
plt.figure(figsize=(10, 12))

# 1️⃣ Original Series
plt.subplot(411)
plt.plot(data['Average'], label='Average Tomato Price')
plt.legend(loc='upper left')
plt.title('Tomato Average Price')

# 2️⃣ Trend
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend')

# 3️⃣ Seasonal
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonality', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality')

# 4️⃣ Residual
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residuals')

plt.tight_layout()
plt.show()

```
### OUTPUT:
<img width="1233" height="358" alt="image" src="https://github.com/user-attachments/assets/8e277cf6-153a-492c-b2a3-1e0e1c3f2466" />
<img width="1232" height="377" alt="image" src="https://github.com/user-attachments/assets/2a040537-2af7-4b89-8a45-3d5b08ffbb5f" />
<img width="1228" height="377" alt="image" src="https://github.com/user-attachments/assets/3ad64722-ca1a-4303-8305-35cee6aa55cb" />
<img width="1232" height="375" alt="image" src="https://github.com/user-attachments/assets/a66e8d2a-88d1-4e1e-8200-11c680790d7c" />



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
