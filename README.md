# Extreme Value Theory Bachelor's Thesis

This repository contains the empirical work for a bachelor's thesis on the
financial applications of Extreme Value Theory (EVT). The main focus is whether
EVT methods can describe cryptocurrency tail risk and improve the measurement
of losses during extreme market events.

The project combines three related pieces of analysis:

- Examination of stylized facts in cryptocurrency returns, including heavy
  tails, volatility clustering, asymmetry, and calendar effects.
- Comparison of tail-risk characteristics across cryptocurrencies and
  traditional financial assets using EVT and GARCH-EVT methods.
- Backtesting of Value-at-Risk (VaR) and Expected Shortfall (ES) estimates
  based on Generalized Pareto, Normal, Student-t, and empirical approaches.

## Repository Structure

```text
.
|-- Bachelors_Thesis/
|-- Data/
|-- Extreme_Value_Theory/
|-- Research_Papers/
|-- LICENSE
|-- README.md
`-- REQUIREMENTS.txt
```

## Folder Contents

### `Bachelors_Thesis/`

This folder contains the final written thesis.

Files:

- `Bachelors_Thesis_Czachesz.pdf`

  - Final bachelor's thesis document.
  - Presents the theoretical background, methodology, empirical analysis, and
    conclusions of the project.

### `Data/`

This folder contains the historical market data used by the notebooks. The
datasets include daily price series and Binance-style OHLCV data for
cryptocurrencies and traditional financial assets.

Files:

- `bnbusdt_data_20170817_20241011.xlsx`

  - BNB/USDT OHLCV data.
  - Used in the cryptocurrency stylized-facts analysis.
- `btcusd_data_20100719_20250516.xlsx`

  - Long-run BTC/USD historical price series.
  - Used in the EVT tail-risk and VaR/ES analyses.
- `btcusd_data_2017-08-17_2025-05-28_binance.xlsx`

  - Bitcoin OHLCV data from the Binance market period.
  - Used for return construction and cryptocurrency comparisons.
- `btcusd_data_20170817_20241231.xlsx`

  - Bitcoin OHLCV data through December 2024.
  - Used in the stylized-facts notebook.
- `ethusd_data_2017-08-17_2025-05-28_binance.xlsx`

  - Ethereum OHLCV data from the Binance market period.
  - Used for return construction and cryptocurrency comparisons.
- `ethusd_data_20170817_20241231.xlsx`

  - Ethereum OHLCV data through December 2024.
  - Used in the stylized-facts notebook.
- `ethusd_data_20180209_20250516.xlsx`

  - Long-run ETH/USD historical price series.
  - Used in the EVT tail-risk and VaR/ES analyses.
- `eurusd_1975-01-02_2025-05-16.xlsx`

  - Historical EUR/USD exchange-rate series.
  - Included as a traditional-market comparison dataset.
- `solusdt_data_20170817_20241231.xlsx`

  - SOL/USDT OHLCV data.
  - Used in the cryptocurrency stylized-facts analysis.
- `sp500_data_19480416_20250516.xlsx`

  - Long-run S&P 500 historical price series.
  - Used as an equity-market comparison in the EVT analysis.
- `sp500_data_20170817_20241231.xlsx`

  - S&P 500 market data aligned with the cryptocurrency comparison period.
  - Used in the stylized-facts analysis.
- `xau_1969-01-31_2025-05-09.xlsx`

  - Long-run Gold/XAU historical price series.
  - Used as a traditional safe-haven comparison in the tail-risk analysis.

### `Extreme_Value_Theory/`

This folder contains the main empirical notebooks for the thesis research
questions.

Files:

- `Stylized_Facts_Cryptocurrencies.ipynb`

  - Examines the statistical properties of BTC, ETH, BNB, and SOL returns.
  - Calculates log returns and compares cryptocurrency behavior with the
    S&P 500.
  - Studies fat tails through kurtosis and return-distribution diagnostics.
  - Tests for volatility clustering using ARCH tests and ARCH/GARCH models.
  - Measures return asymmetry through skewness.
  - Uses Augmented Dickey-Fuller tests to examine stationarity.
  - Studies changing relationships between cryptocurrencies and equities.
  - Tests weekend, overnight, intraday, and day-of-the-week effects using
    non-parametric methods such as Kruskal-Wallis and Friedman tests.
- `Tail_Risk_Characteristics.ipynb`

  - Addresses how tail-risk characteristics differ between cryptocurrencies
    and traditional financial markets.
  - Constructs comparable log-return datasets for Bitcoin, Ethereum, Gold,
    the S&P 500, and EUR/USD.
  - Fits Normal, Student-t, Laplace, Generalized Pareto, and Generalized Extreme
    Value distributions.
  - Applies the Peaks Over Threshold approach to left and right return tails.
  - Compares skewness, kurtosis, GPD shape parameters, VaR, and ES across
    assets.
  - Uses statistical tests and distribution plots to compare empirical returns
    with conventional parametric assumptions.
  - Combines GARCH volatility filtering with EVT tail fitting for Bitcoin,
    Ethereum, and Gold.
- `EVT-based_VaR_ES.ipynb`

  - Addresses whether EVT-based models provide better risk assessment for
    extreme cryptocurrency events.
  - Builds independent BTC, ETH, and weekend-return datasets for backtesting.
  - Produces rolling 95% VaR estimates using empirical, Normal, Student-t, and
    GPD approaches.
  - Evaluates VaR forecasts using breach counts and Lopez-style loss measures.
  - Produces rolling ES estimates and compares model performance after VaR
    exceedances.
  - Visualizes quarterly risk estimates, daily breaches, and ES exceedances.
  - Finds that GPD-based estimates are often more conservative and frequently
    outperform conventional distributional assumptions, particularly for VaR.

### `Research_Papers/`

This folder contains background literature used to motivate the methodology and
interpretation.

Files:

- `Extreme_Value_Theory_Zhang.pdf`

  - Research paper on extreme relationships between cryptocurrency returns and
    trading volumes.
  - Provides background for the application of EVT to high-frequency
    cryptocurrency markets.

## Setup

Create and activate a virtual environment, then install the requirements:

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r REQUIREMENTS.txt
```

On macOS or Linux, activate the environment with:

```bash
source .venv/bin/activate
```

Then start Jupyter:

```bash
jupyter notebook
```

## Suggested Reading Order

1. `Bachelors_Thesis/Bachelors_Thesis_Czachesz.pdf`

   - Best for the full research narrative, theoretical framework, and
     conclusions.
2. `Extreme_Value_Theory/Stylized_Facts_Cryptocurrencies.ipynb`

   - Best for understanding the empirical behavior that motivates the use of
     heavy-tail and volatility models.
3. `Extreme_Value_Theory/Tail_Risk_Characteristics.ipynb`

   - Best for the cross-asset EVT, POT, distribution-fitting, and GARCH-EVT
     analysis.
4. `Extreme_Value_Theory/EVT-based_VaR_ES.ipynb`

   - Best for the rolling risk-model backtests and comparison of VaR and ES
     methods.

## Methodological Summary

The project models asset log returns with particular attention to observations
in the extreme tails of the distribution. The Peaks Over Threshold framework
is used to identify sufficiently extreme returns and fit a Generalized Pareto
Distribution to the resulting exceedances. Estimated shape parameters and tail
risk measures are then compared across cryptocurrencies and traditional
financial assets.

The analysis also combines GARCH volatility models with EVT. GARCH filtering
accounts for time-varying volatility and volatility clustering before the
remaining standardized extremes are modeled. This helps distinguish changing
market volatility from the underlying heaviness of the return tails.

The VaR and ES notebook complements the cross-asset analysis by evaluating
forecast performance through rolling backtests. Empirical, Normal, Student-t,
and GPD estimates are compared using observed breaches, exceedance behavior,
and loss measures. Together, the notebooks assess both the statistical fit and
the practical risk-management value of EVT-based methods.
