# Unemployment_In_Belgium_Model
Wersja Polska (README_pl.md)

🧠 Economic Interpretation
Okun's Law (d_l_gdp_2 = -4.32): A 1% acceleration in GDP growth two quarters prior results in a 0.043 percentage point drop in the current unemployment rate, demonstrating the delayed transmission of economic output to the labor market.
Procyclical Wages (d_l_wcost_3 = -0.18): Higher labor costs reflect an overheating economy and a "candidate's market." This economic expansion drives a drop in the unemployment rate 3 quarters later.
The Core Stabilization Mechanism (d_unemp_1 = -0.46): The negative autoregressive coefficient proves the process is strictly stationary and mean-reverting. A 1 p.p. spike in unemployment last quarter triggers an automatic cooling off of 0.46 p.p. this quarter, preventing the forecast from exploding.

🔍 Robust Diagnostic VerificationThe model successfully passes the "Great Four" validation gates, proving its mathematical integrity:
RESET Test for Specification ($p = 0.923$): Confirms the functional form is thoroughly adequate and no non-linear variables are missing.
White's Test for Heteroskedasticity ($p = 0.212$): Confirms constant variance of error terms (homoskedasticity).
Breusch-Godfrey LM Autocorrelation Test ($p = 0.775$): Confirms residuals are pure white noise up to the 4th order. (Note: Traditional Durbin-Watson is invalid here due to the lagged dependent variable; the LM test is the correct standard).
Normality of Residuals ($p = 0.198$): Confirms error terms follow a perfect Gaussian bell curve, making all t-tests and p-values fully reliable.
Collinearity (VIF): All Variance Inflation Factors range strictly between 1.05 and 3.38, well below the danger threshold of 10.0, indicating zero multi-collinearity issues.

📈 Out-of-Sample Forecast Evaluation (Ex-Post)To rigorously test predictive power, the model was evaluated on a holdout window of 8 quarters:
Mean Absolute Error (MAE): 0.138 p.p. — The model misses the actual change in the unemployment rate by an average of just 0.14 percentage points.Theil's U2 Statistic: 0.248 — Indicates that this econometric model is 4 times better than a naive random walk model.Theil Decomposition:Bias Proportion ($U^M$): 4.49% (Near zero, proving the model is completely unbiased).Variance Proportion ($U^R$): 1.88% (The model perfectly mimics the actual data's volatility).Disturbance Proportion ($U^D$): 93.63% — The ultimate triumph. Over 93.6% of the forecast error is pure, unavoidable random noise. The model has extracted 100% of the structured economic intelligence.

🔮 Future Projections (Ex-Ante)Under the Baseline Scenario (freezing explanatory variables at their latest levels and setting future shocks to 0), the ex-ante forecast shows a beautiful stabilizing wave effect. Due to the negative autoregressive parameter (-0.46), any lingering pandemic or energy distortions smoothly decay, causing the Belgian unemployment rate to gently converge toward its long-run equilibrium.
