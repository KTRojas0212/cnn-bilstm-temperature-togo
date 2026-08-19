# Explainable Comparative Deep Learning for Daily Temperature Forecasting: Lomé, Togo

MSc thesis project in Mathematics (Data Science), Pan African University /
Jomo Kenyatta University of Agriculture and Technology (JKUAT), Nairobi.

A benchmark of thirteen forecasting models for daily air temperature at Lomé,
Togo, spanning naïve, classical statistical, classical machine learning and
deep learning families including a hybrid CNN-BiLSTM-Attention architecture.

*Status:* in progress.

## Problem

Togo has a sparse observational network and limited local computing capacity
for numerical weather prediction, yet reliable daily temperature information
matters for agriculture, public health and energy planning. Deep learning is
often proposed as a low-cost alternative, but published studies rarely test
hybrid architectures against strong simple baselines on the same data. This
project builds that comparison for a data-scarce West African setting.

## Data

- *Source:* Agence Nationale de la Météorologie (ANAMET / Météo Togo)
- *Station:* Lomé Airport synoptic station
- *Period:* 2015–2026, daily resolution
- *Target variable:* daily air temperature (T2M)

Ground-station observations, not satellite or reanalysis estimates. Data
provenance was documented directly with ANAMET's Climatology Division. The raw
records are not redistributed in this repository; access requests go to ANAMET.

## Models compared

Thirteen models across four families, all trained and evaluated on identical
splits:

| Family | Models |
|--------|--------|
| Naïve | Persistence, Seasonal Naïve |
| Classical statistical |Linear Regression, ARIMA(5,0,0) |
| Classical machine learning |XGBoost, Random Forest  |
| Deep learning | ANN, LSTM, BiLSTM, GRU, CNN-LSTM, CNN-BiLSTM, CNN-BiLSTM-Attention |

The hybrid *CNN-BiLSTM-Attention* model combines 1D convolutional layers for
local feature extraction, bidirectional LSTM layers for temporal dependencies,
and an attention mechanism that weights time steps by their contribution to
the prediction.

## Results

| Rank | Model | MAE (°C) | RMSE (°C) | R² |
|------|-------|-----------|----------|-----|
| 1 | XGBoost |0.4749 | 0.6416| 0.8438 |
| 2 |GRU | 0.4842|0.6699 |0.8298 |
| 3 | Linear Regression|0.5258 | 0.7141 |0.8065 |
| 4 | CNN-BiLSTM |0.5423| 0.7157| 0.8057| 
| 5 | BiLSTM |0.5299 |0.7203 |0.8032 | 
| 6 | CNN-BiLSTM-Attention |0.5915 | 0.7713 |0.7743|
| 7 |Random Forest |0.6057 |0.8088 |0.7518  |

**The hybrid model did not win.** It ranked 6th of 13, behind XGBoost, GRU,
Linear Regression, CNN-BiLSTM and a plain BiLSTM. Differences between the
leading models were assessed with formal statistical significance testing
rather than by comparing point estimates alone.

This is the finding, not a failure of the experiment. Architectural complexity
did not translate into predictive advantage on this dataset, and a linear model
outperforming an attention-based hybrid is a result worth reporting for anyone
choosing methods for a similar data-scarce context.

<img width="2380" height="1330" alt="cell28_out02" src="https://github.com/user-attachments/assets/6be7d5ed-5ac0-48d7-94f7-bba4d77db9ab" />
