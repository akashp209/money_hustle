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

## Random Forest: Test AUC 0.440

![oaf](https://miro.medium.com/max/1400/0*yEJkjyR0rfwmIMW0)
![da](https://miro.medium.com/max/1400/0*xcONkYgqexrfanNn)

## Rethinking Label Distribution

![d](https://miro.medium.com/max/1400/0*JIR6M-qNMvEnqZYZ)

As you can see in our sample dataset here, all of these rows have very similar 20-MAs, open, and closes. If 20 days after 1/4/2019 has a > 3% increase, then the days around 1/4/2019 will also have a > 3% increase, and that being true for any stock, the determining factor in the label going up in 20 days is generally not decided on the 20th day. It is determined in the days the records have overlapping periods in their 20 future trading periods. In this case, if we extract 1/6/2019 out and as the test set and train on the rest of it, the model will for sure assign the test data a label of one because all of its features are similar to the dates around it which form a cluster. The other issue with this approach is that, as stated earlier, the model is allowing the training set to use future data to predict. For example, the training set included 1/7/2019 -1/11/2019, to predict 1/6/2019, which is impossible to do in the real world.

![dw](https://miro.medium.com/max/1400/0*WJcudnncY71mkvIM)

And that becomes a problem when we are not shuffling the original dataset and when we use later dates as the test set. In this case, the closing prices in the training set hover around 20 dollars per share, but since we are using 2019 as the test set, the prices are dramatically different, thus, the model would perform poorly in assigning them the correct labels, especially considering the features of our records having a range of values that is not present in the training set.

![d](https://miro.medium.com/max/1400/0*YosijWrdK_jvzsOB)

The solution we came up with was to change our label to a daily stock price movement. If the next day’s closing price is greater than the current day’s closing price, then the label is 1. Here, whether a day’s stock price goes up the next day is independent of one another, which resolved our problem of forming clusters and peeking future data.

## Experiment 2 (next day price increase/decrease as label)

## 1. TPOT

![dwe](https://miro.medium.com/max/1400/0*_9rlrYGYo1-NBBgw)

**References:**

[https://towardsdatascience.com/tpot-automated-machine-learning-in-python-4c063b3e5de9 ](https://towardsdatascience.com/tpot-automated-machine-learning-in-python-4c063b3e5de9)
[https://epistasislab.github.io/tpot/using/ ](https://epistasislab.github.io/tpot/using/)

TPOT is an open-source AutoML python package and runs through many different combinations of feature engineering and model selection. TPOT automatically creates many pipelines that include different ways of feature engineering (PCA, MaxAbsScaler, MinMaxScaler, etc) as well as different models with various mixtures of hyperparamete

The performance of TPOT heavily depends on the number of pipelines and the time you allow it to run. The total number of pipelines is equal to POPULATION_SIZE + GENERATIONS x OFFSPRING_SIZE, which can be determined in TPOT’s parameters.

![dw](https://miro.medium.com/max/1400/0*NH4_qFEwhxyn6rQZ)
![ded](https://miro.medium.com/max/1400/0*uov0DJGWXSyGp8PF)

Since we only let TPOT ran 150 pipelines, which only took less than 15 minutes, the performance is not ideal: TEST AUC 0.509. However, with enough time (tens of hours or even days), TPOT can be a very powerful and easy tool to generate great results.

Additionally, TPOT automatically stores the best pipeline it searched through and allows users to export those results as a .py file. As you can see, in our case, TPOT performed PCA on our data and selected GaussianNB as the best classification model.

![ew](https://miro.medium.com/max/1400/0*fFsGOJwtD3yvD3Zv)

## 2. XGBoost

Using an XGBClassifier, we did not have to configure much other than the learning rate, max depth, n_estimators, and subsample. Using cross-validation and a scoring metric of AUC, we optimized the hyperparameters. Finally, we used the optimized hyperparameters to make a final model on an X_train and y_train. The accuracy (not AUC) on the test set was 50.5%

![dwv](https://miro.medium.com/max/1400/0*FQMC0gvK66m6tFBR)
With XGBClassifier, we obtain a 0.478 Test Set AUC Score

![fwef](https://miro.medium.com/max/1400/0*eHpnKqkfSwCUwncN)

## 3. Random Forest

Using a random forest classifier, we tuned hyperparameters across a range of values using the brute force Grid Search Cross-Validation. The best parameters are shown with max_depth = 3 and min_samples_leaf = 3.

![csd](https://miro.medium.com/max/1400/0*ZONcFpdh_WPrJPYK)
![ecsf](https://miro.medium.com/max/1400/0*C_lpji1pn1K2ZU4P)
![cscsd](https://miro.medium.com/max/1400/0*xQ4Ga87R4jakHb2K)

With this Random Forest Classifier, we obtain a 0.519 Test Set AUC Score

![fwe](https://miro.medium.com/max/1400/0*PZCn39_9o3SZabTC)

## 4. Google AutoML

With the increasing popularity of AutoML, we decided to input our dataset to Google Cloud AutoML to see if it can predict a better AUC score than us. Google AutoML has a very user-friendly interface that automatically spits out some statistics after you upload your dataset.

![fw](https://miro.medium.com/max/1400/0*PQsM8FD19h4jx_mc)

In a classification projects like ours, Google AutoML allows users to select different performance metrics to optimize the final model.

![fsf](https://miro.medium.com/max/1400/0*dvOq6HG1WTSFzY2s)

So how did Google AutoML did? After just one hour of training, it returned an AUC of 0.529, by far the highest in our process. It is important to note that the AUC with random forest reaches 0.519 which is only 0.01 lower than the Google AutoML.

![cfwe](https://miro.medium.com/max/1400/0*lZ8IrGw-NSpia4Xu)

# Conclusion and Insights
The weakness of technical analysis: In the world of finance, technical analysis (using historical stock prices to predict future stock prices) has been proven to be futile. Additional features could be considered in further analysis:

1. Tweets Scrapping: sentiment analysis on tweets
2. Earnings Call Transcripts: analyze tones of executives during earnings calls; evaluate topics the executives/analysts are discussing
3. Satellite data (satellite images on oil wells can potentially be used to predict oil prices)

The only true way to beat the stock market is to have additional information, such as having access to future data or knowing quarterly earnings results ahead of time, leading to impossibility or illegality. Using the technical indicators can tell you part of the story, but predicting next day stock direction is too random and influenced by outside factors to create a strong model.

> # Key Takeaway: Machine learning projects are only useful and effective if the data used to train the model and the data the model encounters in the future come from the same distribution, which is not the case when using independent and volatile stock market daily returns as the label.













































































