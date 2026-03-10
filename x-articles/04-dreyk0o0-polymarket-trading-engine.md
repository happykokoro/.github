# Polymarket Trading Engine Using MIT Financial Mathematics Models

**Author:** DreykØ (@dreyk0o0)
**Source:** https://x.com/dreyk0o0/status/2030759824422490125
**Date:** Mar 9, 2026
**Stats:** 22 replies · 95 reposts · 721 likes · 111K views

![Embedded: Video/screenshot of "QUANTX FACTOR ENGINE" dashboard showing portfolio value chart climbing from ~$16K to ~$18K, with trading positions and Sharpe ratio data](screenshot-dashboard)

---

I spent a few days studying **MIT's Financial Mathematics course.**

**Then i tried to do a Polymarket trading engine** using the same models hedge funds use.

**The results surprised me.**

The new engine runs a **factor + stochastic volatility model** across Polymarket markets.

Core components:

**Factor model**
Rᵢ = αᵢ + Σ βᵢk f_k + εᵢ

**Volatility clustering**
σ²ₜ = α₀ + α₁ε²ₜ₋₁ + β₁σ²ₜ₋₁ (GARCH)

**Portfolio risk**
σ²ₚ = wᵀΣw

**The idea is simple.**

Most traders look at markets **individually.**

But markets **actually move in hidden factors.**

Politics sentiment
macro narratives
crypto momentum
event cycles

Once you model those factors, the correlations become **predictable.**

The engine now:

- extracts factors with **PCA**
- models volatility with **GARCH**
- sizes positions with portfolio risk constraints
- executes arbitrage and momentum signals

**Current dashboard:**

**$16,000 → $18,152**
**68% win rate**
**Sharpe: 8.8**

**I stopped looking at Polymarket as individual bets.**

Instead I treated it like a **portfolio of correlated assets.**

That **changed** everything about how the system trades.

> Quote: Roan (@RohOnChain) · Mar 2 Article
> "MIT's Quant Course Decoded for Every Prediction Market Trader"
> I'm going to break down every key concept from MIT's 20+ hour Financial Mathematics course and show you exactly how each one applies to trading on Prediction Markets. Let's get straight to it...
