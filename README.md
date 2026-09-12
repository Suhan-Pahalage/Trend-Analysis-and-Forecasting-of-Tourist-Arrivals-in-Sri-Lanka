# Trend-Analysis-and-Forecasting-of-Tourist-Arrivals-in-Sri-Lanka

# Tourist Arrival Dynamics and Time Series Forecasting in Sri Lanka (1971–2023)

A comprehensive empirical research project evaluating historical tourist arrival dynamics in Sri Lanka over a 52-year period (1971–2023) using statistical trend analysis, multi-variable linear regression, and Seasonal Autoregressive Integrated Moving Average (SARIMA) time series modeling.

---

## 📋 Academic Metadata
* **Institution**: University of Sri Jayewardenepura
* **Course**: STA 351 2.0 Research Methodology
* **Authors**: S. Pahalage, W.H.S.C. Wijayarathna, I.A.A. Wathsala, S.P.O.V. Pathirathna, R.T.T. Budunwela
* **Primary Tools**: R, Minitab

---

## 🛠️ Methodology & Data Preprocessing

This project employs a dual-software statistical framework to analyze tourist arrival patterns, socio-demographics, and forecasting models:

* **Minitab**:
  * **Descriptive Statistics**: Evaluated socio-demographic features (age, gender, occupation, visit purpose) and seasonal variations.
  * **Linear Regression & Trend Analysis**: Modeled long-term linear trajectories for trip purposes, duration of stay, demographics, and source regions.
* **R Software**:
  * **Dataset Partitioning**: The estimation/training sample spans **January 1971 to December 2021**, while **January 2022 to December 2023** is reserved for out-of-sample model evaluation and testing[cite: 1].
  * **Missing Value Imputation**: Severe shocks (April 2019 Easter Bombings) and COVID-19 pandemic airport closures (April 2020 – December 2020) caused missing arrival records[cite: 1]. These gaps were imputed using statistical estimation techniques in R prior to time series modeling[cite: 1].
  * **Stationarity & SARIMA**: Evaluated stationarity via Augmented Dickey-Fuller (ADF) testing, differencing transformations, autocorrelation profiling (ACF/PACF), candidate model fitting, and validation[cite: 1].

---

## 📊 Empirical Results & Demographic Trajectories

### 1. Overall Long-Term Trend (1971–2023)
Linear regression demonstrates a steady, long-term upward trajectory in annual arrivals, expanding by an average of **26,452 visitors per year**[cite: 1].

* **Linear Trend Model**: $$Y_t = -135,145 + 26,452 \cdot t$$
* **Goodness of Fit**: $R^2 = 50.88\%$ ($p < 0.001$), accounting for over half of total historical variance[cite: 1].

---

### 2. Seasonal Variations (12-Month Moving Average)
Seasonal indices derived from monthly arrival data reveal distinct peak and low travel windows[cite: 1]:

* **Peak Season**: **December** (1.306) and **January** (1.263) — arrivals exceed the annual monthly baseline by 26% to 30%[cite: 1].
* **Low Season**: **May** (0.691) and **June** (0.706) — arrivals drop approximately 30% below the baseline[cite: 1].

| Month | Seasonal Index | Month | Seasonal Index |
| :--- | :--- | :--- | :--- |
| **Jan** | 1.26275 | **Jul** | 1.00147 |
| **Feb** | 1.22553 | **Aug** | 0.99559 |
| **Mar** | 1.19746 | **Sep** | 0.80866 |
| **Apr** | 0.90102 | **Oct** | 0.87534 |
| **May** | 0.69053 | **Nov** | 1.02908 |
| **Jun** | 0.70613 | **Dec** | 1.30645 |

---

### 3. Purpose of Visit Trends (1991–2020)

| Purpose of Visit | Slope ($m$) | Intercept ($c$) | $R^2$ | Trend | Strength |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Pleasure / Holiday** | -0.7076 | 93.833 | 0.406 | Decrease | Moderate |
| **Visiting Friends & Relatives** | +0.5677 | -1.918 | 0.556 | Increase | Moderate |
| **Business** | +0.0145 | 6.029 | 0.001 | Increase | Very Weak |
| **Religious & Cultural** | -0.0007 | 1.039 | 0.000 | Decrease | Very Weak |

---

### 4. Duration of Stay Trends (1985–2020)

| Period of Stay | Slope ($m$) | Intercept ($c$) | $R^2$ | Trend | Strength |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1–3 Nights** | +0.260 | 13.28 | 0.091 | Increase | Very Weak |
| **4–7 Nights** | **+0.505** | **17.13** | **0.506** | **Increase** | **Moderate** |
| **8–14 Nights** | +0.206 | 27.80 | 0.292 | Increase | Weak |
| **15–21 Nights** | -0.348 | 19.68 | 0.479 | Decrease | Moderate |
| **22–30 Nights** | -0.266 | 10.56 | 0.325 | Decrease | Weak |
| **31+ Nights** | -0.357 | 11.55 | 0.324 | Decrease | Weak |

---

### 5. Demographic & Occupational Shifts (1991–2020)

* **Gender**: Female tourist arrivals are increasing at **+0.341% per year** ($R^2 = 0.479$), while male tourists decrease proportionally[cite: 1].
* **Age**: Younger visitors (20–39 years) show a contracting trend, whereas older age groups (50–59 and 60+) exhibit consistent growth[cite: 1].
* **Occupation**: High expansion among gainfully employed visitors, led by **Professionals** (+0.942% per year, $R^2 = 0.711$)[cite: 1].

---

### 6. Source Region Dynamics (1993–2023)

| Region | Slope ($m$) | Intercept ($c$) | $R^2$ | Trend | Growth Volume |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Asia & Pacific** | **+22,373** | **4,917** | **0.377** | Increase | Highest |
| **Europe** | +16,248 | 128,368 | 0.341 | Increase | High |
| **Americas** | +2,792 | 1,841 | 0.462 | Increase | Moderate |
| **Middle East** | +2,390 | -6,712 | 0.369 | Increase | Moderate |
| **Africa** | +352 | -952 | 0.422 | Increase | Low |

---

## 📈 Time Series & SARIMA Model Development

### 1. Stationarity Testing (Augmented Dickey-Fuller Test)
Stationarity of the monthly arrival data (1971–2021) was evaluated using the Augmented Dickey-Fuller (ADF) test at $\alpha = 0.05$[cite: 1]:

* **Original Level Series**: Test Stat = $-2.43973$ ($p = 0.131$) $\rightarrow$ **Non-Stationary**[cite: 1].
* **First Non-Seasonal Differencing ($\Delta Y_t$, $d=1$)**: Test Stat = $-4.96779$ ($p < 0.001$) $\rightarrow$ **Stationary**[cite: 1].
* **First Seasonal Differencing ($\Delta_{12} Y_t$, $D=1, s=12$)**: Applied to remove 12-month seasonal persistence identified in the ACF plot[cite: 1].

---

### 2. Candidate Model Comparison

| Candidate Model | AIC | BIC | Out-of-Sample MAE | Out-of-Sample MAPE |
| :--- | :--- | :--- | :--- | :--- |
| **$\text{ARIMA}(0,1,0)(0,1,1)_{12}$** | 12,956.84 | 12,965.63 | 76,716.16 | 85.84% |
| **$\text{ARIMA}(0,1,0)(0,1,2)_{12}$** | **12,937.56** | **12,950.75** | **32,377.18** | **34.36%** |
| **$\text{ARIMA}(3,1,0)(1,1,2)_{12}$** | 12,892.98 | 12,923.75 | 32,348.65 | 34.13% |
| **$\text{ARIMA}(3,1,0)(0,1,2)_{12}$** | 12,891.07 | 12,917.44 | 33,105.91 | 35.07% |

> **Model Selection**: The **$\text{ARIMA}(0,1,0)(0,1,2)_{12}$** model was selected as optimal due to its parameter parsimony, high statistical significance across all estimated terms ($p < 0.001$), and strong out-of-sample forecasting capability ($MAPE = 34.36\%$)[cite: 1].

---

## 💬 Discussion & Methodological Limitations

1. **Impact of COVID-19 Pandemic & Easter Bombings**:
   * The April 2019 Easter bombings caused an immediate drop in arrivals due to security concerns[cite: 1].
   * The onset of COVID-19 in early 2020 resulted in global travel bans and airport closures from April 2020 to December 2020[cite: 1].
   * Estimating and imputing these missing values enabled time series continuity, but introduces a degree of uncertainty given the unprecedented nature of these exogenous shocks[cite: 1].

2. **Linear Trend Assumptions**:
   * Long-term trend models were strictly evaluated using linear specifications[cite: 1].
   * While linear models offer clear interpretations, they do not account for non-linear dynamics, higher-order polynomials, or complex economic cycles[cite: 1].

3. **Exogenous Factors in SARIMA**:
   * SARIMA selection relied purely on univariate statistical criteria (AIC, BIC, MAE, MAPE)[cite: 1].
   * Univariate models do not explicitly incorporate external economic drivers, exchange rates, or unexpected crisis events, which can affect long-term predictive accuracy during extreme structural disruptions[cite: 1].

---

## 🎯 Summary of Conclusions

* **Overall Growth**: Historical arrivals exhibit a moderate upward trajectory expanding by ~26,452 tourists annually[cite: 1].
* **Seasonal Peak**: Travel exhibits strong seasonality, peaking in December/January and dipping significantly in May/June[cite: 1].
* **Shift in Travel Behavior**: Demand is moving toward shorter stays (4–7 nights), increased visits to friends/relatives (VFR), an aging tourist demographic (50+ age group), and professional travelers[cite: 1].
* **Regional Drivers**: The Asia & Pacific region is leading overall post-2009 volume growth[cite: 1].
* **Forecast Trajectory**: Out-of-sample forecasting using the validated **$\text{ARIMA}(0,1,0)(0,1,2)_{12}$** model projects a steady, gradual recovery and increase in international visitor arrivals in subsequent years[cite: 1].

---

## 💡 Policy & Stakeholder Recommendations

1. **Off-Peak Marketing**: Implement targeted promotional campaigns in May and June to offset low-season drops[cite: 1].
2. **Demographic Alignment**: Tailor travel and wellness offerings to mature travelers (50+ years) and solo female travelers[cite: 1].
3. **Short-Stay Product Design**: Expand MICE and curated 4–7 day itineraries to match the shifting preference toward shorter trips[cite: 1].
4. **Market Expansion**: Concentrate promotional campaigns within high-growth Asia-Pacific source markets[cite: 1].

---
