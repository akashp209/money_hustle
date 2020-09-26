---
title: 'Can Machine Learning Predict The Stock Market?'
date: '2020-03-20'
---
##### We test to see if technology is powerful enough to solve the mystery of financial markets

![machine](https://miro.medium.com/max/1400/1*5mcK1HO50cdgfQ6LGc9FPw.png)
If invested correctly and wisely, the U.S. stock market can generate astonishing returns. Following the steps of quantitative investment firms like Two Sigma and Citadel, we are interested in knowing if we can use machine learning to predict stock price movements.

## The Data
We used Alpha Vantage API to pull daily price data for five ETFs (QQQ, TQQQ, VTI, IWM, SPY) and started out with just Open, High, Low, Close and Volume.
![data](https://miro.medium.com/max/868/0*l3pn1AWTTkQ2WUzR)

## Feature Generation
We decided to manually create functions in python to calculate several heavily use technical indicators in trading: Chaikin A/D, BBAND, CCI, EMA, MACD, OBV, RSI, SMA, and STOCH.

## Simple Moving Average

Moving Averages are used to smooth the data in an array to help eliminate noise and identify trends. The Simple Moving Average is literally the simplest form of a moving average. Each output value is the average of the previous n values. In a Simple Moving Average, each value in the time period carries equal weight, and values outside of the time period are not included in the average. This makes it less responsive to recent changes in the data, which can be useful for filtering out those changes.

![code](https://miro.medium.com/max/1400/0*7eM15_e8nIa43UmY)

## Exponential Moving Average

The Exponential Moving Average is a staple of technical analysis and is used in countless technical indicators. In a Simple Moving Average, each value in the time period carries equal weight, and values outside of the time period are not included in the average. However, the Exponential Moving Average is a cumulative calculation, including all data. Past values have a diminishing contribution to the average, while more recent values have a greater contribution. This method allows the moving average to be more responsive to changes in the data.

![code1](https://miro.medium.com/max/1400/0*WM4sdrwz-Nb-_iJZ)

## Moving Average Convergence Divergence

The Moving Average Convergence Divergence (MACD) is the difference between two Exponential Moving Averages. The Signal line is an Exponential Moving Average of the MACD.

The MACD signals trend changes and indicates the start of the new trend direction. High values indicate overbought conditions, low values indicate oversold conditions. Divergence with the price indicates an end to the current trend, especially if the MACD is at extremely high or low values. When the MACD line crosses above the signal line a buy signal is generated. When the MACD crosses below the signal line, a sell signal is generated. To confirm the signal, the MACD should be above zero for a buy, and below zero for a sell.

The time periods for the MACD are often given as 26 and 12. However, the function actually uses exponential constants of 0.075 and 0.15, which are closer to 25.6667 and 12.3333 periods. To create a similar indicator with time periods other than those built into the MACD, use the Price Oscillator function.

![code2](https://miro.medium.com/max/1400/0*t3_aWHWHrutNniOM)

## Stochastic Oscillator

The Stochastic Oscillator measures where the close is in relation to the recent trading range. The values range from zero to 100. %D values over 75 indicate an overbought condition; values under 25 indicate an oversold condition. When the Fast %D crosses above the Slow %D, it is a buy signal; when it crosses below, it is a sell signal. The Raw %K is generally considered too erratic to use for crossover signals.

![code3](https://miro.medium.com/max/1400/0*1WG3J2Kt49IOgl7n)

## Accumulation/Distribution Line

The Accumulation/Distribution Line is similar to the On Balance Volume (OBV), which sums the volume times +1/-1 based on whether the close is higher than the previous close. The Accumulation/Distribution indicator, however, multiplies the volume by the close location value (CLV). The CLV is based on the movement of the issue within a single bar and can be +1, -1 or zero.

The Accumulation/Distribution Line is interpreted by looking for a divergence in the direction of the indicator relative to price. If the Accumulation/Distribution Line is trending upward it indicates that the price may follow. Also, if the Accumulation/Distribution Line becomes flat while the price is still rising (or falling) then it signals an impending flattening of the price.

![code4](https://miro.medium.com/max/1400/0*ZIYbXgGSFfKcSGie)

## Bollinger Bands

Bollinger Bands consist of three lines. The middle band is a simple moving average (generally 20 periods) of the typical price (TP). The upper and lower bands are F standard deviations (generally 2) above and below the middle band. The bands widen and narrow when the volatility of the price is higher or lower, respectively.

Bollinger Bands do not, in themselves, generate buy or sell signals; they are an indicator of overbought or oversold conditions. When the price is near the upper or lower band it indicates that a reversal may be imminent. The middle band becomes a support or resistance level. The upper and lower bands can also be interpreted as price targets. When the price bounces off of the lower band and crosses the middle band, then the upper band becomes the price target.

![code5](https://miro.medium.com/max/1400/0*HkxeXS3K3gJ5e-7Z)

## On Balance Volume

The On Balance Volume (OBV) is a cumulative total of the up and down volume. When the close is higher than the previous close, the volume is added to the running total, and when the close is lower than the previous close, the volume is subtracted from the running total.

To interpret the OBV, look for the OBV to move with the price or precede price moves. If the price moves before the OBV, then it is a non-confirmed move. A series of rising peaks, or falling troughs, in the OBV indicates a strong trend. If the OBV is flat, then the market is not trending.

![code6](https://miro.medium.com/max/1400/0*3zAGwuIb1THub3NV)

## Data After Feature Generation

![code7](https://miro.medium.com/max/1400/0*lr1n__l3MuEHYvzJ)

## Our Hypothesis

We initially wanted to build a single model using data from all ETFs (QQQ, TQQQ, SPY, VTI, IWM) to predict a long term price trend for stocks traded on an exchange. We set the label as 1 if the return 20 trading days in the future > 3% and 0 otherwise.

However, we found that there is great variance in the data between each ETF, so we decided that we needed to build separate models for each ETF. We ended up only using the QQQ ETF dataset to build our model.

## Experiment 1 (20-day return > 3% as label)

**LSTM: Test AUC 0.476**

![code8](https://miro.medium.com/max/1400/0*ntjE1-fTOxIk1Ovx)

## MLP Neural Network: Test AUC 0.577

![ds](https://miro.medium.com/max/1400/0*8-Vagpa5vJpo27W8)

![sd](https://miro.medium.com/max/1400/0*KfRKQvmTCKzkPEo7)


## Random Forest: Test AUC 0.917

![random](https://miro.medium.com/max/1400/0*dq6qkT-mbv51agiJ)
![sec](https://miro.medium.com/max/1400/0*4KPNoGPdjaPaGxCb)
![third](https://miro.medium.com/max/1400/0*xHEcCm3p-1OtWEUJ)


## Too Good To Be True — A False Hope

Our best model using the QQQ dataset gave us an AUC of .917. We had thought that we figured out a way to predict the stock market. However, this was not the case as we found a major flaw with our model.

It is known by convention that in machine learning, you need to shuffle your dataset in order to create your training and test sets. It is necessary to do this because you want the data in your test set to come from the same distribution as your training data. However, because historical stock data is time-dependent, meaning the data of the subsequent days does not exist until those subsequent days occur, shuffling our data would mean that the training dataset would have access to some data that is actually set in the future. For example, hypothetically, if we were to train our model in 2017 using our dataset which has data from 2018, we could not actually use this training dataset to train our model because, in 2017, the 2018 data had not yet existed. For this reason, we cannot shuffle our data when creating our training and test datasets.

For our next model, we used data from 2010 through 2016 as our training set and data from 2017 through 2019 as our test set. This distribution split is also useful because it basically allows us to “simulate” how our model would do with future data.

Sadly with this model, the AUC score dropped significantly to 0.44 with the same Random Forest Classifier.





























































