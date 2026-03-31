
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
import yfinance as yf


ticker = yf.Ticker('PETR4.SA')
df = ticker.history(interval='1d', start='2023-01-01', end='2026-03-31')
print(df.head())


df

df.tail()

df[['Close']].info()

df[['Close']].head()

decomposicao = seasonal_decompose(df[['Close']],model='additive', period=30, extrapolate_trend=30)

df[['Close']].plot()

decomposicao.seasonal + decomposicao.resid + decomposicao.trend

decomposicao.trend.iloc[0:5]

df[['Close']].plot()

decomposicao.plot();

decomposicao.seasonal

df['Close'].rolling(7).mean

media_movel7d = df['Close'].rolling(7).mean()
media_movel14d = df['Close'].rolling(14).mean()
media_movel21d = df['Close'].rolling(21).mean()

fig, ax = plt.subplots(figsize=(12,5))
plt.plot(media_movel7d, 'orange')
plt.plot(media_movel14d, 'red')
plt.plot(media_movel21d, 'black')
plt.plot(df['Close'])



