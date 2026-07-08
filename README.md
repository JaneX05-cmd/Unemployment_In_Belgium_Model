# 📈 Macroeconomic Forecasting & Econometric Analysis: Belgium Unemployment Rate Dynamics
Developed an advanced Autoregressive Distributed Lag (ADL) model on first differences to analyze and forecast the quarterly unemployment rate in Belgium (2005–2025). This repository showcases a complete, production-grade econometric workflow designed to bridge macroeconomic theory with rigorous statistical verification—ideal for Data Analyst and Economic Research roles.

---

## 🌍 Language Options / Wersje Językowe
- [English Version](#-english-version)
- [Wersja Polska](#-wersja-polska)

---

# 🇬🇧 English Version

## 🎯 Project Objective & Overview
The goal of this project is to model, validate, and forecast the quarterly dynamics of the Belgian unemployment rate. By leveraging core economic principles—such as **Okun's Law** and the **Phillips Curve**—the project shifts away from naive level-regressions to analyze pure short-term dynamics, providing highly reliable ex-ante projections under a baseline scenario.

### 🚀 Key Recruiter Insights (Why this project stands out)
- **Advanced Time-Series Modeling:** Avoided the common pitfall of spurious regression by performing stationarity tests (ADF) and the **Engle-Granger Cointegration Test**.
- **Rigorous Diagnostic Backing:** The final model doesn't just look good; it strictly satisfies all classical linear regression model (CLRM) assumptions, achieving a spectacular **RESET test score ($p = 0.923$)** and clean normality of residuals ($p = 0.198$).
- **Economic Intelligence:** Successfully modeled structural breaks using dummy variables for the COVID-19 pandemic and Ukraine war shock, while empirically identifying the **flattening of the Phillips Curve** by dropping an insignificant inflation variable.
- **High-Precision Evaluation:** Validated on an out-of-sample test window, achieving a Mean Absolute Error (MAE) of just **0.14 percentage points** and a **Theil's U2 of 0.248**, proving it beats a naive random walk model 4-fold.

---

## 🛠️ Methodology & Theoretical Framework

### 1. Cointegration Testing (Why No ECM?)
Standard macroeconomic levels are inherently non-stationary ($I(1)$). To test for a long-run equilibrium, an **Engle-Granger Cointegration Test** was conducted on the residuals ($\hat{u}$).
- **Result:** The unit-root hypothesis for $\hat{u}$ could not be rejected ($p = 0.8307$).
- **Methodological Choice:** Because the variables are **not cointegrated**, building an Error Correction Model (ECM) would be a methodological error. Consequently, the relationship was modeled purely in **first differences ($\Delta$)** to capture short-run dynamics safely.

### 2. Variable Definitions & Transformations
To adhere to econometric best practices and comply with recommendations regarding rates, the dependent variable remains in percentage points, while nominal/index independent variables are log-transformed to represent growth rates:
- `d_unemp`: Quarterly change in the unemployment rate (in percentage points) — **Dependent Variable**.
- `d_l_gdp`: Quarterly GDP growth rate ($\Delta \ln(\text{GDP})$).
- `d_l_production`: Quarterly industrial production growth rate ($\Delta \ln(\text{Production})$).
- `d_l_wcost`: Quarterly growth rate of Unit Labor Costs ($\Delta \ln(\text{wcost})$).
- `shock_2020_2022_1`: Lagged binary variable capturing black swan events (COVID-19 lockdowns & energy crises).

---

## 📊 Model Specification & Estimation Results

An Autoregressive Distributed Lag model with specific lag structures was estimated via Ordinary Least Squares (OLS) with the intercept removed to eliminate unnecessary drift:

```text
Model 11: OLS, using observations 2006:2-2025:2 (T = 77)
Dependent variable: d_unemp

                      Coefficient   Std. Error   t-ratio   p-value 
  -----------------------------------------------------------------
  d_l_wcost_3          −0.182477    0.0909272    −2.007    0.0486   **
  d_l_production_1     −3.83465     1.22362      −3.134    0.0025   ***
  d_l_production_4     −3.03808     1.18772      −2.558    0.0127   **
  d_l_gdp_1            −2.39867     0.938317     −2.556    0.0127   **
  d_l_gdp_2            −4.32282     0.900677     −4.800    1.46e-05 ***
  shock_2020_2022_1     0.487989    0.126809      3.848    0.0003   ***
  d_unemp_1            −0.462104    0.0889766    −5.194    1.94e-06 ***

Centered R-squared: 0.583819
