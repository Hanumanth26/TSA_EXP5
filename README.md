# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


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
Developed By: HANUMANTH RAO
Reg. No: 212222240016
```
```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the Passenger Details
# Replace 'AirPassengers.csv' with the path to your data file
data = pd.read_csv('AirPassengers.csv')

# Ensure that the 'Month' column is in datetime format
data['Month'] = pd.to_datetime(data['Month'])
data['Year'] = data['Month'].dt.year
# Set the 'Month' column as the index
data.set_index('Month', inplace=True)
data.head()

# Plotting the Data
ar1 = data['Year'].values.reshape(-1, 1)
ma1 = data['#Passengers'].values.reshape(-1, 1)
plt.plot(ar1,ma1,label='Data')
plt.title('Plotting the Data')
plt.legend()
plt.show()

# Perform time series decomposition
period=13
result = seasonal_decompose(data,model='multiplicative', period=period)

# Plot the seasonal component
plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

# Plot the trend component
plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

# Plot the original time series
plt.figure(figsize=(12, 6))
plt.subplot(4, 1, 1)
plt.plot(data['#Passengers'], label='original')
plt.title('Original Time Series')
plt.legend()
plt.show()
```
### OUTPUT:

#### FIRST FIVE ROWS:


![WhatsApp Image 2024-04-06 at 14 39 18_832f69c1](https://github.com/Hanumanth26/TSA_EXP5/assets/121033192/810be462-2fc2-48de-b840-9c597d6e0cf2)


#### PLOTTING THE DATA:


![WhatsApp Image 2024-04-06 at 14 38 02_ea71825c](https://github.com/Hanumanth26/TSA_EXP5/assets/121033192/742eca10-e065-47aa-8afb-e5f48e625acb)


#### SEASONAL PLOT REPRESENTATION :
![WhatsApp Image 2024-04-06 at 14 38 02_e6f19b91](https://github.com/Hanumanth26/TSA_EXP5/assets/121033192/77a5362c-8f88-4350-9cca-b48098880c05)




#### TREND PLOT REPRESENTATION :



![WhatsApp Image 2024-04-06 at 14 38 01_cfd645ce](https://github.com/Hanumanth26/TSA_EXP5/assets/121033192/9a8ce239-5fcc-49da-abea-f0c67be732da)


#### OVERAL REPRESENTATION:
![WhatsApp Image 2024-04-06 at 14 38 01_62693d2a](https://github.com/Hanumanth26/TSA_EXP5/assets/121033192/d3bef312-e995-4b3c-8c1d-73aadd51ca38)




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
