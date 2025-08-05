# Time Series Analysis of Electronic Sales

**Project Title:** Time Series Analysis of Sales of Electronic Items

## 📖 Project Overview

This repository presents a comprehensive exploration and forecasting of daily electronic item sales over the year 2019. By applying classical time-series techniques—stationarity tests (ADF, KPSS), decomposition (STL), Box–Cox transformation—and moving-average modeling, we uncover patterns and build accurate forecasts to guide inventory and marketing decisions.

## 📂 Repository Structure

```
├── data/                    # Raw and transformed datasets
│   ├── sales_2019.csv       # Original daily sales records
│   └── transformed.csv      # Box–Cox and detrended series
├── notebooks/               # Jupyter notebooks detailing each step
│   ├── 1_EDA.ipynb          # Exploratory Data Analysis & visualization
│   ├── 2_stationarity.ipynb # ADF and KPSS tests, ACF plots
│   ├── 3_decomposition.ipynb# STL decomposition and residual analysis
│   ├── 4_transformation.ipynb # Box–Cox transformation and stationarity re-check
│   └── 5_forecasting.ipynb # MA(p) model selection and forecasting
├── src/                     # Python scripts/modules
│   ├── data_loader.py       # Data loading & preprocessing functions
│   ├── stats_tests.py       # Stationarity and ACF/PACF utilities
│   └── models.py            # MA model fitting and evaluation
├── results/                 # Figures and metrics
│   ├── figures/             # Plots: time series, decomposition, forecasts
│   └── metrics.md           # Summary: AIC, RMSE for MA(1)–MA(7)
├── requirements.txt         # Python dependencies
└── README.md                # Project overview and instructions
```

## 🗄️ Dataset

* **sales\_2019.csv**: Daily total sales amounts for various electronic products from January 1, 2019 to December 31, 2019.
* No missing values; each record has a timestamp and total sales figure.

## 🔍 Methodology

1. **Exploratory Data Analysis (EDA)**

   * Plot daily sales to observe trends and seasonal spikes (spring, October, December).
   * Fit a linear regression to confirm non-stationarity.

2. **Stationarity Testing**

   * **ADF Test** (p ≈ 0.477) and **KPSS Test** (p = 0.01) indicate non-stationary series.
   * ACF plot shows slow decay.

3. **STL Decomposition**

   * Decompose into trend, seasonal, and residual components.
   * Validate that residuals center around zero but still exhibit non-constant variance.

4. **Box–Cox Transformation**

   * Apply Box–Cox with λ = −0.115 to stabilize variance and reduce skewness.
   * Re-test stationarity: still non-stationary, require MA modeling on residuals.

5. **Forecasting with MA(p) Models**

   * Fit MA models of order p = 1…7 on the detrended, transformed series.
   * Compare using Akaike Information Criterion (AIC) and RMSE.
   * **MA(7)** selected (lowest AIC = −2050.39; RMSE = 0.0024).

## 📈 Results

* **MA(7)** model outperforms lower orders, capturing autocorrelation up to lag 7.
* Forecast vs. actual plots demonstrate high accuracy in short-term projections.
* Analysis confirms the cleaned residual behaves like white noise, meeting modeling assumptions.

## 🚀 Usage

To reproduce the analysis and forecasts, run the following notebooks in order:

```bash
jupyter notebook notebooks/1_EDA.ipynb
jupyter notebook notebooks/2_stationarity.ipynb
jupyter notebook notebooks/3_decomposition.ipynb
jupyter notebook notebooks/4_transformation.ipynb
jupyter notebook notebooks/5_forecasting.ipynb
```

Or execute the scripts in `src/`:

```bash
python src/data_loader.py
python src/stats_tests.py
python src/models.py
```

## 🔗 Colab Notebook

[Open in Colab](https://colab.research.google.com/drive/1m6ozdDKkaI6E7KIqKrzzIWyBqUM7qcJo?usp=sharing)
