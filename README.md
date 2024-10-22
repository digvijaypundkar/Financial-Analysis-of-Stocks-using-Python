# Stock Market Analysis: Insights into Risk, Returns, and Trends

### Getting data 

To retrieve the data for this project, the ⁠ yfinance ⁠ package was utilized instead of ⁠ pandas-datareader ⁠ due to its broader functionality. 

The ⁠ yfinance ⁠ package, which wraps the Yahoo Finance API, provides extensive financial data, including minute-level stock market information, P/E ratios, revenue, EBIT, income statements, balance sheets, and cash flows. This makes it a powerful tool for detailed financial analysis. While ⁠ pandas-datareader ⁠ is a useful option, ⁠ yfinance ⁠ was chosen for its superior range of features and flexibility for future data exploration.

### Data Preparation

The project begins by defining the analysis period and selecting the relevant ticker symbols. The focus is on the stock market impact during the COVID-19 pandemic, with the analysis covering data from January 2018 to mid-August 2020. This range provides a baseline for comparison before and during the pandemic.

Key stocks of interest include:
•⁠  ⁠*S&P 500 ETF (SPY)*: A broad representation of the U.S. economy.
•⁠  ⁠*American Airlines (AAL)*: Severely affected due to widespread flight cancellations.
•⁠  ⁠*Zoom (ZM)*: A major beneficiary of the pandemic, with a surge in demand for virtual communication.
•⁠  ⁠*Netflix (NFLX) and Facebook (FB)*: Other prominent companies during this period.

The ⁠ yfinance ⁠ package was used to retrieve data for these stocks, including open, close, high, low prices, and daily trading volumes. Data from all tickers are combined into a single dataframe for streamlined comparison.
