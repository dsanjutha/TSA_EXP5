# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 03.10.2026



### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

**Dataset name:** cars_dataset

**Software required/tool required: google colab/Jupyter**


### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 1: Load the dataset
data = pd.read_csv('/content/cars_dataset.csv')

# Step 2: Group data by year
data = data.groupby('year')['price'].mean()

# Step 3: Perform seasonal decomposition
data.index = pd.to_datetime(data.index, format='%Y')
data = data.asfreq('YS').interpolate()

decomposition = seasonal_decompose(data, model='additive', period=2)

# Step 4: Plot the decomposition
plt.figure(figsize=(10, 12))

# Original Data
plt.subplot(411)
plt.plot(data, label='Car Price')
plt.legend(loc='upper left')
plt.title('Average Car Price')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Linear Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```


### OUTPUT:
Original Time series Data:
<img width="922" height="272" alt="image" src="https://github.com/user-attachments/assets/f0d5b466-bc56-457e-86a5-e9950413a326" />











Trend plot :




<img width="925" height="277" alt="image" src="https://github.com/user-attachments/assets/b156632f-a1b3-4bc8-8632-675ad34c1394" />




Seasonal plot:

<img width="922" height="278" alt="image" src="https://github.com/user-attachments/assets/6d98dd89-ecfc-4e2b-ab61-c5d6f8da87e9" />


Residual plot:
<img width="925" height="282" alt="image" src="https://github.com/user-attachments/assets/bbb6073b-8ed9-445d-8bae-7972f1f77bec" />




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
