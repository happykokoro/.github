# How Polymarket Actually Prices Beliefs: The Math Behind LMSR

**Author:** Aleiah (@AleiahLock)
**Source:** https://x.com/AleiahLock/status/2031030310092062913
**Date:** Mar 9, 2026
**Stats:** 34 replies · 70 reposts · 359 likes · 145K views

![Header Image: LMSR - How Polymarket Prices Beliefs - mathematical formulas including C(q) = b·ln(Σe^(qi/b)), softmax derivatives, inflection curves](screenshot-header)

---

Before Polymarket, before PredictIt, before any of the modern prediction markets you've heard of, someone had to solve a hard problem.

How do you build a market that always has liquidity? One where you can always buy or sell, even if nobody is on the other side of your trade?

The answer is LMSR. And once you understand it, you'll see markets differently.

## The Problem With Regular Order Books

Normal financial markets use an order book. Buyers post bids. Sellers' post asks. When they match, a trade happens.

This works fine for stocks with millions of traders. It falls apart for a market asking, "Will candidate X win the election in county Y?" Nobody is posting bids. The spread is enormous. You can't trade.

Prediction markets need a different mechanism. They need an automated market maker - a bot that always quotes a price and always takes the other side.

LMSR (Logarithmic Market Scoring Rule) is that mechanism. It was formalised by Robin Hanson in 2002 and has become the mathematical foundation for most prediction markets.

## The Core Idea

Instead of matching buyers and sellers, LMSR maintains a cost function. You're not trading with another person. You're trading with the market itself, and the market uses math to determine what you pay.

The cost function for a market with n outcomes is:

**C(q) = b × ln(Σ e^(qi/b))**

Where:
- q is a vector of quantities - how many shares of each outcome have been purchased
- b is the liquidity parameter - controls market depth
- The sum runs over all possible outcomes

This looks intimidating. Let's break it down with actual numbers.

## A Binary Market Example

Say you have a market: "Will it rain tomorrow? Yes or No."

Two outcomes. Currently nobody has bought anything, so q = [0, 0].

Let's set b = 100 (a reasonable liquidity parameter).

```python
import numpy as np

def lmsr_cost(q, b):
    """
    LMSR cost function.
    q: array of quantities for each outcome
    b: liquidity parameter
    """
    return b * np.log(np.sum(np.exp(np.array(q) / b)))

def lmsr_price(q, b, outcome_index):
    """
    Current price of a specific outcome.
    This is the softmax function.
    """
    q = np.array(q)
    exp_q = np.exp(q / b)
    return exp_q[outcome_index] / np.sum(exp_q)

def cost_of_trade(q_before, q_after, b):
    """
    How much does a trade cost?
    Difference in cost function before and after.
    """
    return lmsr_cost(q_after, b) - lmsr_cost(q_before, b)

# Starting state: nobody has bought anything
q = [0, 0]
b = 100

# Current prices
p_yes = lmsr_price(q, b, 0)
p_no = lmsr_price(q, b, 1)

print(f"Initial price of YES: {p_yes:.4f}")  # 0.5000
print(f"Initial price of NO: {p_no:.4f}")    # 0.5000
print(f"Sum: {p_yes + p_no:.4f}")            # 1.0000
```

When no shares have been bought, both outcomes are priced at 0.5. The market starts neutral. That's by design.

## How Prices Move

Now someone buys 50 shares of YES. What happens?

```python
# Someone buys 50 shares of YES
q_before = [0, 0]
q_after = [50, 0]

# What did that cost them?
trade_cost = cost_of_trade(q_before, q_after, b)
print(f"Cost of buying 50 YES shares: ${trade_cost:.2f}")

# What are prices now?
p_yes_new = lmsr_price(q_after, b, 0)
p_no_new = lmsr_price(q_after, b, 1)

print(f"New price of YES: {p_yes_new:.4f}")  # 0.6225
print(f"New price of NO: {p_no_new:.4f}")    # 0.3775
```

Buying YES shares pushes the YES price up and NO price down. This is the price discovery mechanism working - the market reflects that someone believes rain is more likely. The prices always sum to 1.0. That's not a coincidence.

The price function is the softmax function:

**p_k(q) = e^(qk/b) / Σ e^(qi/b)**

Softmax guarantees the outputs are positive and sum to 1. It's the same function used in the final layer of neural network classifiers. The market is literally pricing beliefs the same way a neural network outputs probabilities.

## The Liquidity Parameter

The b parameter controls how sensitive the market is to trades.

```python
import matplotlib.pyplot as plt

def show_price_sensitivity(b_values):
    shares_bought = np.linspace(0, 200, 100)
    for b in b_values:
        prices = []
        for s in shares_bought:
            q = [s, 0]
            prices.append(lmsr_price(q, b, 0))
        plt.plot(shares_bought, prices, label=f'b={b}')
    plt.xlabel('YES shares purchased')
    plt.ylabel('YES price')
    plt.title('Price sensitivity vs liquidity parameter')
    plt.legend()
    plt.grid(True)
    plt.show()

show_price_sensitivity([50, 100, 200, 500])
```

- Small `b`: prices move a lot with each trade. Thin market, easy to move.
- Large `b`: prices move slowly. Deep market, harder to move, more liquidity.

There's a tradeoff. More liquidity means the market maker (the platform) takes on more risk. The maximum loss the market maker can incur is:

**L_max = b × ln(n)**

For a binary market with b=100,000:

```python
b = 100_000
n = 2  # binary market
max_loss = b * np.log(n)
print(f"Maximum market maker loss: ${max_loss:,.0f}")
# Maximum market maker loss: $69,315
```

This is the subsidy the platform provides to bootstrap liquidity. It's the cost of running the market.

## Detecting Inefficiency

Here's where it gets interesting for traders.

The LMSR price represents the market's current belief. But markets aren't always right. The price can diverge from the true probability.

If you have a better estimate of the true probability than the market does, you have an edge.

```python
def expected_value(market_price, true_probability, shares=1):
    """
    Expected value of buying one YES share.
    market_price: what you pay per share (between 0 and 1)
    true_probability: your estimate of the true probability
    shares: number of shares
    A YES share pays $1 if YES wins, $0 if NO wins.
    """
    # If YES wins (probability = true_prob): you gain (1 - market_price)
    # If NO wins (probability = 1 - true_prob): you lose market_price
    ev = (true_probability * (1 - market_price) -
          (1 - true_probability) * market_price)
    return ev * shares

# Example: market says 40% chance, you think it's 60%
market_price = 0.40
your_estimate = 0.60

ev = expected_value(market_price, your_estimate)
print(f"Expected value per share: ${ev:.3f}")
# Expected value per share: $0.200
# That's a 20 cent edge per dollar risked
# In Kelly terms, this is a significant edge
```

Positive expected value means the market is mispriced in your favor. You buy. Negative means the other direction is mispriced. You sell (buy NO).

## Sequential Price Impact

One thing traders need to account for: your own trade moves the price against you.

```python
def simulate_buy_impact(initial_q, shares_to_buy, b, outcome=0, steps=10):
    """
    Simulate buying a large position incrementally.
    Shows how average fill price degrades with size.
    """
    q = list(initial_q)
    total_cost = 0
    total_shares = 0
    prices_paid = []
    shares_per_step = shares_to_buy / steps

    for step in range(steps):
        price_before = lmsr_price(q, b, outcome)
        q_after = q.copy()
        q_after[outcome] += shares_per_step
        step_cost = cost_of_trade(q, q_after, b)
        total_cost += step_cost
        total_shares += shares_per_step
        prices_paid.append(step_cost / shares_per_step)
        q = q_after

    avg_fill = total_cost / total_shares
    final_price = lmsr_price(q, b, outcome)

    print(f"Shares bought: {shares_to_buy}")
    print(f"Starting price: {lmsr_price(initial_q, b, outcome):.4f}")
    print(f"Average fill price: {avg_fill:.4f}")
    print(f"Final price: {final_price:.4f}")
    print(f"Total cost: ${total_cost:.2f}")
    print(f"Price impact: {final_price - lmsr_price(initial_q, b, outcome):.4f}")
    return avg_fill

# Starting at even odds, buying 200 shares with b=100
simulate_buy_impact([0, 0], 200, b=100, outcome=0)
```

This matters enormously for sizing. You can't just calculate expected value at the current price and buy as much as you want. Your own buying degrades your average fill price.

## Putting It Together: A Simple Edge Calculator

```python
def analyze_market(
    current_q,          # current quantity vector [q_yes, q_no]
    b,                  # liquidity parameter
    your_probability,   # your estimate of YES probability
    max_shares=100      # maximum shares to consider buying
):
    """
    Given a market state and your probability estimate,
    calculate whether there's an edge and how much to buy.
    """
    current_price = lmsr_price(current_q, b, 0)
    edge = your_probability - current_price

    print(f"Market price: {current_price:.4f}")
    print(f"Your estimate: {your_probability:.4f}")
    print(f"Raw edge: {edge:.4f}")

    if abs(edge) < 0.02:
        print("Edge too small — no trade")
        return

    direction = 0 if edge > 0 else 1  # buy YES if positive edge, NO if negative
    direction_name = "YES" if direction == 0 else "NO"

    # Calculate EV at different sizes
    print(f"\nBuying {direction_name}:")
    print(f"{'Shares':>8} {'Avg Fill':>10} {'Total EV':>10}")

    q = list(current_q)
    total_cost = 0

    for shares in [10, 25, 50, 100]:
        q_temp = list(current_q)
        q_temp[direction] += shares
        total_cost = cost_of_trade(current_q, q_temp, b)
        avg_fill = total_cost / shares

        # EV calculation
        if direction == 0:  # bought YES
            ev = your_probability * shares - total_cost
        else:  # bought NO
            ev = (1 - your_probability) * shares - total_cost

        print(f"{shares:>8} {avg_fill:>10.4f} {ev:>10.4f}")

# Example: market at 35%, you think it's 55%
analyze_market(
    current_q=[-20, 20],  # someone has been selling YES
    b=100,
    your_probability=0.55,
    max_shares=100
)
```

## What This Actually Tells You

LMSR is elegant because it's self-consistent. Prices are always valid probabilities. The market maker's risk is bounded. And the mechanism creates genuine incentives for informed traders to move prices toward truth.

The math isn't magic. It's just calculus applied to belief aggregation. The softmax function, the cost function, the price impact formula - these are all derivable from first principles if you spend an afternoon with it.

What makes prediction markets interesting isn't that they're easy to beat. It's that when you have genuinely better information than the market - real research, domain expertise, faster data - the mechanism gives you a clean way to express that edge and get paid for being right.

The LMSR is the plumbing that makes that possible.
