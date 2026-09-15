# Football Match Outcome Prediction

A machine learning and deep learning project for predicting **football match outcomes** — Home Win, Draw, or Away Win — using historical team performance.

## Models

* **XGBoost** – tabular baseline using engineered team statistics
* **LSTM** – learns patterns from recent match sequences
* **Transformer** – uses self-attention to model historical team form

## Approach

* Chronological train/validation split to prevent future-data leakage
* Engineered team form, win rate, goal difference, ratings, and home/away statistics
* Used the **last 3, 5, and 10 matches** as historical context
* Evaluated models using **Accuracy, Macro F1, Log Loss, and Brier Score**
* Performed a history-window ablation study

## Results

| Model       |   Accuracy |   Log Loss |
| ----------- | ---------: | ---------: |
| XGBoost     |     49.79% |     1.0096 |
| LSTM        |     49.18% |     1.0131 |
| Transformer | **49.83%** | **1.0080** |

The **Transformer** achieved the best overall validation performance, while XGBoost remained highly competitive.

Pipeline
Raw Match Data
       │
       ▼
Target Verification
       │
       ▼
Chronological Train / Validation Split
       │
       ├──────────────────────┐
       ▼                      ▼
Tabular Feature Engineering  Sequential Feature Construction
       │                      │
       ▼                      ├───────────────┐
    XGBoost                    ▼               ▼
                           LSTM          Transformer
                               │               │
                               └───────┬───────┘
                                       ▼
                              Probability Prediction
                                       │
                                       ▼
                              Model Comparison
