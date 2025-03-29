# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA

### Name:ASHOK KUMAR PREETHAM KUMAR

### Register Number:212224040032

### Date: 29/03/25

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv('AirPassengers.csv')
data.head()
data['Month'] = pd.to_datetime(data['Month']) # data=pd.read_csv("/content/AirPassengers.csv",parse_dates=
data.set_index('Month', inplace=True)
data['passengers_diff'] = data['#Passengers'] - data['#Passengers'].shift(1)
result = seasonal_decompose(data['#Passengers'], model='additive', period=12)
data['passengers_sea_diff'] = result.resid
data['passengers_log'] = np.log(data['#Passengers'])
data['passengers_log_diff'] = data['passengers_log'] - data['passengers_log'].shift(1)
result = seasonal_decompose(data['passengers_log_diff'].dropna(), model='additive', period=12)
plt.plot(data['passengers_diff'], label='Differencing')
plt.legend(loc='best')
plt.title('Differencing')
plt.xlabel('Year')
plt.ylabel('Seasonally djusted No of passengers')
plt.subplot(6, 1, 3)
plt.plot(data['passengers_sea_diff'], label='Seasonal Difference ')
plt.legend(loc='best')
plt.title('Seasonal Difference')
plt.xlabel('Year')
plt.ylabel('No of passengers')
plt.subplot(6, 1, 4)
plt.plot(data['passengers_log'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.xlabel('Year')
plt.ylabel('Log(No of passengers)')
plt.subplot(6, 1, 5)
plt.plot(data['passengers_log_diff'], label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing')
plt.xlabel('Year')
plt.ylabel('RDiff(Log(No of passengers))')
data['passengers_log_seasonal_diff'] = data['passengers_log_diff'] - data['passengers_log_diff'].shift(12)
plt.subplot(6, 1, 6)
plt.plot(data['passengers_log_seasonal_diff'], label='Log Transformation and regular Differencing and S')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing and Seasonal Differencing')
plt.xlabel('Year')
plt.ylabel('SDiff(RDiff(Log(No of passengers)))')
plt.tight_layout()
plt.show()+
data.plot(kind='line')
```


### OUTPUT:

ORIGINAL DATA:
![image](https://github.com/user-attachments/assets/3ec1fce4-7a5e-47ee-92f0-0d7bc2ccd6ce)


REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/ad6d8898-298a-4dd1-bc9e-d48b79961d64)

SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/01fed134-5a02-4783-a520-2f71604b1555)

LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/595fc5e3-7b39-43d8-bd88-db32cbf03a4c)

LOG TRANSFORMATION AND REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/28de1817-030f-4ace-b59d-dcb59d148fa9)

LOG TRANSFORMATION AND REGULAR DIFFERENCING AND SEASONAL DIFFERENCING:
![image](https://github.com/user-attachments/assets/9ab44e65-152b-4cd8-862f-ae6b0cd3542d)

COMBINED GRAPH:
![image](https://github.com/user-attachments/assets/3838a5ea-5fd2-4db1-be43-e00f1b80b7ae)


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger data.

