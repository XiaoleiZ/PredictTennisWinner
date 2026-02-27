# Tennis Match Prediction Pipeline

This repository contains a streamlined Jupyter notebook for predicting WTA and ATP tennis match outcomes using the **Bradley-Terry model**. 

## Key Features

- **Game-Level Predictions**: Instead of predicting match outcomes directly, the model uses head-to-head dominance to predict *game-winning probability*. In this way, we make use of the richer information from historical game scores. Custom combinatorics convert these into match-winning probabilities based on strict tennis rules.
- **Walk-Through Fitting**: Evaluates tournaments in 2025 H2 one by one. The model trains strictly on matches completed *before* each tournament's start date to prevent data leakage.
- **Optimized Bayesian BT Model**: Incorporates player rankings as priors and uses vectorized analytic gradients (`L-BFGS-B`) for fast, instant training.

## Out-of-Sample Performance (2025 H2)
The models iterate through the 2025 H2 calendar tournament by tournament, testing blind predictions against implied probabilities derived directly from Bet365 odds.

### WTA Performance

| Model | Accuracy | LogLoss | Brier Score | Coverage |
| :--- | :--- | :--- | :--- | :--- |
| B365 implied probability | 67.70% | 0.5912 | 0.2026 | 99.11% |
| Bayesian BT | 66.47% | 0.6626 | 0.2219 | 86.28% |
| Baseline BT | 65.90% | 0.6344 | 0.2199 | 86.28% |

### ATP Performance (Best of 5 Supported)

| Model | Accuracy | LogLoss | Brier Score | Coverage |
| :--- | :--- | :--- | :--- | :--- |
| B365 implied probability | 66.04% | 0.5918 | 0.2048 | 99.44% |
| Bayesian BT | 63.49% | 0.6606 | 0.2300 | 90.95% |
| Baseline BT | 63.28% | 0.6446 | 0.2260 | 90.95% |


## What's Included
- Data automatically downloaded from Tennis-Data (`2022-2025`)
- Baseline & Bayesian Bradley-Terry Models
- Evaluation metrics: accuracy, log loss, brier score
- Benchmarking against Bookmaker (`B365`) implied probabilities
- Surface-level accuracy breakdowns

## Files
- `tennis_match_prediction.ipynb`: The end-to-end portfolio notebook containing the full pipeline.
