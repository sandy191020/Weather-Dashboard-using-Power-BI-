# 🌦️ Power BI Weather Report Dashboard

## 🎯 Objective
To create an interactive **Power BI dashboard** that shows real-time and forecast weather data for 6 cities using the Weather API.

---

## ⚡ Steps Followed
1. Fetched data from **Weather API** using **Get Data > Web**.  
2. Created new queries for each city by changing the location parameter.  
3. Merged queries into a consolidated **Current** table.  
4. Cleaned and transformed data (renamed columns like `day` → `forecast_date`).  
5. Built **measures** for temperature, location, and KPIs.  
6. Defined **relationships** between Location and other tables.  
7. Designed visuals (cards, charts, pie charts, slicer for cities, multi-row cards).  
8. Styled the report with a background and formatting for a clean look.  

---

## 📊 Features
- Real-time weather metrics (°C and °F).  
- Average forecast temperature for selected cities.  
- City-wise comparison via slicer.  
- Last updated timestamp.  
- Interactive charts, cards, and KPIs.  

---

## 🧮 DAX Measures
```DAX
Curr_Temp_C = SUM('Current'[current.temp_c]) & " °C"

Curr_Temp_F = SUM('Current'[current.temp_f]) & " °F"

Last_Update = "Last Updated, " & FORMAT(FIRSTNONBLANK('Current'[current.last_updated], ""), "dd mmm")

For_Temp_C = AVERAGE(Forcast_Day[forecast.forecastday.day.avgtemp_c]) & " °C"
