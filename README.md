# 🌤️ Weather Forecast & Air Quality Dashboard — Power BI

![Dashboard Preview](dashboard_screenshot.png)

## 📌 Overview

An interactive **Weather Forecast & Air Quality Dashboard** built in Power BI, powered by live data from **WeatherAPI.com**. The dashboard provides real-time weather conditions, 7-day forecasts, and detailed air quality metrics for **6 cities across India**.

---

## 🚀 Features

| Feature | Description |
|---|---|
| 🌡️ **Current Weather** | Live temperature, weather condition & city info |
| 📅 **7-Day Forecast** | Daily temperature trend with interactive line chart |
| 💨 **Weather KPIs** | Visibility, Humidity, Wind Speed, UV Index, Pressure, Precipitation |
| 🌅 **Sunrise & Sunset** | Dynamic daily sunrise/sunset timings |
| 🌧️ **Chance of Rain** | Daily rain probability (stacked bar chart) |
| 🫁 **Air Quality Index** | PM2.5, PM10, CO, NO2, SO2, O3 with color-coded indicators |
| ✅ **AQI Status** | Good / Moderate / Unhealthy — dynamic DAX measure |
| 💬 **AQI Suggestion** | Real-time health recommendations based on AQI level |
| 🎨 **Dynamic Colors** | Color measures for CO, NO2, O3, PM10 indicators |

---

## 🏙️ Cities Covered

- Ajmer
- Rampur  
- Moradabad
- Meerut
- *(+ 2 more cities)*

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard design & visualization |
| **WeatherAPI.com** | Live weather & air quality data source |
| **Power Query** | Data transformation & cleaning |
| **DAX** | Custom measures, KPIs, color formatting |

---

## 📊 DAX Measures Used

```dax
-- Current Temperature
Curr_Temp_C = SELECTEDVALUE('Current'[current.temp_c])

-- Forecast Temperature
For_Temp_C = SELECTEDVALUE('Forecast'[forecast.forecastday.day.avgtemp_c])

-- AQI Status
AQI_Status =
VAR AQI = SELECTEDVALUE('Current'[current.air_quality.pm10])
RETURN
    SWITCH(
        TRUE(),
        AQI <= 50,  "Good",
        AQI <= 100, "Moderate",
        AQI <= 150, "Unhealthy for Sensitive Groups",
        AQI <= 200, "Unhealthy",
        AQI <= 300, "Very Unhealthy",
        "Hazardous"
    )

-- CO Suggestion
CO Suggestion =
VAR CO = SELECTEDVALUE('Current'[current.air_quality.co])
RETURN
    SWITCH(
        TRUE(),
        CO <= 50,  "Air is clean and healthy",
        CO <= 100, "Acceptable air quality, stay active",
        CO <= 150, "Sensitive groups should reduce outdoor time",
        CO <= 200, "Limit prolonged outdoor exertion",
        CO <= 300, "Avoid outdoor activity if possible",
        "Stay indoors, wear mask if outside"
    )

-- Dynamic Color Measures (CO, NO2, O3, PM10)
CO Color =
VAR val = SELECTEDVALUE('Current'[current.air_quality.co])
RETURN
    SWITCH(TRUE(),
        val <= 50,  "#2ECC71",
        val <= 100, "#F1C40F",
        val <= 150, "#E67E22",
        "#E74C3C"
    )
```

---

## 🎨 Dashboard Design

- **Dark glassmorphism UI** — modern weather app aesthetic
- **Orange accent theme** — warm, energetic color palette  
- **Custom weather icons** — Visibility, Humidity, Wind, UV, Pressure, Rain
- **Donut chart** for AQI with dynamic color
- **Interactive slicers** — City selector + Day selector
- **Page size:** 1280 × 720 (HD)

---

## 📁 Project Structure

```
weather-forecast-powerbi/
│
├── Weather_Forecast_Dashboard.pbix   # Main Power BI file
├── dashboard_screenshot.png          # Dashboard preview
└── README.md                         # Project documentation
```

---

## 🔧 How to Use

1. Download `Weather_Forecast_Dashboard.pbix`
2. Open in **Power BI Desktop** (free download from Microsoft)
3. Go to `Home → Refresh` to load current weather data
4. Use **city slicer** to switch between cities
5. Use **day slicer** to explore 7-day forecast

> ⚠️ **Note:** You need a free API key from [WeatherAPI.com](https://www.weatherapi.com) to refresh live data. Add your key in `Transform Data → Data Source Settings`.

---

## 📈 Skills Demonstrated

- ✅ REST API integration in Power BI
- ✅ Power Query data transformation
- ✅ Advanced DAX measures (SWITCH, SELECTEDVALUE, VAR)
- ✅ Conditional color formatting via DAX
- ✅ Interactive dashboard design
- ✅ KPI cards, line charts, donut charts, bar charts
- ✅ Custom theme & glassmorphism UI design

---

## 👤 Author

**Yash Vardhan**  
MCA Student | Chaudhary Charan Singh University  
Aspiring Data Analyst

---

## 📬 Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com)

---

⭐ **If you found this helpful, please star this repository!**

