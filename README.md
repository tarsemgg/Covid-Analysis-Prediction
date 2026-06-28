# 🦠 COVID-19 Analysis & Prediction with Python

> Exploratory data analysis, interactive visualizations, and a 7-day forecast of global COVID-19 confirmed cases using Facebook Prophet.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](YOUR_COLAB_LINK_HERE)
![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Plotly](https://img.shields.io/badge/Plotly-Interactive%20Viz-blueviolet)
![Prophet](https://img.shields.io/badge/Prophet-Time%20Series-orange)

---

## 📌 Problem Statement

Given real-world COVID-19 patient data, the goal is to:
- **Visualize** the global impact of COVID-19 across countries and time
- **Analyze** trends in infection, death, and recovery rates
- **Predict** the number of confirmed cases **7 days into the future** using time-series forecasting

---

## 📂 Dataset

| File | Description |
|------|-------------|
| `covid_19_clean_complete.csv` | Global daily COVID-19 stats — Confirmed, Deaths, Recovered, Active counts by Country/Region |

**Source:** [Kaggle – COVID-19 Clean Complete Dataset](https://www.kaggle.com/datasets/imdevskp/corona-virus-report)

**Key columns:** `Date`, `Country/Region`, `Province/State`, `Lat`, `Long`, `Confirmed`, `Deaths`, `Recovered`, `Active`

---

## 🔧 Tech Stack

| Library | Purpose |
|--------|---------|
| `Pandas` | Data loading, cleaning, and aggregation |
| `NumPy` | Numerical operations |
| `Plotly Express` | Interactive charts and choropleth maps |
| `Plotly Graph Objects` | Custom forecast visualization with confidence bands |
| `Geopy` | Reverse geocoding to fill missing Province/State values |
| `Facebook Prophet` | Time-series forecasting (7-day prediction) |
| `Matplotlib` | Supporting plots |

---

## 🔍 Project Workflow

### 1. 📥 Data Loading & Cleaning
- Loaded global COVID-19 data using Pandas
- Detected **34,404 null values** in the `Province/State` column
- Used **Geopy's Nominatim** with reverse geocoding (lat/lon → state name) to intelligently fill those nulls — a more sophisticated approach than simply dropping or imputing with a constant
- Fell back to `Country/Region` for any coordinates that geocoding couldn't resolve
- Fixed `Date` column dtype from string → `datetime`

### 2. 📊 Exploratory Data Analysis & Visualization

| Visualization | Insight |
|--------------|---------|
| Line chart — Confirmed over time | Tracked exponential growth globally |
| Multi-line chart — Confirmed / Deaths / Recovered / Active | Compared all 4 metrics on a single timeline |
| Donut pie chart — Global distribution | Showed the proportion of confirmed, deaths, recovered, active cases |
| Animated choropleth map | Visualized the **spread of COVID-19 across countries over time** (plays like a video) |
| Scatter plot — Deaths vs Confirmed | Revealed **USA, Brazil & India** as the top 3 countries with the highest confirmed-to-death ratio, with the US at the top |
| Box plot — Monthly case distribution | Made it **crystal clear that July 2020 saw a massive surge** in cases |

### 3. 🔮 Time-Series Forecasting with Facebook Prophet
- Aggregated daily global confirmed cases
- Trained a **Prophet model** on historical data
- Generated a **7-day future forecast**
- Plotted trend components (overall trend + weekly + yearly seasonality)
- Built a custom **Plotly interactive forecast chart** showing:
  - Actual historical cases (blue)
  - Predicted values (orange)
  - Upper & lower confidence bands (shaded gray area)

---

## 📈 Key Findings

- 🌍 **Global spread** was clearly visualized through the animated choropleth — COVID spread from Asia outward rapidly in early 2020
- 🇺🇸 **USA, Brazil, and India** led in confirmed-to-death ratios, with the US at the top
- 📅 **July 2020** was the peak month for daily case surges globally
- 📉 The Prophet model successfully captured the **upward trend and weekly seasonality**, producing a reliable short-term forecast with confidence intervals

---

## 🚀 How to Run

1. Open the notebook in **Google Colab** using the badge above
2. Upload the dataset file (`covid_19_clean_complete.csv`) to your Colab session
3. Run all cells top to bottom (`Runtime → Run All`)

> ⚠️ The geocoding step (filling null Province/State values) makes real API calls and may take a few minutes depending on the number of unique coordinates.

---

## 📁 Repository Structure

```
covid-analysis-prediction/
│
├── Covid_Analysis.ipynb     # Main notebook
├── README.md                # Project documentation
└── data/
    └── covid_19_clean_complete.csv   # Dataset (download from Kaggle)
```

---

## 🧠 What I Learned

- How to handle **large-scale missing data** using geospatial reverse geocoding — a creative alternative to standard imputation
- Building **interactive, animated visualizations** with Plotly (choropleth maps, scatter plots, box plots)
- Applying **Facebook Prophet** for time-series forecasting with minimal setup
- Combining Prophet forecasts with **Plotly Graph Objects** for polished, presentation-ready prediction charts

---

## 🙋‍♂️ Author

Tarsem Kumar
- 🔗 [LinkedIn](https://linkedin.com/in/tarsemkumar)
- 🐙 [GitHub](https://github.com/tarsemgg)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
