# Predicting Turkish Airlines Stock Prices Using N-BEATS, TFT, and Informer

Comparative time series forecasting of Turkish Airlines (THYAO.IS) stock prices using deep learning models during a period of high inflation and economic uncertainty in Turkey.

**Authors:** Maria Immaculata Dyah Hita Widowati, Nindya Eka Putri Ramadhani, Ruth Wahyu Sedjati Priyambodo, Gita Damayanti, and Faiz Nabilianto

**Institution:** Department of Statistics, Institut Teknologi Sepuluh Nopember (ITS), Surabaya, Indonesia

---

## Table of Contents

- [Project Overview](#project-overview)
- [Domain and Business Understanding](#domain-and-business-understanding)
- [Research Objectives](#research-objectives)
- [Dataset and Data Understanding](#dataset-and-data-understanding)
- [Methodology](#methodology)
- [Forecasting Models](#forecasting-models)
- [Model Evaluation](#model-evaluation)
- [Results and Discussion](#results-and-discussion)
- [Feature Contribution Analysis](#feature-contribution-analysis)
- [Conclusion](#conclusion)
- [Limitations](#limitations)
- [References](#references)
- [Project Structure](#project-structure)

---

## Project Overview

Stock prices are influenced by historical price movements, market volatility, and broader economic conditions. Forecasting becomes particularly challenging in markets experiencing prolonged inflation and macroeconomic uncertainty.

This project investigates the performance of three deep learning models—**N-BEATS, Informer, and Temporal Fusion Transformer (TFT)**—for forecasting the adjusted closing price of Turkish Airlines (THYAO.IS).

The study uses daily historical stock data from Yahoo Finance covering January 2021 to September 2025. The models are evaluated using rolling cross-validation to assess their forecasting performance across successive time periods.

### Key Highlights

- **Asset:** Turkish Airlines (THYAO.IS)
- **Data period:** January 4, 2021 – September 4, 2025
- **Observations:** 1,167 daily records
- **Forecasting target:** Adjusted closing price
- **Models:** N-BEATS, Informer, and TFT
- **Evaluation:** RMSE, MAE, MAPE, and rolling cross-validation
- **Additional analysis:** Feature contribution through ablation analysis

## Domain and Business Understanding

### Domain Background

Turkish Airlines operates in an industry exposed to changes in fuel costs, exchange rates, international travel demand, and economic conditions. During periods of high inflation, these factors may contribute to greater uncertainty in financial markets and fluctuations in stock prices.

Historical stock price data can provide useful information for identifying temporal patterns and evaluating potential forecasting approaches.

### Problem Statement

This project addresses the following questions:

1. How effectively can historical price information capture temporal patterns in Turkish Airlines stock prices?
2. Which of the three deep learning models provides the best forecasting performance?
3. How does incorporating additional market variables affect forecasting accuracy?

### Project Goals

- Develop stock price forecasting models using N-BEATS, Informer, and TFT.
- Compare model performance using consistent evaluation metrics.
- Examine whether additional market variables improve forecasting accuracy.
- Identify the model that performs best according to the reported evaluation results.

## Research Objectives

The main objective is to evaluate alternative deep learning architectures for time series forecasting in a volatile market environment.

The analysis compares a univariate forecasting approach, which focuses on historical target values, with a multivariate approach that incorporates additional market information.

The findings are intended to support methodological evaluation and provide insights into the challenges of forecasting stock prices. They are not intended to provide guaranteed investment returns.

## Dataset and Data Understanding

### Data Source

The dataset was obtained from Yahoo Finance using the ticker symbol `THYAO.IS`, representing Turkish Airlines shares traded on Borsa Istanbul.

**Data period:** January 4, 2021 – September 4, 2025  
**Number of observations:** 1,167

The dataset contains daily stock market information.

### Research Variables

| Variable | Description |
|---|---|
| Date | Trading date |
| Open | Opening stock price |
| High | Highest stock price during the trading day |
| Low | Lowest stock price during the trading day |
| Close | Closing stock price |
| Adj Close | Adjusted closing stock price; the forecasting target |
| Volume | Number of shares traded |

The target variable is the adjusted closing price (`Adj Close`). Historical observations are used to capture temporal dependencies in the stock price series.

### Data Understanding and Exploratory Analysis

The initial analysis examines historical price movements and trading activity to understand the characteristics of the dataset before model development.

The analysis focuses on:

- Historical stock price movements.
- Price fluctuations during the observation period.
- Relationships between market variables.
- Data quality and preprocessing requirements.
- The temporal patterns relevant to forecasting.

## Methodology

The project follows a time series forecasting workflow.

1. **Data collection:** Obtain historical THYAO.IS stock data from Yahoo Finance.
2. **Data preprocessing:** Examine missing values, duplicate observations, correlations, and potential outliers.
3. **Data splitting:** Separate the historical data into training and evaluation periods while preserving temporal order.
4. **Feature preparation:** Construct historical input sequences and prepare the variables required by each model.
5. **Model development:** Train N-BEATS, Informer, and TFT.
6. **Rolling cross-validation:** Evaluate predictions over successive time windows.
7. **Model comparison:** Compare forecasting errors using RMSE, MAE, and MAPE.
8. **Post-hoc analysis:** Investigate the contribution of external variables through ablation analysis.

### Rolling Cross-Validation

Rolling cross-validation is used to evaluate the models across successive time periods rather than relying solely on a single fixed evaluation window.

The report describes an evaluation period containing 228 observations, with a validation window of 10 observations and a step size of one. The evaluation window therefore advances one observation at a time.

This approach is designed to assess model performance under changing market conditions while preserving the chronological structure of time series data.

## Forecasting Models

### 1. N-BEATS

N-BEATS (Neural Basis Expansion Analysis for Time Series Forecasting) is a deep learning architecture based on fully connected neural network blocks.

In this project, N-BEATS is applied to model historical stock price patterns and capture nonlinear temporal relationships.

### 2. Informer

Informer is a Transformer-based architecture designed for long-sequence time series forecasting. It uses ProbSparse self-attention to reduce the computational complexity associated with conventional attention mechanisms.

The study uses Informer as a univariate model that focuses on historical THYAO stock prices.

### 3. Temporal Fusion Transformer (TFT)

TFT is designed for multi-horizon forecasting and combines attention mechanisms, gating components, and variable selection.

In this study, TFT incorporates additional market variables, including Open, High, Low, and Volume, alongside historical information to investigate whether multivariate inputs improve forecasting performance.

## Model Evaluation

Forecasting accuracy is evaluated using the following metrics.

| Metric | Purpose |
|---|---|
| RMSE | Measures the square root of the average squared prediction error |
| MAE | Measures the average absolute difference between actual and predicted values |
| MAPE | Measures the average absolute prediction error as a percentage of actual values |

Lower values indicate better forecasting accuracy for these error metrics, provided the metrics are calculated on comparable evaluation data.

## Results and Discussion

The report presents the following model evaluation results.

| Model | MAPE | RMSE |
|---|---:|---:|
| N-BEATS | 1.55% | 6.0910 |
| Informer | 2.08% | 7.5920 |
| TFT | 1.76% | 6.6567 |

According to the numerical results in the evaluation table, **N-BEATS records the lowest MAPE and RMSE** among the three models.

The results indicate that a univariate architecture is not automatically superior to a multivariate architecture. Model performance depends on the temporal patterns learned, the input configuration, and the characteristics of the evaluation period.

The study also examines the behavior of the models during periods of changing stock price trends. The report describes differences in how the models follow short-term movements and fluctuations.

*Note: The original report's abstract and some discussion paragraphs identify Informer as the best model, which conflicts with the numerical evaluation table above. The final interpretation should be reconciled with the original experiment outputs before publication.*

## Feature Contribution Analysis

A post-hoc ablation analysis is conducted to examine the contribution of external variables used by TFT.

The analysis masks one variable at a time and evaluates the resulting change in Mean Absolute Error (MAE).

The reported findings indicate that:

- **Open** has the largest positive contribution to the model's performance among the examined external variables.
- **Volume** and **Low** also contribute to the model's predictions.
- **High** shows a negative contribution in the reported analysis, suggesting that its inclusion may reduce forecasting performance under the tested configuration.

These findings illustrate why adding more input variables does not necessarily lead to better predictions.

## Conclusion

This project compares three deep learning approaches for forecasting Turkish Airlines stock prices using historical daily market data from 2021 to 2025.

The analysis combines time series preprocessing, deep learning model development, rolling cross-validation, quantitative error evaluation, and post-hoc feature contribution analysis.

The numerical evaluation table reports the lowest MAPE and RMSE for N-BEATS, while the original report's narrative also discusses Informer's forecasting performance. The final model selection should therefore be verified against the original experiment outputs before drawing a definitive conclusion.

More broadly, the project highlights the importance of evaluating forecasting models using time-aware validation and considering whether additional market variables provide useful predictive information.

## Limitations

- The analysis focuses on a single stock, Turkish Airlines (THYAO.IS), so the findings may not generalize to other assets or markets.
- Historical price patterns may change as market conditions evolve.
- Forecasting errors can increase during unexpected market events.
- The reported results depend on the selected model configurations and evaluation procedure.
- Forecasting accuracy does not guarantee investment profitability.
- The model ranking and narrative conclusions require reconciliation with the original experiment outputs.

## References

The project draws on research related to deep learning for time series forecasting, including the original studies introducing N-BEATS, Informer, and Temporal Fusion Transformer.

The historical stock price data was obtained from Yahoo Finance.

For the full bibliography, see the references section in the accompanying research report.

## Project Structure

```text
turkish-airlines-stock-forecasting/
├── README.md
├── notebooks/
│   └── stock_price_forecasting.ipynb
├── reports/
│   └── turkish_airlines_stock_forecasting.pdf
├── images/
│   ├── stock_price_trend.png
│   ├── rolling_forecast_comparison.png
│   └── model_evaluation.png
└── requirements.txt
```

*The file and image names above are suggested examples. Replace them with the actual files included in the repository.*

---

**Project Type:** Time Series Forecasting | Deep Learning | Financial Data Analysis

**Institution:** Department of Statistics, Institut Teknologi Sepuluh Nopember (ITS)
