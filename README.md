# Stock Market Prediction using ARIMA Model
This project is to predict stock price using ARIMA model with help of Yahoo Finance stock data.


## Install and import the required libraries


## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

## Loading the data
Install and import yfinance using the following code-  

*!pip install yfinance*  

*import yfinance as yf*  

Download the data as a .csv file.

Ans load it.

## Data Preparation

Check for null data.  
Drop any null data.  
Conver the "Date" in the .csv file into datetime formate.  

Most analyist use *"Close Price of the Stock"* for analysis.So we will be using only the "Date" and "Close" data of the .csv file.
We will groupby "Date" and "Close" of the .csv file.

## Stationarity Test

For ARIMA modle to work it needs to be *stationary*.So we will be performing *Stationary test*.

**Autocorrelation Function**



![Screenshot (77)](https://user-images.githubusercontent.com/78019202/182507778-53bfa15b-307f-493f-a65e-4e5bfc8ebe75.png)



**Partial Autocorrelation Function**

![Screenshot (78)](https://user-images.githubusercontent.com/78019202/182507825-92d07122-fba7-4458-acf3-7554b08a2d89.png)

**Dickey Fuller Test**




## Removing Non-Stationrity 
**Differencing Method**  



![Screenshot (81)](https://user-images.githubusercontent.com/78019202/182508043-b8ffb108-50e2-468a-917e-3c5f3514a750.png)

**Re-test with Dickey Fuller Test**

**"Close First Difference"**  


![Screenshot (82)](https://user-images.githubusercontent.com/78019202/182508172-e8bd8c28-3bb4-44d8-9192-352c7156f1d8.png)


## Optimum p , d and q for ARIMA   

With Auto_ARIMA find the p,d,q values with the following code  

*stepwise_fit = auto_arima(msft_6M2['Close'],trace=True,suppress_warnings=True)*  

*print(stepwise_fit.summary())*  

*stepwise_fit.plot_diagnostics(figsize=(15,8))*  

*plt.show()*

![Screenshot (83)](https://user-images.githubusercontent.com/78019202/182508235-c9bffdf1-6035-4e84-8164-3ebb3f1d31aa.png)
## Building the modle

Build the model with following code-  

*series = msft_6M2['Close']*  
*X = series.values*  
*size = int(len(X) * 0.7)*  
*train, test = X[0:size], X[size:len(X)]*   
*model = ARIMA(train, order=(0, 1, 0))*  
*model_fit = model.fit()*  
*print(model_fit.summary())*


*Autocorrelation Plot*
![Screenshot (84)](https://user-images.githubusercontent.com/78019202/182508290-cf795a56-1abe-41b5-a659-4ae2b1cb5881.png)

## Testing



## Performance Test

![Screenshot (85)](https://user-images.githubusercontent.com/78019202/182508343-0ac6de09-695a-4aa6-b9dc-f920a43cf830.png)

## Real vs Predicted Price
![Screenshot (86)](https://user-images.githubusercontent.com/78019202/182508401-02ab29e3-d73b-4d78-9c21-97c973dde725.png)
