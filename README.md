# cnn-bilstm-temperature-togo

# Daily Temperature Prediction over Togo with a Hybrid CNN-BiLSTM-Attention Model

MSc thesis project — Mathematics (Data Science), Pan African University /
Jomo Kenyatta University of Agriculture and Technology (JKUAT), Nairobi.

**Status:** in progress. The results below are preliminary and will be
updated when the final evaluation is complete.

## Problem

Togo has a sparse observational network and limited local computing capacity
for numerical weather prediction, yet reliable daily temperature information
matters for agriculture, public health and energy planning. This project asks
whether a deep learning model trained on freely available satellite and
reanalysis data can produce accurate daily temperature forecasts for a West
African coastal site, as a low-cost complement to dynamical models.

## Data

- **Source:** NASA POWER (MERRA-2 and CERES SYN1deg products)
- **Location:** Lomé, Togo
- **Period:** January 2020 – September 2025, daily resolution
- **Target variable:** T2M (temperature at 2 metres)

Raw data is not stored in this repository. It can be downloaded directly from
the NASA POWER data access portal: https://power.larc.nasa.gov/

## Method

The model combines three components in a single architecture:

1. **1D convolutional layers** — extract local patterns from the input
   sequences.
2. **Bidirectional LSTM layers** — capture temporal dependencies in both
   directions across the sequence.
3. **Attention mechanism** — weights time steps according to their
   contribution to the prediction.

Preprocessing covers quality control, gap handling, normalisation,
sliding-window sequence construction, and a chronological train/validation/test
split.

## Results (preliminary)

| Metric | Value |
|--------|-------|
| RMSE   | [insert] °C |
| MSE    |  |
| R²     |  |

Baseline comparison is in progress.

