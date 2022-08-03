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



![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)



**Partial Autocorrelation Function**

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

**Dickey Fuller Test**




## Removing Non-Stationrity 
**Differencing Method**  



![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

**Re-test with Dickey Fuller Test**

**"Close First Difference"**  


![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)


## Optimum p , d and q for ARIMA   

With Auto_ARIMA find the p,d,q values with the following code  

*stepwise_fit = auto_arima(msft_6M2['Close'],trace=True,suppress_warnings=True)*  

*print(stepwise_fit.summary())*  

*stepwise_fit.plot_diagnostics(figsize=(15,8))*  

*plt.show()*

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)
![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)
## Building the modle

Build the model with following code-  

*series = msft_6M2['Close']*  
*X = series.values*  
*size = int(len(X) * 0.7)*  
*train, test = X[0:size], X[size:len(X)]*   
*model = ARIMA(train, order=(0, 1, 0))*  
*model_fit = model.fit()*  
*print(model_fit.summary())*

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

*Autocorrelation Plot*
![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

## Testing

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

## Performance Test

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

## Real vs Predicted Price
https://github.com/21skar4/Stock-Market-Prediction-using-ARIMA-Model-SoC/issues/12#issue-1326584796
