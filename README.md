# Analyzing and Forecasting Unemployment Rate Dynamics in Belgium 🇧🇪📉

[Wersja polska](README_pl.md)

## 📌 Project Objective
The main goal of this project is to analyze and forecast the macroeconomic variables shaping the dynamics of the unemployment rate in Belgium[.

## 📊 Data and Variables
The analysis is based on 84 quarterly observations spanning from Q1 2005 to Q4 2025.
* **Dependent Variable:** `unemp` – unemployment rate.
* **Independent Variables:** `production` (industrial production), `gdp` (Gross Domestic Product), `wcost` (unit labor costs), and `shock_2020_2022` (a dummy variable accounting for the Covid-19 pandemic and the war in Ukraine).

## 🛠️ Methodology
* Due to data non-stationarity (confirmed by the Augmented Dickey-Fuller test) and a lack of cointegration, transformations including logarithmic scaling and first differences were applied.
* An Autoregressive Distributed Lag (ADL) model was constructed, successfully capturing the time-delayed adjustment processes characteristic of the labor market[.

## 💡 Key Analytical Insights
* **GDP & Production Impact:** Consistent with Okun's Law, growth in GDP and industrial production (lagged by 1-3 quarters) stimulates labor demand, leading to a significant drop in unemployment dynamics.
* **Labor Costs:** An increase in unit labor costs (`wcost`) acts as a signal of an overheated, employee-driven market, resulting in a reduction in unemployment growth two quarters later.
* **Labor Market Flexibility:** Current unemployment dynamics are strongly dependent on past values – higher growth in the previous quarter tends to lower the rate in the current one, indicating a flexible and self-regulating market.
* **Macroeconomic Anomalies:**
  * The 2008-2009 financial shock did not increase unemployment, as European policies favored reducing working hours over mass layoffs.
  * Inflation was completely statistically insignificant, suggesting that strict inflation targeting by European states has effectively neutralized the traditional Phillips Curve relationship.

## 📈 Diagnostics and Forecasting
* **Goodness of Fit:** The model explains 59.8% (Adjusted R-squared) of the variance in unemployment dynamics, a highly satisfactory result for time-series data based on first differences.
* **Formal Testing:** The model successfully passed all statistical diagnostic tests (no autocorrelation via Durbin-Watson and LM tests, homoscedasticity via White's test, correct specification via RESET test, no multicollinearity via VIF, and normal distribution of residuals).
* **Forecast Accuracy:** The ex-post forecast is of very high quality – the mean error is merely 0.1%, and an impressive 98% of the forecast error is attributed to purely unpredictable random noise (UD proportion). In the baseline scenario, the ex-ante forecast behaves stably, smoothly dampening over time as it reverts to the mean.
