# Istanbul Traffic Congestion, Weather, Holidays and Air Quality

## Overview of the Project  
This project investigates the relationship between **Istanbul’s daily traffic congestion** and several external factors such as **weather conditions, public & school holidays, and air quality levels**.  
The objective is to analyze how these variables influence traffic intensity and to develop statistical and predictive models to better understand and forecast congestion patterns.

---

## Motivation  
Istanbul is one of the most congested cities in the world, and its traffic varies drastically with season, weekday, and even weather changes.  
Understanding how **rain, temperature, wind**, and **holidays** impact congestion can help improve urban mobility planning and reduce travel delays.  


---

## Objectives  
- Analyze how different weather patterns influence traffic congestion levels in Istanbul.  
- Examine how public and school holidays affect average congestion.  
- Study whether air quality indicators (PM2.5, PM10, AQI) correlate with traffic intensity.  
- Build regression and time-series models to predict daily congestion levels.  

---

## Information Collection  
The project will integrate **multiple open datasets** related to traffic, weather, holidays, and air quality.  
Data will be collected programmatically (via APIs) or from official CSV sources, cleaned, merged, and analyzed.  

| Variable | Description | Source |
|-----------|--------------|---------|
| `date` | Observation date | Common key for merging |
| `congestion_index` | Daily average congestion (%) | İstanbul Metropolitan Municipality (İBB) Open Data Portal |
| `temperature` | Mean daily temperature (°C) | Turkish State Meteorological Service (MGM) |
| `precipitation` | Daily total rainfall (mm) | MGM or open-weather API |
| `wind_speed` | Daily mean wind speed (m/s) | MGM |
| `is_public_holiday` | Indicator of public holiday | Turkey official holiday calendar (Gov API / CSV) |
| `is_school_holiday` | Indicator of school closure periods | Ministry of Education academic calendar |
| `aqi`, `pm25`, `pm10` | Air quality metrics | İBB or WAQI (aqicn.org) API |

---

## Data Sources  
- **Traffic Data:** [İBB Open Data Portal](https://data.ibb.gov.tr) — “Traffic Congestion Index” dataset.  
- **Weather Data:** [Meteoroloji Genel Müdürlüğü](https://www.mgm.gov.tr/) or Open-Meteo API.  
- **Holiday Data:** [Gov.tr official holiday API](https://www.resmigazete.gov.tr/) and [Nager.Date API](https://date.nager.at/).  
- **Air Quality Data (optional):** [WAQI](https://aqicn.org/api/) or İBB environmental monitoring feeds.  

All datasets will be properly cited in the final report and limited to open, non-personal data.

---

## Approach  

1. **Data Collection:**  
   - Download or request daily data from all relevant APIs and official datasets.  
   - Store raw files in `data/raw/` and create cleaned, merged versions in `data/processed/`.  

2. **Exploratory Data Analysis (EDA):**  
   - Visualize congestion by weekday, month, and weather condition.  
   - Compute descriptive statistics and correlations between features.  

3. **Hypothesis Testing:**  
   - Compare average congestion on rainy vs. dry days.  
   - Compare average congestion on holidays vs. regular weekdays.  
   - Test correlations between AQI and congestion.  

4. **Modeling (Planned):**  
   - Multiple Linear Regression using weather and holiday dummy variables.  
   - Time-series regression with weekday and monthly fixed effects.  
   - Evaluate using RMSE, R², and residual diagnostics.  

---

## Anticipation  
Expected outcome: identify the strongest external factors influencing Istanbul’s congestion and produce interpretable models that can forecast daily congestion given weather and holiday information.  
Results will help urban authorities and commuters plan around predictable traffic fluctuations.

---

## Types of Analysis to Be Performed  

- **Univariate Analysis:**  
  - Distribution of daily congestion, temperature, AQI, and rainfall.  
- **Bivariate Analysis:**  
  - Correlation between congestion and weather/holiday indicators.  
- **Regression Analysis:**  
  - Linear and multiple regression models to test hypotheses.  
- **Time Series Analysis:**  
  - Trend and seasonality checks; weekday and monthly effects.  

---

## Analysis Summary & Expected Results  

| Factor | Expected Relationship | Hypothesis |
|---------|----------------------|-------------|
| Rain (mm) | Positive correlation | Rain increases congestion |
| Temperature (°C) | Moderate positive | Warm days slightly increase traffic |
| Public Holiday | Negative effect | Holidays reduce congestion |
| School Holiday | Negative effect | Less morning traffic |
| AQI (Air Quality Index) | Positive correlation | Poor air quality coincides with high traffic |

> **Comment:**  
> The analysis will aim to confirm these expectations through hypothesis testing and model evaluation once data is collected.

---

## Visual Insights (Planned)  
- **Heatmaps:** Congestion by weekday × hour.  
- **Scatterplots:** Congestion vs. temperature, rainfall, and AQI.  
- **Boxplots:** Comparing congestion on holidays vs. weekdays.  
- **Regression Fit Lines:** Visualizing model predictions and residuals.

---

## Conclusion  
This project will quantify how environmental and temporal variables affect Istanbul’s daily traffic congestion.   
- A clear research question and motivation,  
- Multiple open data sources, and  
- A concrete data collection and analysis plan.

---

## Limitations & Future Work  
- **Data Gaps:** Weather or AQI data might have missing days.  
- **Granularity:** Daily averages may hide short-term traffic variations.  
- **Future Work:** Include hourly traffic feeds, integrate mobility data (Google Maps, TomTom), and test nonlinear models (e.g., Random Forests, LSTM).
