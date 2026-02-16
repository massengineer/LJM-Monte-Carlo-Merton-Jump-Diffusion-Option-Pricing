# Model Risk in Option Pricing: From Black–Scholes to Jump Diffusion

This project, authored by **James Onyegbosi** and **Louis Massingham** (February 2026), explores the critical role of modelling assumptions in derivative pricing. It provides a detailed analysis of the transition from the traditional Black–Scholes framework to the structurally richer Merton Jump-Diffusion model.

## Project Overview

The aim of this notebook is to present the Black–Scholes model, introduce the Merton Jump-Diffusion alternative, and quantify the pricing errors—or **model risk**—that emerge when simpler models are applied to worlds governed by complex jump dynamics.

---

## 1. The Black–Scholes Model

The Black–Scholes model is a fundamental framework for pricing European-style options.

### Key Assumptions

* **Frictionless Market**: No transaction costs or bid-ask spreads; assets are infinitely divisible.
* **Continuous Trading**: Trading can occur at any point in time.
* **Constant Risk-Free Rate**: Investors can borrow or lend unlimited amounts at a constant rate.
* **Geometric Brownian Motion (GBM)**: Asset prices follow a stochastic differential equation (SDE) assuming constant drift and volatility, implying log-normally distributed prices.
* **No Arbitrage**: Risk can be eliminated through dynamic hedging.

### Implementation

The project implements the analytical Black–Scholes formula in Python and verifies the result using **Monte Carlo simulation**. The simulations demonstrate that under GBM assumptions, the Monte Carlo estimate converges to the analytical price.

---

## 2. Structural Limitations and Model Failure

The Black–Scholes framework often fails in real financial markets due to several "stylised facts":

* **Heavy Tails**: Real return distributions exhibit fat tails, meaning large moves happen more frequently than a Gaussian model predicts.
* **Volatility Clustering**: Volatility varies over time rather than remaining constant.
* **Jumps**: Asset prices often experience sudden discontinuities due to news or shocks, which is structurally impossible under GBM.
* **Volatility Smile/Skew**: Implied volatility varies systematically with strike price in real markets, contradicting the model's assumption of constant volatility.

---

## 3. The Merton Jump-Diffusion Model

To address these failures, the project introduces the **Merton Jump-Diffusion model**.

### Model Components

* **Continuous Diffusion**: Identical to the Black–Scholes diffusion term.
* **Jump Component**: A Poisson process governs the arrival of jumps, while jump sizes are log-normally distributed.

This model captures heavy-tailed distributions and discontinuous price paths that better match empirical financial data.

---

## 4. Quantifying Model Risk

Model misspecification risk is analysed by pricing options in a "true world" governed by jump-diffusion using a simpler Black–Scholes model.

### Findings

* **Systematic Bias**: Black–Scholes systematically misprices options when jumps are present, often underpricing out-of-the-money (OTM) options.
* **Tail Risk Underestimation**: The error grows as jump intensity () increases, as Black–Scholes fails to account for the increased probability of extreme outcomes.
* **Implied Volatility Smile**: When Jump-Diffusion prices are fed back into the Black–Scholes formula, they produce a "volatility smile," mirroring the patterns seen in actual market data.

---

## 5. Conclusion

The project concludes that pricing models are not just computational tools; they embed structural beliefs about market behaviour. Relying on simpler models, such as the Black–Scholes model, in environments with jumps leads to an underestimation of tail risk and mis-hedged positions.

---

### Prerequisites

* Python 3.x
* NumPy
* SciPy
* Matplotlib

### How to Use

1. Run the **Black-Scholes implementation** to establish a baseline price.
2. Execute the **Monte Carlo simulation** to visualise GBM and Jump-Diffusion paths.
3. Compare the **pricing errors** and **implied volatility curves** to diagnose model risk.
