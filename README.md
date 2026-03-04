# 🦟 Climate & Dengue Forecasting — São Paulo

Analysis of the relationship between climate variables (temperature and precipitation) and dengue cases in the city of São Paulo (2015–2025), with a Machine Learning-based predictive model.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mariananlemos/climate-dengue-forecasting-sp/blob/main/climate_dengue_forecasting_sp.ipynb)

---

## 📋 About the Project

This project investigates how temperature and precipitation influence dengue case dynamics in São Paulo. The full pipeline includes:

1. **Data collection** — weekly cases via InfoDengue API + climate data from IAG/USP
2. **Exploratory analysis** — time series, seasonality, and heatmaps
3. **Statistical correlation** — Spearman with temporal lag (0–3 months)
4. **Predictive model** — Random Forest with temporal validation (TimeSeriesSplit)
5. **Interactive dashboard** — Plotly with historical data, forecasts, correlation, and feature importance
6. **Risk map** — Folium heatmap showing vulnerability by district

## 🗂️ Structure

```
├── climate_dengue_forecasting_sp.ipynb   # Main notebook (full pipeline)
├── README.md
└── (generated after execution)
    ├── dengue_sp_2015_2025.csv           # Consolidated dataset
    ├── previsoes_6meses.csv              # 6-month forecast
    ├── modelo_dengue_sp.pkl              # Trained model (Random Forest)
    ├── dashboard_dengue_sp.html          # Interactive dashboard (Plotly)
    ├── mapa_dengue_sp.html               # Risk map (Folium)
    ├── sazonalidade.png                  # Seasonality chart
    ├── heatmap_ano_mes.png               # Year × month heatmap
    ├── correlacao_dengue.png             # Correlation chart
    ├── validacao_modelo.png              # Temporal validation (folds)
    └── importancia.png                   # Feature importance
```

## 🚀 Getting Started

### Google Colab (recommended)
Click the **Open In Colab** badge above and run all cells in order.

### Locally
```bash
pip install pandas numpy scipy matplotlib seaborn plotly folium scikit-learn joblib requests
jupyter notebook climate_dengue_forecasting_sp.ipynb
```

## 🔬 Methodology

| Step | Description |
|------|-------------|
| **Dengue data** | InfoDengue API — epidemiological weeks aggregated by month |
| **Climate data** | Monthly average temperature (IAG/USP, 2015–2021) + projection for 2022–2025 |
| **Precipitation** | IAG/USP climatological normals with stochastic variation |
| **Correlation** | Spearman (non-parametric) with lags from 0 to 3 months |
| **Model** | Random Forest (200 trees, max_depth=6) with lag and seasonality features |
| **Validation** | TimeSeriesSplit (4 folds) — respects temporal order |

## 📊 Key Visualizations

- **Time series** — Cases, temperature, and precipitation (2015–2025)
- **Seasonality** — Peaks in Jan–Apr correlated with heat and rainfall
- **Year × month heatmap** — Identifies outbreaks by period
- **Correlation by lag** — Temperature precedes cases by ~1 month
- **4-panel dashboard** — Historical + forecast + correlation + feature importance
- **Risk map** — Vulnerability by São Paulo district

## 📦 Dependencies

- Python 3.8+
- pandas, numpy, scipy
- matplotlib, seaborn, plotly
- folium
- scikit-learn
- joblib, requests

## 📝 Data Sources

- **Dengue cases (SP)**: [InfoDengue — Epidemiological Surveillance](https://info.dengue.mat.br/)
- **Average temperature (SP)**: [São Paulo City Hall / SMUL-Geoinfo](https://drive.prefeitura.sp.gov.br/cidade/secretarias/upload/chamadas/temp_mdia-precipitacao_1650654282.htm)
- **Meteorological data**: [BDMEP/INMET](https://bdmep.inmet.gov.br/)

## ⚠️ Limitations

- Temperature data for 2022–2025 are projections based on historical averages
- Precipitation uses climatological normals with simulated variation
- Correlation ≠ causation — climate creates favorable conditions for *Aedes aegypti*, but transmission also depends on active viral circulation and epidemiological surveillance

## 📄 License

MIT