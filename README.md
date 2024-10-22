# Stock Market Analysis: Insights into Risk, Returns, and Trends

### Getting data 

To retrieve the data for this project, the `yfinance` package was utilized instead of `pandas-datareader` due to its broader functionality. 

The `yfinance` package, which wraps the Yahoo Finance API, provides extensive financial data, including minute-level stock market information, P/E ratios, revenue, EBIT, income statements, balance sheets, and cash flows. This makes it a powerful tool for detailed financial analysis. While `pandas-datareader` is a useful option, `yfinance` was chosen for its superior range of features and flexibility for future data exploration.

### Data Preparation

The analysis covers stock data from January 2018 to mid-August 2020, focusing on the impact of COVID-19.

Key stocks of interest include:
•⁠  ⁠*S&P 500 ETF (SPY)*: A broad representation of the U.S. economy.
•⁠  ⁠*American Airlines (AAL)*: Severely affected due to widespread flight cancellations.
•⁠  ⁠*Zoom (ZM)*: A major beneficiary of the pandemic, with a surge in demand for virtual communication.
•⁠  ⁠*Netflix (NFLX) and Facebook (FB)*: Other prominent companies during this period.

The ⁠ yfinance ⁠ package was used to retrieve data for these stocks, including open, close, high, low prices, and daily trading volumes. Data from all tickers are combined into a single dataframe for streamlined comparison.

### Exploratory Data Analysis

The initial inspection reveals fewer data points for **Zoom (ZM)** compared to other companies, likely due to its later IPO. This will be revisited shortly. 

The `.describe()` method is used to generate descriptive statistics, helping identify data ranges and potential outliers, though no significant anomalies are found.

A heatmap is used to visualize missing data. For stocks like **Zoom**, gaps in data occur before their IPO date—April 18, 2019—resulting in missing values for earlier dates, which is expected and not a cause for concern.

![IMG-20241023-WA0004](https://github.com/user-attachments/assets/0124459a-11f8-4c10-827c-64de9a8c7693)

### Closing Prices Over Time

A line chart of closing prices is an excellent way to visualize stock trends and detect key market movements. To create this, the adjusted closing prices of each stock are extracted into a new dataframe using the `pandas.DataFrame.xs()` method.

The `plotly` package was used for its simplicity, aesthetics, and interactivity, allowing zooming, panning, and data comparisons directly within the notebook. Notably, a sharp drop in March 2020 aligns with the onset of the COVID-19 pandemic, causing widespread market selloffs.

However, **Zoom (ZM)** defied this trend, with its stock soaring as the platform became essential for virtual communication during lockdowns. This chart offers a great way to explore such stories and uncover market patterns.

![IMG-20241023-WA0007](https://github.com/user-attachments/assets/8196ce4c-c951-4859-9834-7f5241ad3611)

### Candlestick Charts

![image](https://github.com/user-attachments/assets/3ae4bf4b-1d9b-4e63-ade2-2d8aca537d9d)

A candlestick chart provides a detailed view of stock price movements, summarizing the open, close, high, and low prices for each trading day. Candlesticks are green if the closing price is higher than the opening price, indicating bullish sentiment, while they are red if the price falls. The length of the candlestick reflects intraday volatility, offering insights into investor sentiment.

Using Plotly, a custom candlestick chart is created for the companies of interest. This visualization not only aids in interpreting price movements but also plays a crucial role in trading strategies. Candlestick patterns, formed by multiple candlesticks, serve as actionable buy or sell signals. 

One notable pattern, the "Three Line Strike," predicts downtrend reversals with an 83% accuracy rate, as noted by Bulkowski in his “Encyclopedia of Candlestick Charts.” Such high-confidence signals can significantly enhance trading decisions.

### Simple Risk Management

This section quantifies stock performance over time and compares it with investment risks. Understanding the risk-return relationship is essential for making informed long-term financial decisions. By analyzing historical performance and volatility, investors can make strategic choices based on potential returns relative to risk.

### Returns Analysis

This section quantifies the returns of each company by evaluating day-to-day percent changes in closing prices using the `pandas .pct_change()` function. A new dataframe, called the ‘returns’ dataframe, captures these daily changes.

For example, **American Airlines (AAL)** saw a 7.44% gain on August 10, followed by three consecutive losses. To summarize this data, the average daily returns are calculated using the `.mean()` function.

Over approximately 2.5 years, Facebook's average daily return is 0.08%, while Zoom's, at 0.5%, is inflated due to missing half its data. Conversely, AAL shows a negative expected return, highlighting the importance of avoiding investments that lead to losses.


### Best and Worst Day Returns

This section explores the best and worst single-day returns for the companies, revealing that many of the worst returns occurred in March 2020 due to the U.S. market crash amid the COVID pandemic and oil price wars. Goldman Sachs even predicted a 24% contraction in U.S. GDP, leading to significant market volatility.

Interestingly, **SPY** recorded its best return just a week after its worst, as investor sentiment began to improve. Analyzing best and worst day returns often correlates with major news events, making it worthwhile to research the context behind these fluctuations.

Next, we will examine the standard deviations of these returns for further insights.

### Returns Standard Deviation

Standard deviation is a key method for analyzing investment risk, indicating historical volatility. A higher standard deviation suggests greater risk, while a lower one may indicate lower potential returns. The balance between risk and return varies by investor preference.

From the analysis, **SPY** shows the lowest standard deviation, making it one of the safest investments due to its diversification across 500 companies. 

Separating the data from 2019 and 2020 reveals that all stocks experienced higher volatility in 2020, with **AAL** and **ZM** exhibiting the highest levels. This increased volatility is attributed to the chaotic market conditions stemming from the COVID-19 pandemic. Notably, SPY’s volatility was approximately 3–4 times greater in 2020 than in 2019. 

Visualizing the distributions of daily returns further clarifies these findings.

### Returns Distribution Plot

The distribution plot in **Figure 6** compares AAL's daily returns for 2019 and 2020. The 2019 returns show a tighter range, while 2020's distribution is much wider, reflecting fluctuating investor sentiment driven by hefty flight cancellations and occasional positive news about vaccines. This volatility resulted in exaggerated price movements. 

While the focus here is on the impact of COVID-19, extending the analysis period can provide insights into a company's historical stability over multiple years.

![IMG-20241023-WA0001](https://github.com/user-attachments/assets/0c4cdf18-1c91-4d12-87bc-6216381cafc7)

### Risk vs. Returns

Understanding the risk-return trade-off is vital for personal investing decisions. **Figure 7** plots risk against returns, illustrating the relative performance of companies. Investments below the red line are considered worthwhile, while those above it are not. 

This line, which varies based on personal risk tolerance, indicates that while higher risk can lead to higher returns, there's a threshold beyond which the returns may not justify the risk. Younger investors might accept more risk for potential gains, while those nearing retirement would prefer lower risk. 

It's important to note that this analysis is based on historical data. For instance, AAL shows high risk and negative returns due to COVID-19 impacts, but future gains are uncertain, as the airline industry may rebound or face bankruptcy.

![IMG-20241023-WA0005](https://github.com/user-attachments/assets/f1e44deb-689a-45d9-8ac0-996d5bbb7163)

### Simple Moving Average

A Simple Moving Average (SMA) is a continuously updated average price over a specific period. For example, a 10-day SMA averages the first 10 closing prices for the initial data point. The next data point then includes the 11th closing price while dropping the first, creating a rolling average. This process smooths out day-to-day volatility and highlights underlying stock price trends. Shorter time frames yield less smoothness but better reflect the source data.

In this analysis, I use the **cufflinks** package to plot the moving averages. The 10-day moving average for Netflix's (NFLX) closing prices demonstrates how the SMA reduces the jagged peaks and valleys, revealing a clearer upward trend over the past two years.

### Bollinger Band Plots

Bollinger Band plots are a technical analysis tool consisting of three lines: a Simple Moving Average (SMA) and two bounding lines set at ±2 standard deviations from a 20-day SMA. 

These bands help identify oversold or overbought conditions in stocks. When a stock’s price approaches the upper band, it may be considered overbought, while proximity to the lower band suggests it is oversold. Although not a sole basis for trading decisions, movements near these bands can indicate unusual price levels, making oversold stocks appealing for purchase.

Additionally, Bollinger Bands are useful for monitoring volatility. The bands widen during periods of high volatility and contract during calmer market conditions—a phenomenon known as a "squeeze." Traders often view squeezes as potential trading opportunities, anticipating that they may precede increased volatility, although the direction of the price movement remains uncertain.
