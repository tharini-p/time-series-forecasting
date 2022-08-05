# Time series forecasting of Bitcoin prices

The objective for this project is to predict Bitcoin prices using time series forecasting techniques. Bitcoin has remained the leading cryptocurrency since it was first used in 2009. It is a decentralized digital currency that is controlled by the will of its users. The transactions and values are stored independently of any governments or financial instituitions. In this project, ARIMA model is used to predict the prices.

### Data
The dataset contains opening and closing prices Bitcoin from January 2015 to March 2022.
Datasource: [YahooFinance]( https://finance.yahoo.com/quote/BTC-USD/history/)

![data_btc](https://github.com/tharini-p/time-series-forecasting/blob/main/img/data_btc.png)


### Stationarity

The Augmented Dickey-Fuller test is a statistical test that can be used to check the stationarity of a time series. The null hypothesis of the test is that the time-series can be represented by a unit root, that is it is non-stationary while the alternate hypothesis is that the time series does not have a unit root, that is it is stationary.

We reject or fail to reject a null hypothesis based on the p-value obtained from the results,
* p-value > 0.05: Fail to reject null hypothesis and the series is non-stationary
* p-value <= 0.05: Reject null hypothesis and the series is stationary

```
p-value: 0.785456
```
Hence the series is not stationary.

### Transformations

First, the time series is log transformed as a logarithmic transformation is useful when the variation increases with time. Then trend and seasonality is removed by differencing the time series. Then the ADF test is performed on this transformed series,

```
p-value: 0.000000
```
The series is stationary now.

### ARIMA

ARIMA (AutoRegressive Integrated Moving Average) model from statsmodel is used for forecasting. 15% of the data is used for testing.

RSS: 4.4065

![rss_btc](https://github.com/tharini-p/time-series-forecasting/blob/main/img/rss_btc.png)


The model is evaluated using a rolling forecasting origin. Error is calculated for all the one step predictions and then averaged.

The mean error is 2.6882%

![pred_btc](https://github.com/tharini-p/time-series-forecasting/blob/main/img/pred_btc.png)


