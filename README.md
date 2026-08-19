# Attention-Based Multi-Resolution Deep Learning for Electricity Load Forecasting

An attention-based multi-resolution LSTM framework for multi-horizon electricity load forecasting in Tamil Nadu and Kerala, India.

## Overview

This project proposes MR-Attn-LSTM, a deep learning framework that captures electricity demand patterns at hourly, daily, and weekly resolutions using parallel LSTM branches and a Bahdanau attention mechanism.

The model simultaneously forecasts electricity demand at 1-hour, 6-hour, and 24-hour horizons.

The framework is evaluated using real-world hourly electricity demand data from TNEB and KSEB covering January 2023 to June 2025.

## Architecture

```text
Electricity Demand Data
        |
        v
Feature Engineering
        |
        v
Min-Max Normalization
        |
        +----------------+----------------+
        |                |                |
        v                v                v
     Hourly           Daily           Weekly
      LSTM             LSTM             LSTM
        |                |                |
        +----------------+----------------+
                         |
                         v
                  Concatenation
                         |
                         v
                Bahdanau Attention
                         |
                         v
                    Dense Layers
                         |
              +----------+----------+
              |          |          |
              v          v          v
             1-Hour     6-Hour     24-Hour
             Forecast   Forecast   Forecast
Dataset

The project uses real-world hourly electricity demand data from Tamil Nadu Electricity Board (TNEB) and Kerala State Electricity Board (KSEB).

Dataset period: January 2023 to June 2025

State	Observations	Maximum Demand
Tamil Nadu	21,888	20,393 MW
Kerala	21,888	5,762 MW

Total observations: 43,776 hourly records.

Features

The model uses 17 engineered features including:

Cyclical time features
1-hour lag
6-hour lag
12-hour lag
24-hour lag
48-hour lag
168-hour lag
24-hour rolling mean
24-hour rolling standard deviation
168-hour rolling mean
Model

MR-Attn-LSTM consists of:

Three parallel LSTM branches
Hourly, daily, and weekly temporal resolutions
Two-layer LSTM encoders
Bahdanau additive attention
Dense prediction layers
Three multi-horizon prediction heads

The model produces forecasts for:

1 hour ahead
6 hours ahead
24 hours ahead
Results
1-Hour Forecasting Performance
Model	Tamil Nadu MAPE	Kerala MAPE
Linear Regression	9.07%	5.90%
Random Forest	3.40%	3.10%
Gradient Boosting	3.10%	2.80%
LSTM	2.30%	2.10%
GRU	2.20%	2.00%
CNN-LSTM	2.00%	1.85%
MR-Attn-LSTM	1.50%	1.35%
Multi-Horizon Performance
State	Horizon	MAE	RMSE	MAPE
Tamil Nadu	1 Hour	220 MW	335 MW	1.50%
Tamil Nadu	6 Hours	355 MW	520 MW	2.40%
Tamil Nadu	24 Hours	540 MW	790 MW	3.70%
Kerala	1 Hour	46 MW	74 MW	1.35%
Kerala	6 Hours	74 MW	116 MW	2.15%
Kerala	24 Hours	122 MW	188 MW	3.60%

The proposed model improves MAE over CNN-LSTM by approximately 26.7% for Tamil Nadu and 27.0% for Kerala at the 1-hour horizon.

Technologies

Python
TensorFlow
Keras
Scikit-learn
NumPy
Pandas
Matplotlib
Google Colab
NVIDIA T4 GPU

Attention-Based Multi-Resolution Deep Learning Framework for Multi-Horizon Electricity Load Forecasting in Southern India
Author:
Marana Deepak






