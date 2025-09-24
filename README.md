# Weather-Dashboard-using-Power-BI-
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Power BI Weather Report — README</title>
  <style>
    :root{--bg:#0f1724;--card:#111827;--muted:#94a3b8;--accent:#7dd3fc;--glass:rgba(255,255,255,0.03)}
    *{box-sizing:border-box}
    body{font-family:Inter,Segoe UI,Roboto,system-ui,Arial;background:linear-gradient(180deg,#071026 0%, #081226 100%);color:#e6eef6;margin:0;padding:28px}
    .wrap{max-width:900px;margin:0 auto}
    header{display:flex;align-items:center;gap:18px}
    .logo{width:64px;height:64px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#60a5fa);display:flex;align-items:center;justify-content:center;font-weight:700;color:#042134}
    h1{margin:0;font-size:22px}
    p.lead{color:var(--muted);margin-top:6px}
    .card{background:var(--card);padding:18px;border-radius:12px;margin-top:20px;box-shadow:0 6px 18px rgba(2,6,23,0.7);}
    ol{margin:8px 0 0 18px;color:var(--muted)}
    dt{font-weight:600;margin-top:12px}
    pre{background:var(--glass);padding:12px;border-radius:8px;overflow:auto;color:#dbeafe}
    code{font-family:monospace;font-size:13px}
    .kpi{display:flex;gap:10px;flex-wrap:wrap;margin-top:12px}
    .pill{background:rgba(125,211,252,0.08);padding:6px 10px;border-radius:999px;color:var(--accent);font-weight:600}
    .screenshot{margin-top:14px;border-radius:8px;overflow:hidden;border:1px solid rgba(255,255,255,0.03);}
    .btn{display:inline-block;padding:8px 12px;border-radius:8px;background:#0ea5a1;color:#042134;font-weight:700;text-decoration:none;margin-top:12px}
    footer{margin-top:22px;color:var(--muted);font-size:13px}
    @media (max-width:640px){body{padding:14px}.wrap{padding:6px}}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="logo">WB</div>
      <div>
        <h1>Power BI Weather Report Dashboard</h1>
        <p class="lead">A simple, interactive dashboard showing current & forecast weather for multiple cities using Weather API.</p>
      </div>
    </header>

    <section class="card">
      <h2 style="margin:0;font-size:16px">🎯 Objective</h2>
      <p style="color:var(--muted);margin-top:8px">Visualize real-time and forecast weather for 6 cities in Power BI — quick insights, comparisons, and trend overview.</p>

      <dl style="margin-top:12px;color:var(--muted)">
        <dt>Key steps</dt>
        <dd>
          <ol>
            <li>Get Weather API &rarr; Power BI: <code>Get Data &gt; Web</code>.</li>
            <li>Create separate queries for each city (advanced query → change location param).</li>
            <li>Clean & transform: rename/remove columns (e.g. rename <code>day</code> to <code>forecast_date</code>).</li>
            <li>Merge tables to form a consolidated <code>Current</code> (and forecast) table.</li>
            <li>Create relationships between <code>Location</code> and other tables.</li>
            <li>Build visuals: cards, charts, slicer for city selection, multi-row cards, pie charts.</li>
            <li>Final styling: background, layout, and formatting of cards/labels.</li>
          </ol>
        </dd>

        <dt>Features</dt>
        <dd>
          <div class="kpi">
            <span class="pill">6 City Comparison</span>
            <span class="pill">Real-time Current & Forecast</span>
            <span class="pill">°C & °F</span>
            <span class="pill">Last Updated Timestamp</span>
            <span class="pill">Interactive Slicer</span>
          </div>
        </dd>
      </dl>
    </section>

    <section class="card">
      <h2 style="margin:0;font-size:16px">🧮 DAX Measures (examples)</h2>
      <p style="color:var(--muted);margin-top:8px">Copy these into Power BI's measure editor and adjust table/column names if needed.</p>
      <pre><code>Curr_Temp_C = SUM('Current'[current.temp_c]) & " °C"

Curr_Temp_F = SUM('Current'[current.temp_f]) & " °F"

Last_Update = "Last Updated, " & FORMAT(FIRSTNONBLANK('Current'[current.last_updated], ""), "dd mmm")

For_Temp_C = AVERAGE(Forcast_Day[forecast.forecastday.day.avgtemp_c]) & " °C"</code></pre>
    </section>

    <section class="card">
      <h2 style="margin:0;font-size:16px">📁 How to use / Deploy</h2>
      <ol style="color:var(--muted)">
        <li>Clone the repo and open the <code>.pbix</code> in Power BI Desktop.</li>
        <li>Update the Weather API key in your queries (if stored as a parameter or URL).</li>
        <li>Refresh the dataset to fetch the latest weather for the 6 cities.</li>
        <li>Use the location slicer to switch between cities or compare multiple at once.</li>
      </ol>

      <div class="screenshot">
        <img src="" alt="Insert dashboard screenshot here" style="display:block;width:100%;height:240px;object-fit:cover;background:linear-gradient(90deg,#0b1220,#082133);">
      </div>
      <a class="btn" href="#">Download .pbix</a>
    </section>

    <section class="card">
      <h2 style="margin:0;font-size:16px">ℹ️ Notes & Tips</h2>
      <ul style="color:var(--muted);margin-top:8px">
        <li>Prefer parameterizing the city name inside Power Query so you can reuse the same query for all cities.</li>
        <li>Use scheduled refresh in the Power BI Service if you publish and need automated updates.</li>
        <li>Keep API requests within rate limits — cache when possible or reduce refresh frequency.</li>
      </ul>
    </section>

    <footer>
      <div style="display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap">
        <div>Built by <strong>Sandeep Singh</strong> — B.E CSE-DS</div>
        <div style="color:var(--muted)">Made with Power BI • Weather API</div>
      </div>
    </footer>
  </div>
</body>
</html>
