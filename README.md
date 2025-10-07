# 🌦️ Power BI Weather Dashboard

An interactive **Power BI Dashboard** integrating **real-time** and **forecast weather data** from the **Weather API**, providing users with deep insights into climate conditions, air quality, and forecast trends across multiple cities.

---

## 📊 Overview

The **Power BI Weather Dashboard** visualizes live and forecasted weather parameters including:

* 🌡️ Temperature (°C & °F)
* 💧 Humidity
* 🌬️ Wind Speed
* 🌫️ Air Quality Index (AQI)
* 🌧️ Precipitation Probability
* 🌅 Sunrise & Sunset Timings

It allows users to **compare cities**, **analyze trends**, and **monitor environmental conditions** — all within a clean, dark-themed interface designed for modern data storytelling.

---

## ⚙️ Data Source and Preparation

### **Data Acquisition**

Data was fetched directly from the **Weather API** using Power BI’s **Get Data > Web** option.

**Steps:**

1. Queried the API endpoint using a valid API key to fetch JSON data.
2. Created separate queries for each city via the location parameter.
3. Appended all queries into a unified table `Current`.
4. Extracted forecast data from nested JSON into a new table `Forecast_Day`.
5. Cleaned and renamed columns for consistency.

### **Data Transformation (Power Query)**

* Enabled *“Use First Row as Headers.”*
* Expanded all nested JSON fields.
* Converted data types appropriately (e.g., Date/Time, Decimal).
* Removed unnecessary metadata columns.
* Standardized column names for clarity.

### **Relationships**

* **Location Table (City)** → One-to-Many → **Current & Forecast_Day Tables**
  Enables **cross-filtering** across visuals using city slicers.

---

## 🧮 DAX Measures

```DAX
Curr_Temp_C = SUM('Current'[current.temp_c]) & " °C"
Curr_Temp_F = SUM('Current'[current.temp_f]) & " °F"

Last_Update = "Last Updated, " &
FORMAT(FIRSTNONBLANK('Current'[current.last_updated], ""), "dd mmm")

For_Temp_C = AVERAGE(Forecast_Day[forecast.forecastday.day.avgtemp_c]) & " °C"
Avg_Humidity = AVERAGE('Current'[current.humidity])

Temp_Diff =
AVERAGE(Forecast_Day[forecast.forecastday.day.avgtemp_c]) -
SUM('Current'[current.temp_c])

AQI_Status =
SWITCH(TRUE(),
 [AQI] <= 50, "Good",
 [AQI] <= 100, "Moderate",
 [AQI] <= 150, "Unhealthy",
 [AQI] <= 200, "Very Unhealthy",
 "Hazardous"
)
```

---

## 📈 Key Visualizations

| **Section**                      | **Objective**                                 | **Visualization Type** | **Highlights**                                     |
| -------------------------------- | --------------------------------------------- | ---------------------- | -------------------------------------------------- |
| 🌤️ **Current Weather Overview** | Display real-time weather details             | Card visuals           | Dynamic temperature cards with gradient formatting |
| 🌡️ **Key Weather Parameters**   | Show humidity, wind, pressure, UV, visibility | Multi-row cards        | Uniform theme and rounded corners                  |
| 📅 **Forecast Trend (5 Days)**   | Display forecasted average temperatures       | Line Chart             | Smooth gradient line, tooltips with °C & °F        |
| 🌫️ **Air Quality Index**        | Visualize air quality & pollutants            | Gauge + Donut Charts   | Conditional colors (Green → Red)                   |
| 🌅 **Sunrise & Sunset**          | Display city-wise timings                     | Card visuals           | Formatted `hh:mm AM/PM` with icons                 |
| ☔ **Chance of Rain**             | Show precipitation probability                | Bar Chart              | Gradient bars (light → dark orange)                |
| 🌆 **Temp Comparison**           | Compare current vs forecast temps             | Clustered Column       | Dual bars with hover tooltips                      |
| 🏙️ **City Slicer**              | Filter data by city                           | Slicer                 | Enables cross-filtering for all visuals            |
| 🕒 **Last Updated**              | Show last API refresh time                    | Card visual            | Auto-refresh with each update                      |

---

## 🎨 Dashboard Design & Formatting

* **Theme:** Dark mode with orange and white highlights
* **Font:** Segoe UI (professional and clean)
* **Layout:**

  * Left: Current weather metrics
  * Center: Forecast and AQI visuals
  * Right: Rain chance, sunrise/sunset, timestamp
* **Conditional Formatting:** Applied to temperature, AQI, and precipitation
* **Icons:** Weather-related icons (☀️ 🌧️ 🌫️ 🌪️) for clarity

---

## 🧰 Tools & Technologies

| Tool                                | Purpose                                  |
| ----------------------------------- | ---------------------------------------- |
| **Power BI Desktop**                | Data modeling & visualization            |
| **Weather API (JSON)**              | Real-time & forecast weather data source |
| **Power Query Editor**              | Data cleaning & transformation           |
| **DAX (Data Analysis Expressions)** | Calculated measures and KPIs             |

---

## 🚀 Future Enhancements

1. ⚠️ **Weather Alerts** — Real-time notifications via Power Automate or email.
2. 📉 **Historical Weather Analysis** — Visualize long-term trends and anomalies.
3. 🛰️ **Satellite Imagery** — Integrate live cloud and heatmap visuals.
4. 🔮 **Predictive Analytics** — Forecast using machine learning models.
5. 📱 **Mobile-Optimized View** — Enhanced usability for Power BI Mobile.
6. 🌍 **Regional Comparison Mode** — Multi-city comparisons for better insights.

---

## 🧾 Summary

The **Power BI Weather Dashboard** demonstrates how to transform **API-driven data** into actionable insights.
It effectively combines **real-time monitoring**, **forecast analysis**, and **environmental visualization** — all within an elegant, interactive, and automated interface.

> 💡 *This project exemplifies end-to-end Power BI development — from API integration and data transformation to DAX modeling and dashboard design.*

---

## 📷 Preview (Optional)

> *(Insert screenshots or GIFs of your dashboard here — e.g., current weather cards, forecast trend chart, AQI gauge.)*

---



**⭐ If you like this project, consider giving it a star on GitHub!**
