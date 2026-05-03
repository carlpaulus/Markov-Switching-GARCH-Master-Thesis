# Master Thesis – Markov-Switching Models & Cryptocurrencies

## Overview

This repository contains the Python implementation and supporting material for my **Master’s thesis**, completed in **2023** as part of the **Master in Applied Data Science** at **Frankfurt School of Finance & Management**.

The thesis, titled **“Markov-Switching Models & Cryptocurrencies”**, investigates whether Markov-Switching GARCH models can better capture the volatility dynamics of Bitcoin returns by explicitly modelling different latent market regimes.

The project combines financial econometrics, time series modelling, maximum likelihood estimation, regime-switching models, GARCH volatility dynamics and Python-based implementation.

## Academic context

- **Institution:** Frankfurt School of Finance & Management
- **Program:** Master in Applied Data Science
- **Year:** 2023
- **Project type:** Master’s thesis
- **Topic:** Markov-Switching GARCH models applied to cryptocurrency returns
- **Asset studied:** Bitcoin against USD
- **Main focus:** Regime-dependent conditional means and volatility dynamics

The thesis was supervised by:

- Prof. Dr. Jean-David Fermanian
- Prof. Dr. Lucas Böttcher

## Research objective

The objective of this thesis was to implement and analyze a **Markov-Switching GARCH model** for Bitcoin returns.

The central idea was to test whether the standard MS-GARCH framework could be improved by allowing each hidden regime to have its own conditional mean.

Many academic implementations of Markov-Switching GARCH models simplify the model by assuming zero conditional means. This thesis explores a more flexible specification in which each regime has a distinct conditional mean:

- one regime associated with bear-market behavior;
- one regime associated with bull-market behavior;
- one regime associated with more normal or intermediate market conditions.

The goal was therefore twofold:

1. to assess whether a multi-regime volatility model is useful for Bitcoin returns;
2. to investigate whether estimating regime-specific conditional means improves the economic interpretation and flexibility of the MS-GARCH model.

## Thesis summary

The thesis is structured around the following topics:

### 1. Literature review

The project builds on the academic literature on:

- GARCH models;
- Markov-Switching models;
- MS-GARCH models;
- cryptocurrency volatility;
- regime changes in Bitcoin markets;
- maximum likelihood estimation of hidden-state models.

The research is motivated by the fact that cryptocurrency returns often exhibit volatility clustering, fat tails, structural breaks and regime changes.

### 2. Data analysis

The empirical analysis focuses on Bitcoin price data downloaded from Yahoo Finance.

The data analysis includes:

- price series analysis;
- log-return computation;
- stationarity tests;
- investigation of regime changes;
- skewness and kurtosis analysis;
- autocorrelation analysis;
- comparison of return behavior across different market phases.

The data analysis supports the assumption that Bitcoin returns are not adequately described by a single homogeneous volatility regime.

### 3. MS-GARCH model

The model implemented in this repository is a Markov-Switching GARCH model with three latent regimes.

The conditional return process is modelled with regime-dependent means and regime-dependent conditional variances.

For each regime, the model estimates:

- a conditional mean `mu`;
- a GARCH constant `omega`;
- an ARCH coefficient `alpha`;
- a GARCH coefficient `beta`;
- transition probabilities between regimes.

The transition matrix is obtained through a reparametrization using unconstrained `gamma` parameters. This makes optimization more practical, because the transition probabilities must remain positive and each row of the transition matrix must sum to one.

### 4. Maximum likelihood estimation

The model is estimated through maximum likelihood.

The implementation includes:

- construction of regime-dependent conditional variances;
- recursive filtering of regime probabilities;
- calculation of the likelihood contribution at each time step;
- numerical optimization of the parameter vector;
- extraction of estimated parameters and regime probabilities.

The estimation relies on the Hamilton filter logic to update the probabilities of being in each latent regime over time.

### 5. Results

The thesis finds evidence that three hidden regimes provide a meaningful representation of Bitcoin return dynamics.

The estimated regimes can be interpreted as:

- a bear-market regime;
- a bull-market regime;
- a normal or intermediate regime.

The results suggest that regime-specific conditional means provide a more flexible and economically meaningful specification than assuming a common or zero conditional mean across all regimes.

The thesis also finds that:

- the estimated `omega` parameters are positive, which is coherent with the model;
- the `alpha` parameters are relatively small, suggesting that volatility is less sensitive to short-term shocks;
- the `beta` parameters are high, suggesting strong volatility persistence;
- the bull-market regime appears to be the most persistent;
- the bear-market regime appears to be less persistent and more likely to transition quickly to another state.

## Repository structure

```text
.
├── README.md
├── .gitignore
├── .gitattributes
├── MASTER_THESIS.pdf
│
└── msgarch/
    ├── __init__.py
    │
    ├── base/
    │   ├── __init__.py
    │   ├── model1.py
    │   ├── model2.py
    │   ├── model3.py
    │   ├── model4.py
    │   ├── model5.py
    │   ├── statistics.py
    │   │
    │   └── utils/
    │       └── __init__.py
    │
    └── results/
        ├── __init__.py
        └── estimation.py