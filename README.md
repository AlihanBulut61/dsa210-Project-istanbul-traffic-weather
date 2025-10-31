# DSA 210 Project Proposal — Weather, Holidays & Air Quality Effects on Istanbul Traffic Congestion

**Course:** DSA 210 (Fall 2025)  
**Student:** Alihan Bulut  
**Repository:** https://github.com/alihanbulut/dsa210-istanbul-traffic-weather

---

## 1) Motivation
Istanbul experiences chronic congestion that varies by hour, weekday, season and weather. This project aims to *quantify* how short‑term weather conditions (rain, temperature, wind), **public & school holidays**, and **air quality** relate to **daily traffic congestion levels**. Results can support better commute planning and policy decisions.

## 2) Research Questions / Hypotheses
- **RQ1.** Do precipitation and temperature significantly change the daily average congestion index?  
  **H1:** Mean congestion is higher on rainy days vs. non‑rainy days.
- **RQ2.** Are congestion levels lower on **official/school holidays** compared to comparable weekdays?  
  **H2:** Holiday indicators are associated with lower congestion.
- **RQ3.** Does air quality (PM2.5/PM10, AQI) co‑vary with congestion after controlling for weather?  
  **H3:** Higher AQI (worse air) correlates with higher congestion.

## 3) Data Sources (public) & Enrichment Plan
I will **combine at least two independent public datasets** (as required) to enrich the primary traffic series:

- **Primary (Traffic):**
  - *Istanbul Traffic Congestion Index* (historic daily values). Candidate sources:  
    - Istanbul Metropolitan Municipality (İBB) Open Data Portal/API.  
    - Public mirrors/datasets that track Istanbul congestion index historically (e.g., Kaggle/TomTom/TrafficIndex).

- **Enrichment A (Weather):**
  - Turkish State Meteorological Service (MGM) daily weather for Istanbul (precipitation, temperature, wind).

- **Enrichment B (Holidays/School Calendar):**
  - Turkey **public holidays** (iCal/CSV/API).  
  - Turkey **school holiday** calendars (Ministry of Education announcements or curated datasets).

- **Optional Enrichment C (Air Quality):**
  - Istanbul AQI / PM2.5 / PM10 series via WAQI (aqicn) API or İBB environmental monitoring feeds.

All sources will be properly cited in the final repo and report. Any scraping will observe robots.txt / Terms.

## 4) Data Collection Plan
1. **Traffic**
   - If an official İBB endpoint is available, request JSON/CSV and store to `data/raw/traffic/*.csv`.  
   - If a community dataset is used (e.g., Kaggle Istanbul Traffic Index), download the CSV and document its provenance and schema.
2. **Weather**
   - Use MGM’s public data pages or a documented API endpoint to collect **daily** precipitation (mm), max/min temperature (°C), and wind speed. Save to `data/raw/weather/*.csv`.
3. **Holidays & School Calendar**
   - Import a Turkey public‑holiday calendar (CSV/ICS/API) and convert to a daily boolean indicator. For school holidays, ingest the academic calendar to mark term/break days. Save to `data/raw/calendar/*.csv`.
4. **Air Quality (optional)**
   - Query WAQI/İBB environmental monitoring for daily AQI/PM2.5/PM10; aggregate to daily averages. Save to `data/raw/air/*.csv`.
5. **Versioning**
   - Keep all raw files immutable under `data/raw/`. Create cleaned, merged, and feature‑engineered tables under `data/processed/` with scripts in `src/`.
6. **Reproducibility**
   - Provide `src/collect_*.py` scripts with CLI args and a `make all` or `python -m src.pipeline` entry point. Pin dependencies in `requirements.txt`.

## 5) Planned Methods (EDA & Inference)
- **EDA:** seasonal/hourly/daily profiles; heatmaps by weekday×hour; distributions; missingness checks.
- **Hypothesis tests:** two‑sample tests (rain vs no‑rain), correlation analysis, and linear models with holiday/weather dummies.
- **Time‑series controls:** multiple regression on daily congestion with fixed effects for weekday/month, weather, holiday, and AQI controls. Robust SEs.
- **Visualization:** clear, labeled charts; confidence intervals; reproducible notebooks.
- **Ethics:** only aggregated, non‑personal, open data; no PII.


## 7) Risks & Mitigations
- **Data availability gaps:** If an official traffic history is limited, fall back to reputable mirrors (e.g., Kaggle/TomTom indices) with clear caveats.
- **API rate limits / access:** Cache raw pulls to disk; document schemas; keep a small sample CSV in the repo to allow quick tests.
- **Schema changes:** Use validation checks in the ETL to fail fast when columns drift.

## 8) Repository Structure (initial)
```
.
├── README.md
├── requirements.txt
├── src/
│   ├── collect_traffic.py           # placeholder
│   ├── collect_weather.py           # placeholder
│   ├── collect_holidays.py          # placeholder
│   ├── collect_air_quality.py       # optional
│   ├── merge_build_features.py      # placeholder
│   └── utils.py                     # placeholder
├── notebooks/
│   └── 00_eda.ipynb                 # to be added
└── data/
    ├── raw/                         # do not commit large files
    └── processed/
```


---

