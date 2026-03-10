# 50 Quantitative Concepts That Hedge Funds Kept Secret for Decades Have Been Revealed

**Author:** Phosphen (@phosphenq)
**Source:** https://x.com/phosphenq/status/2030325671692496922
**Date:** Mar 8, 2026
**Stats:** 10 replies · 111 reposts · 750 likes · 203K views

---

Over the course of reading this article you will build a foundation from scratch in data science techniques, risk and return modeling, data visualization and more. Whether it's your first time ever dealing with financial concepts inside a programming language or you just want to brush up on the basics, you're in the right place. Every concept here comes with runnable Python code and each section builds on the last so don't skip ahead.

Disclaimer: Not Financial Advice & Do Your Own Research & Markets involve risk

Let's get started!

## Data Source:

### 1 - NumPy
The most widely used numerical library in Python for working with arrays, matrices and mathematical operations:

```python
import numpy as np
```

### 2 - Pandas
A numpy wrapper we'll use to hold our data in labeled structures that make financial analysis actually manageable:

```python
import pandas as pd
```

### 3 - Matplotlib
Our data visualization tool that turns numbers into charts:

```python
import matplotlib.pyplot as plt
```

### 4 - Read_csv
To import data into pandas we can use the read_csv function and hand it either a path to a local file or a URL to a remote hosted resource:

```python
df = pd.read_csv("path/to/data.csv")
# or from a URL:
df = pd.read_csv("https://example.com/prices.csv")
```

### 5 - Yfinance
Instead of CSV files we're going to use a Python library called yfinance to fetch our data, which will put it into a pandas data structure for us:

```python
import yfinance as yf
```

### 6 - Yf.download
Let's go ahead and download monthly stock prices for the ETF SPY:

```python
prices = yf.download("SPY", period="max", interval="1mo")
```

### 7 - Adjusted Close
Adjusted Close gives us closing prices that are inclusive of cash flows like dividends and stock splits, so we aren't leaving any data out. This way returns will be calculated as total returns as opposed to price returns:

```python
prices = yf.download(
    ["SPY", "AGG"], period="max", interval="1mo"
)["Adj Close"]
```

A stock paying 3% dividends annually will look flat on a raw Close chart even though you actually earned money. Over 20 years that gap compounds to 80%+ Always use Adjusted Close.

## Information Preparation

### 8 - Series
There's two different pandas data structures we can use to store data. A Series is single-dimensional and can be used for data from a single stock:

```python
spy = prices["SPY"]
type(spy)  # pandas.core.series.Series
```

### 9 - DataFrame
A DataFrame is two-dimensional and can be used to store data from multiple stocks:

```python
type(prices)  # pandas.core.frame.DataFrame
```

In this article we're going to stick with DataFrames.

### 10 - Dropna and inplace
In cases where we have NA values because two different stocks have different inception dates, we can remove all rows with an NA by calling dropna. The inplace parameter performs the operation on the existing DataFrame as opposed to returning a new one:

```python
prices.dropna(inplace=True)
```

### 11 - Price Series
What we have now is called a price series because we have prices at consecutive time steps.

### 12 - Index
The date column is special and is known as our index. We can change the format of our index to monthly to match the granularity of the data with the to_period method:

```python
prices.index = prices.index.to_period("M")
```

### 13 - Plotting Prices
We can now go ahead and plot our prices with matplotlib:

```python
prices.plot()
plt.title("Price Series")
plt.show()
```

This doesn't actually help us perform any type of comparison as our prices start at two different arbitrary points since this is just raw ETF data at the moment. We'll be seeing how to correct this shortly with the wealth index.

## Returns

When it comes to calculating returns from these prices, let's go over some basic math first.

### 14 - Standard Return Formula
The most common return formula that you've probably been taught is where you take the difference in final price and the initial price of an asset and scale it by the initial price:

Return = (P_final - P_initial) / P_initial

This gives you a single period return expressed as a decimal which you can then convert into a percentage:

```python
p_initial = 100
p_final = 130
ret = (p_final - p_initial) / p_initial
print(f"{ret:.2%}")  # 30.00%
```

### 15 - 1+R Format
It's going to be helpful to slightly modify the standard formula. If we divide the final price by the initial price we are left with the exact same number but larger by one. If we then subtract one we have the exact same result:

```python
one_plus_r = p_final / p_initial  # 1.30
ret = one_plus_r - 1  # 0.30
```

This is called the 1+R format and it's going to be a recurring theme.

### 16 - Multi-Period Return
All of that was for a single period return. To calculate a multi-period return we can add one to each single period return, multiply them all together, and then subtract one:

Compound Return = (1+r₁) x (1+r₂) x ... x (1+rₙ) - 1

```python
r1, r2, r3 = 0.10, -0.05, 0.08
compound = (1 + r1) * (1 + r2) * (1 + r3) - 1
print(f"Compound: {compound:.4%}")  # 13.34%
```

This is known as a compound or geometric return. The process is called geometric linking.

### 17 - Variance Drag
It is important to note that in order to calculate the compound return, which is the real return, you cannot just add the returns together due to something called variance drag.

If you invest $100 into an asset and earn 30% in time step one, that's 30% of $100. If you then lose 30% in time step two, that's 30% of $130, which is $39:

```python
initial = 100
after_gain = initial * 1.30  # $130
after_loss = after_gain * 0.70  # $91
print(f"Start: ${initial}")
print(f"+30%: ${after_gain}")
print(f"-30%: ${after_loss}")
print(f"Average: 0%")
print(f"Actual: {(after_loss/initial - 1):.0%}")  # -9%
```

Average return is 0%. Actual return is -9%

The gap between arithmetic and geometric return is approximately σ²/2 and it grows with the square of volatility. At 20% annual vol the drag is ~2%/year. At 80% vol it's ~32%.

If you think this is theoretical, look at MSTU, the 2x leveraged MicroStrategy ETF. Over the past year MSTR fell about 42% while btc was actually up 15%. MSTU didn't fall 84%. It fell 88%. The extra losses are pure variance drag compounding against holders every single day in a stock with 90%+ realized volatility.

Both the 2x long and the 2x inverse MSTR ETFs lost more than 65% in the same year. Long and short, both destroyed. That's variance drag at work in the real world.

If you only learn one thing from this article, let it be this.

### 18 - Pct_change
If you want to go ahead and turn a price series into a return series you can take a shortcut and simply call the pct_change method rather than using the previous formula:

```python
returns = prices.pct_change()
```

### 19 - First Data Point Loss
When converting from prices to returns you will always lose a single data point as returns cannot be computed for the first day since previous closing prices are not available. We can use dropna to clean this up:

```python
returns.dropna(inplace=True)
```

We now have a return series.

### 20 - Plotting Returns
If you want to see how our returns look we can once again plot:

```python
returns.plot()
plt.title("Return Series")
plt.show()
```

### 21 - Compounding the Series (.prod)
If we now want to compound the entire return series we can add one to all of our single period returns, call .prod() which will calculate the product between all of them, and then subtract one:

```python
total_return = (1 + returns).prod() - 1
```

### 22 - Formatting Output
If you want to view this more clearly we can round this and apply the .astype method to change the numbers to strings:

```python
display = (total_return * 100).round(2).astype(str) + "%"
print(display)
```

These are now our in-sample compound returns.

## DataFrame Methods

Coming back to some more DataFrame methods.

### 23 - Head()
View the first five or n elements:

```python
prices.head()
prices.head(10)
```

### 24 - Tail()
Same for the end:

```python
prices.tail()
prices.tail(3)
```

### 25 - Size
View the total number of elements in the DataFrame:

```python
prices.size
```

### 26 - Shape
View the size of each individual axis:

```python
prices.shape  # (rows, columns)
```

### 27 - Index
View our dates:

```python
prices.index
```

### 28 - Columns
View our stocks:

```python
prices.columns
```

### 29 - Single Bracket Indexing
We can index into a single stock with single brackets and get a Series:

```python
spy = prices["SPY"]
```

### 30 - Double Bracket Indexing
Or any number of stocks with double brackets to keep it as a DataFrame:

```python
subset = prices[["SPY", "AGG"]]
```

### 31 - Loc
We can index across rows with .loc given an index label:

```python
prices.loc["2025-01"]
prices.loc["2025-01":"2026-06"]  # slicing with colon
```

### 32 - Iloc
Or with .iloc for integer location given the position of an index:

```python
prices.iloc[0]
prices.iloc[0:12]
```

Both of these methods also work with the colon operator for slicing if you want to select a range.

## Measures of Risk

### 33 - Standard Deviation
Let's go ahead and calculate the volatility measured by standard deviation. We know that standard deviation is just the square root of variance:

σ = √Variance

Once again we can shorthand the underlying math by using the .std() method:

```python
vol = returns.std()
print(vol)
```

Now that we know how to calculate returns and volatility, let's move on to annualizing both of these metrics as this is what we actually use to analyze performance.

## Annualization

### 34 - Annualized Return
We know that if we had a single monthly return we could annualize it by raising it to the 12th power as this would be equivalent to a compound return over a 12 month period.

In reality we have a return series with hundreds of different per-period returns. What we can do is work backward: raise the compound growth to (periods per year / number of periods):

```python
def annualize_return(returns, periods_per_year):
    compound_growth = (1 + returns).prod()
    n_periods = returns.shape[0]
    return compound_growth ** (periods_per_year / n_periods) - 1

ann_ret = annualize_return(returns, 12)  # 12 for monthly data
print(ann_ret)
```

### 35 - Annualized Volatility
Annualized volatility is going to be much easier as we can just multiply our volatility by the square root of the periods per year:

```python
def annualize_vol(returns, periods_per_year):
    return returns.std() * np.sqrt(periods_per_year)

ann_vol = annualize_vol(returns, 12)
print(ann_vol)
```

Why square root? Variance scales linearly with time. Standard deviation is the square root of variance. So std scales with √time.

## Raw Sharpe Ratio

### 36 - Raw Sharpe Ratio
While we're at it we can calculate the raw Sharpe ratio, which is just a risk-adjusted return measure. To calculate the raw Sharpe ratio we can scale our annualized returns by our annualized volatility:

```python
sharpe = annualize_return(returns, 12) / annualize_vol(returns, 12)
print(f"Raw Sharpe: {sharpe}")
```

A Sharpe below 0.5 is weak. 0.5 to 1.0 is the equity average. Above 1.0 is strong. Above 2.0 and you're in a different league. Here's something most people don't know: Bitcoin 12-month Sharpe ratio hit 2.4 in 2025, which puts it in the top 100 global assets by risk-adjusted return. The "it's just gambling" crowd has never run this calculation.

### 37 - Risk-Free Rate
To calculate the actual Sharpe ratio this would require a time series of T-bill returns, also known as the risk-free rate:

Sharpe = (R_portfolio - R_f) / σ_portfolio

That will be covered separately. For quick comparisons the raw Sharpe gets you most of the way.

## Wealth Index

### 38 - Wealth Index (.cumprod)
If we want to use a return series to create a wealth index we can add one to all of our returns, but rather than calling .prod() we can call .cumprod() which calculates the cumulative product, the running product at each successive timestamp:

```python
wealth_index = (1 + returns).cumprod()
wealth_index.plot(title="Growth of $1")
plt.show()
```

We can now see an accurate comparison between securities. This also represents the growth of one dollar.

### 39 - DateOffset
Something to note is that the wealth index doesn't actually start at one because the first data point represents the first day's return. If you want to insert a static one as the first data point in our wealth index, we can take our start date with .index.min(), cycle to the previous month with pd.DateOffset:

```python
start = returns.index.min() - pd.DateOffset(months=1)
```

### 40 - Pd.concat
And then prepend this into the DataFrame with pd.concat:

```python
base = pd.DataFrame(
    {col: [1.0] for col in returns.columns},
    index=[start]
)
wealth_index = pd.concat([base, wealth_index])
wealth_index.plot(title="Wealth Index")
plt.show()
```

Now every asset starts at $1 and you're comparing actual performance instead of arbitrary price levels.

## Drawdowns

For our last topic let's calculate and plot our drawdowns. Drawdowns are just going to be the return from the previous peak to the current price.

### 41 - Previous Peaks (.cummax)
We're going to use the wealth index to help us calculate drawdowns in conjunction with the previous peaks, which can be calculated by calling .cummax() on the wealth index:

```python
previous_peaks = wealth_index.cummax()
```

cummax is a cumulative maximum which will set each value equal to the highest data point on or before each respective time step.

### 42 - Drawdown Formula
To arrive at our drawdowns we take the difference between our wealth index and our previous peaks and scale it by our previous peaks:

```python
drawdowns = (wealth_index - previous_peaks) / previous_peaks
```

This is now our drawdown series.

### 43 - Maximum Drawdown
A key stat that is often calculated would be the maximum drawdown, which we can calculate by calling .min() since our numbers are negative:

```python
max_dd = drawdowns.min()
print(f"Max Drawdown: {max_dd}")
```

### 44 - Date of Maximum Drawdown
We can call .idxmin() or "index minimum" to get the date associated with the maximum drawdown:

```python
max_dd_date = drawdowns.idxmin()
print(f"Date: {max_dd_date}")
```

### 45 - Matplotlib Annotation
If you want to plot all of this together we can add in a matplotlib annotation where we format the max drawdown, give it coordinates, position it, and add in an arrow:

```python
drawdowns.plot(title="Drawdowns")
plt.annotate(
    f"Max DD: {max_dd.min():.2%}",
    xy=(max_dd_date.values[0], max_dd.min()),
    xytext=(max_dd_date.values[0], max_dd.min() + 0.05),
    arrowprops=dict(arrowstyle="->"),
    fontsize=9
)
plt.show()
```

This now turns all of this code that might be hard to wrap your head around into a clean data visualization.

### 46 - Arrow Formatting
The arrowprops dictionary controls how the annotation arrow looks. You can customize the style, color and width:

```python
arrowprops=dict(
    arrowstyle="->",
    color="red",
    lw=1.5
)
```

### 47 - Subplots
To view everything together on one screen:

```python
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
prices.plot(ax=axes[0, 0], title="Prices")
returns.plot(ax=axes[0, 1], title="Returns")
wealth_index.plot(ax=axes[1, 0], title="Wealth Index")
drawdowns.plot(ax=axes[1, 1], title="Drawdowns")
plt.tight_layout()
plt.show()
```

Four views of the same data. This is the standard layout you'll see on any quant's screen.

### 48 - Why Drawdowns > Volatility
Volatility treats gains and losses the same. A +5% day and a -5% day contribute equally to standard deviation. Drawdowns only measure the downside, which is the part you actually feel in your account.

A strategy doing 15% annually with -20% max drawdown versus one doing 15% with -60% max drawdown will show a similar Sharpe. But you'll sleep very differently holding each one.

### 49 - The Full Pipeline
The entire analysis, end to end, in one runnable block:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import yfinance as yf

# Data
prices = yf.download(["SPY", "AGG"], period="max", interval="1mo")["Adj Close"]
prices.dropna(inplace=True)
prices.index = prices.index.to_period("M")

# Returns
returns = prices.pct_change().dropna()

# Metrics
total_return = (1 + returns).prod() - 1
ann_ret = lambda r: ((1+r).prod()) ** (12/r.shape[0]) - 1
ann_vol = lambda r: r.std() * np.sqrt(12)
sharpe = ann_ret(returns) / ann_vol(returns)

# Wealth & Drawdowns
wealth = (1 + returns).cumprod()
peaks = wealth.cummax()
dd = (wealth - peaks) / peaks

print("Compound Returns:")
print((total_return * 100).round(2).astype(str) + "%")
print(f"\nAnnualized Return:\n{(ann_ret(returns)*100).round(2)}%")
print(f"\nAnnualized Vol:\n{(ann_vol(returns)*100).round(2)}%")
print(f"\nSharpe:\n{sharpe.round(3)}")
print(f"\nMax Drawdown:\n{(dd.min()*100).round(2)}%")
```

Copy this, run it, swap the tickers for whatever you're holding.

### 50 - What Comes Next
Everything more advanced in quantitative finance, from options pricing and Black-Scholes to Monte Carlo simulation and factor regressions, is built directly on top of these 50 concepts.

The formulas were never actually secret. They were just buried in $200 textbooks and $500k/year jobs where nobody had any incentive to explain them simply.

That asymmetry is gone now.
