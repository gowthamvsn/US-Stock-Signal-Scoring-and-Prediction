# US Stock Signal Scoring and Prediction Pipeline

This project builds a full quantitative research pipeline for identifying
US equities with strong short-term upside potential using technical indicators,
fundamental filters, and machine learning.

The system combines:
- Market data ingestion
- Indicator engineering
- Forward-looking labeling
- Feature weighting
- Supervised ML classification
- Out-of-sample prediction

---

## Why This Project?

Most retail trading strategies rely on fixed indicator rules or black-box models.
This project bridges the gap by:

- Using **interpretable technical signals**
- Measuring **forward realized price movement**
- Assigning **data-driven weights** to indicators
- Validating signals with **machine learning**
- Producing **ranked probability-based predictions**

The goal is not day trading, but **systematic signal evaluation**.

---

## Data Sources

- **Market Data**: Yahoo Finance (Open, High, Low, Close, Volume)
- **Fundamentals**: EPS (Trailing 12 Months)
- **Universe**: Pre-filtered US equity tickers

> ⚠️ Raw data files are not included due to size and API constraints.


---

## Pipeline Overview

### Stage 1: Data Collection
- Incremental OHLCV download
- Master dataset maintenance
- EPS enrichment

### Stage 2: Feature Engineering
Technical indicators including:
- RSI, MACD, ATR, ADX
- Bollinger Bands (log-space)
- Stochastic Oscillator
- OBV, ROC, CCI
- Garman-Klass volatility

### Stage 3: Label Construction
- Forward-looking max price over future window
- Binary target: ≥ 6% gain

### Stage 4: Signal Scoring
- Indicator-target correlations
- Discrete weight assignment
- Composite signal score

### Stage 5: Machine Learning
- Random Forest classifier
- Feature importance validation
- Train / test evaluation

### Stage 6: Prediction
- Apply trained model to new data
- Output ranked probability scores

---

## File Structure

```
US-Stock-Signal-Scoring-and-Prediction/
├── src/
│   ├── build_dataset_and_scores.py     # Data download, indicators, scoring
│   └── train_and_predict_model.py      # ML training + future predictions
│
├── data/
│   └── README.md                       # Dataset & file expectations
├── README.md
├── requirements.txt
└── .gitignore
```
