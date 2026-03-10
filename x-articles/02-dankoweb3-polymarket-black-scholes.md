# How I Found an Edge on Polymarket Using a 40 Year Old Formula

**Author:** Danko (@DankoWeb3)
**Source:** https://x.com/DankoWeb3/status/2031253469705666993
**Date:** Mar 10, 2026
**Stats:** 7 replies · 14 reposts · 109 likes · 41K views

![Header Image: "The $12 Trillion Formula Nobody Uses on Polymarket" - Wall Street prices $12T+ in options with one model. Polymarket stock markets are the same thing — but nobody there knows it.](screenshot-header)

![Article includes: arXiv paper screenshot - "Toward Black-Scholes for Prediction Markets: A Unified Kernel and Market Maker's Handbook" by Shaw Dalen](screenshot-arxiv)

![Article includes: Diagram showing payoff for Call Option with Knock-Out Barrier and Put Option with Knock-Out Barrier](screenshot-options-diagram)

---

## The setup nobody talks about

Everyone's trading politics, memes etc. on Polymarket. Meanwhile, there's a whole category of markets that 99% of traders ignore:

**Stock price markets.**

"What will Microsoft (MSFT) close at in 2025?" "What will Tesla (TSLA) close at by March 31?" "What will NVIDIA close at by end of Q1?"

These markets let you bet on whether a stock will be above or below a certain price by a specific date.

Sound familiar?

If you've ever traded options — it should. Because these are literally binary options.

## The connection

A Polymarket stock market works like this:

- "Will MSFT be above $420 by March 31?" → Buy YES at 34¢ or NO at 66¢
- "Will MSFT be above $400 by March 31?" → Buy YES at 31¢ or NO at 69¢

Each contract pays $1 if correct, $0 if wrong.

That 34¢ price? It's the market's implied probability — 34% chance MSFT closes above $420.

Now here's the thing. There's a formula that's been calculating exactly these probabilities for 40+ years.

It's called **Black-Scholes**.

## Why this works — the academic foundation

Before I show my strategy, let me explain WHY it works. Not bro-science — actual math.

### Black-Scholes in 60 seconds

The model was published in 1973 by Fischer Black, Myron Scholes, and Robert Merton. It won a Nobel Prize in Economics (1997). Every options desk on Wall Street uses it as baseline.

At its core, Black-Scholes answers one question:

"What is the probability that a stock will be above price K at time T?"

That's literally what Polymarket stock markets are asking.

The model assumes stock prices follow a Geometric Brownian Motion:

**dS = μS dt + σS dW**

Where:
- S = stock price
- μ = expected return (drift)
- σ = volatility
- dW = random Wiener process (Brownian noise)

Translation: stock price changes = a drift component (trend) + a random component (volatility).

In the risk-neutral framework, the premium of a binary option is interpreted as the expected value — the probability of being in-the-money, discounted to present value. This is exactly what a Polymarket YES share represents.

### This isn't new — academia confirms it

In October 2025, researchers published "Toward Black-Scholes for Prediction Markets: A Unified Kernel and Market Maker's Handbook" (arXiv: 2510.15205). The paper explicitly addresses the gap I'm exploiting:

> Prediction markets aggregate dispersed information into tradable probabilities, but they still lack a unifying stochastic kernel comparable to what options gained from Black-Scholes.

The paper proposes a logit jump-diffusion model that treats the traded probability as a martingale — in plain English, they're building the exact same mathematical bridge between tradfi options and prediction markets that I've been using intuitively.

Separately, research on "Modeling Volatility in Prediction Markets" (NYU) showed that if a prediction market is efficient, contract prices follow a diffusion process — the same type of stochastic process underlying Black-Scholes.

### What about crypto?

GBM has been tested on Bitcoin. Research from 2020-2024 found that the model provides moderate predictive accuracy with a mean absolute error of 10% and captures the general trend, though it underestimates extreme moves.

Here's what's interesting: one study found that GBM produces some of the most accurate directional change predictions for crypto with a 63.6% experimental probability — which was unexpected because crypto is more volatile than stocks.

Why? Because crypto's fundamental IS price action. There's no earnings, no margins, no P/E ratio. GBM is built on price dynamics. For crypto, that's not a limitation — it's a feature.

### Two important disclaimers

1. This model is 40+ years old. It's the ABC of options. It's not a secret edge — it's the minimum baseline you need to understand.
2. It's based on the assumption that price moves are log-normally distributed. In reality, they're not perfectly — heavy tails exist, especially in crypto. But it's close enough to be useful as a baseline.

## My strategy

Here's what I actually did:

**Step 1:** Pick a Polymarket stock market (e.g., MSFT closing price by end of month)

**Step 2:** Go to a tradfi options chain for the same stock (CBOE, Yahoo Finance, or any broker). Find the implied volatility (IV) for options expiring on the same date.

**Step 3:** Plug into Black-Scholes:
- Current stock price (S)
- Strike price (K) = the Polymarket price level
- Time to expiration (T)
- Risk-free rate (r)
- Implied volatility (σ) from tradfi options

**Step 4:** Calculate N(d2) — this gives you the probability of the stock being above K at expiration.

**Step 5:** Compare your calculated probability with the Polymarket price.

If the difference is 5-7%+ → that's your trade.

Everything below 5-7% I consider noise. Transaction costs, spreads, and model uncertainty eat it up.

## A real example

Let's say MSFT is trading at $415. Polymarket has:

"Above $420?" → YES at 34¢ (market says 34% chance)

Tradfi options IV for same expiry = 25%
Time to expiry = 21 days

Plugging into Black-Scholes, I get: probability = 41%

Polymarket says 34%. My model says 41%. That's a 7% gap — above my threshold.

I buy YES at 34¢.

If I'm right, I make $0.66 per share profit (buy at 34¢, receive $1). That's a 194% return.

If I'm wrong, I lose 34¢.

But the key insight: I don't need to be right every time. I just need the expected value to be positive. If my model is accurate, buying at 34¢ when fair value is 41¢ is +EV over many trades.

## When it doesn't work

Sometimes Polymarket is perfectly priced.

I saw this once with MSFT — every single strike had probabilities that matched Black-Scholes almost exactly. The distribution was textbook perfect.

When that happens, there's zero edge. It's pure gambling. I close my laptop and walk away.

## The problems

Let me be honest about the limitations:

1. **Liquidity.** Polymarket stock markets are thin compared to politics markets. You might not be able to size up even if you find edge.
2. **Model assumptions.** Black-Scholes assumes constant volatility and log-normal distribution. Reality is messier — fat tails, volatility clustering, earnings events.
3. **I'm simplifying.** There are things I'm glossing over — the Greeks, early resolution risk, funding costs. But for a baseline framework, it works.

## How tradfi uses this every day

To understand why this works on Polymarket, you need to understand how it works on Wall Street.

Every time you see an options chain on your broker — those prices are derived from Black-Scholes (or its extensions like the Binomial model). Market makers don't sit there guessing. They plug in volatility, time, and strike → the model spits out fair value → they quote around it.

The entire $12+ trillion options market is built on this infrastructure.

When Citadel, Jane Street, or Susquehanna quotes an option, they're calculating the exact same N(d2) probability I'm comparing against Polymarket. The difference? They trade against other professionals with the same models. On Polymarket, you're trading against retail degens who price by gut feeling.

That's the edge. Not the formula itself — but the fact that Polymarket participants don't use it.

## The tradfi options → Polymarket arbitrage

Here's the key insight that makes this more than just theory:

Tradfi options and Polymarket stock markets are pricing THE SAME EVENT. "Will MSFT be above $420 on March 31?" — the CBOE has options for this. Polymarket has a market for this. They should converge to the same probability.

But they don't always converge. Because:

1. Polymarket traders are mostly crypto-native — they don't check options chains
2. Liquidity on Polymarket stock markets is thin — fewer sophisticated participants
3. There's no automated arbitrage between the two markets (yet)

When the gap is 5-7%+ → that's free money left on the table.

## The crypto angle — why GBM fits even better

I mentioned that Black-Scholes assumes Geometric Brownian Motion. For stocks, this is an approximation — earnings reports, M&A, dividends all create non-GBM behavior.

But for crypto? GBM is arguably a better fit.

Research on Bitcoin prices (2020-2024) showed that GBM achieves 63.6% directional accuracy — higher than expected for such a volatile asset. The reason: crypto has no fundamental anchors that break the stochastic model. No quarterly earnings surprises. No dividend ex-dates. Just pure price dynamics — which is exactly what GBM models.

If Polymarket scales crypto price markets with decent liquidity, the same Black-Scholes framework could work even better than it does for stocks. The model's assumptions are actually MORE valid for crypto, not less.

## The bottom line

At expiration, every option becomes binary. You get $0 or $1.

Polymarket stock markets ARE binary options.

The entire options industry has been pricing these for 40+ years using Black-Scholes.

If you can calculate fair value better than the average Polymarket trader — you have edge.

The formula is public. The data is public. The markets are open 24/7.

You just have to do the math.

## References & further reading

- Black, F. & Scholes, M. (1973) — "The Pricing of Options and Corporate Liabilities" — the original paper that started it all
- "Toward Black-Scholes for Prediction Markets" (2025, arXiv: 2510.15205) — the first academic paper explicitly building B-S framework for prediction markets like Polymarket
- "Modeling Volatility in Prediction Markets" (NYU) — proves that efficient prediction market prices follow diffusion processes
- "Bitcoin Price Projections Using Geometric Brownian Motion" (2025, IJRIAS) — empirical study showing GBM achieves 63.6% directional accuracy on crypto
- "Generalised Geometric Brownian Motion: Theory and Applications to Option Pricing" (2020, PMC) — extended GBM model addressing heavy tails

Disclaimer: This is not financial advice. I'm sharing my approach for educational purposes. Do your own research. Prediction markets carry risk of total loss.
