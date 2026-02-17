# ⚽ FIFA World Cup 2026 Prediction Model

A probabilistic forecasting framework for the 2026 FIFA World Cup built using historical international match data, statistical goal models, machine learning benchmarks, and full tournament Monte Carlo simulation.

The goal of this project is not to produce a single deterministic bracket, but to model uncertainty properly and estimate realistic advancement probabilities.

---

## Overview

This project builds and compares multiple approaches to forecasting match outcomes and then propagates those probabilities through the official 48-team tournament structure.

Instead of selecting the most likely winner in each match, the model uses simulation to capture the inherent randomness of football and the nonlinear structure of knockout tournaments.

### Core Components

- Competitive match filtering (friendlies excluded)
- Home vs. neutral venue encoding
- Recency-weighted historical results
- Attack and defence strength estimation
- Poisson regression for goal modeling
- Negative Binomial regression to address overdispersion
- Machine learning benchmarks (e.g., Random Forest, Logistic Regression)
- Probability calibration analysis
- Monte Carlo tournament simulation

---

## Modeling Approach

### Goal-Based Statistical Models

The project begins with Poisson regression to model expected goals as a function of ranking differences, home advantage, and derived strength metrics.

Overdispersion is tested using Pearson χ² / degrees of freedom.  
Where variance exceeds the Poisson assumption, a Negative Binomial model is fitted to better reflect goal variability.

Match outcome probabilities are derived from the underlying goal distributions.

---

### Machine Learning Benchmarks

Multiclass classification models are trained as a comparison to the GLM-based approach.

Evaluation emphasizes probability quality rather than raw classification accuracy.

Metrics include:

- Log-loss  
- Multiclass Brier score  
- Accuracy (for context only)

Reliability diagrams are used to assess calibration and detect overconfidence.

---

### Monte Carlo Tournament Simulation

Predicted match probabilities are propagated through the official 2026 format using repeated simulation.

Each simulated tournament samples match outcomes according to predicted probabilities and advances teams accordingly.

Running thousands of simulations produces:

- Round of 16 probability  
- Quarterfinal probability  
- Semifinal probability  
- Final probability  
- Tournament win probability  

This captures compounding uncertainty across knockout rounds and avoids deterministic bracket bias.

---

## Tools

- Python  
- pandas  
- NumPy  
- statsmodels  
- scikit-learn  
- matplotlib  

---

## Purpose

This project demonstrates applied GLM modeling, overdispersion diagnostics, probability-based evaluation metrics, and simulation-based forecasting within a structured tournament environment.
