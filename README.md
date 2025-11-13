<!-- PROJECT TITLE -->
<h1 align="center" style="font-weight:700; font-size:38px;">
  Meta Ads Performance Analysis Dashboard
</h1>

<!-- SUBTITLE -->
<p align="center" style="font-size:16px; max-width:750px; margin:auto;">
A complete marketing intelligence system built using 
<b>Power BI</b>, <b>DAX</b>, and a refined <b>data modelling architecture</b>.  
This project delivers deep insights into Meta ads performance, budget efficiency, audience behaviour,  
and ROI through a clean, interactive dashboard.
</p>

<br>

<!-- BADGES / TECH STACK -->
<p align="center">

  <!-- Power BI -->
  <img src="https://img.shields.io/badge/Power%20BI-Data%20Visualization-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=black" />

  <!-- DAX -->
  <img src="https://img.shields.io/badge/DAX-Analytics-blue?style=for-the-badge" />

  <!-- Python -->
  <img src="https://img.shields.io/badge/Python-Data%20Cleaning-3776AB?style=for-the-badge&logo=python&logoColor=white" />

  <!-- SQL -->
  <img src="https://img.shields.io/badge/SQL-Data%20Processing-005C84?style=for-the-badge&logo=postgresql&logoColor=white" />

  <!-- GitHub -->
  <img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white" />

</p>

<br>

<hr style="margin:40px 0;">

<!-- OVERVIEW SECTION -->
<h2>
  <img src="https://img.icons8.com/ios-filled/28/000000/overview-pages-3.png" 
       style="vertical-align:middle; margin-right:10px;">
  Project Overview
</h2>

<p>
This project analyzes Meta Ads (Facebook & Instagram) to evaluate campaign performance, optimize spend, 
and uncover the behavioural patterns of different audiences.  
Using <strong>Power BI</strong> and <strong>DAX</strong>, the dashboard transforms raw datasets into business-ready insights for:
</p>

<ul>
  <li>Campaign performance evaluation</li>
  <li>Budget efficiency & ROI measurement</li>
  <li>Audience behaviour and demographics</li>
  <li>Time-based engagement trends</li>
  <li>Ad format effectiveness</li>
</ul>

<p>
The final dashboard is designed with a corporate analytical style suitable for presentations, decision-making,  
and portfolio demonstration.
</p>

<hr style="margin:40px 0;">

<!-- FILES SECTION -->
<h2>
  <img src="https://img.icons8.com/ios-glyphs/28/000000/documents.png" 
       style="vertical-align:middle; margin-right:10px;">
  Repository Contents
</h2>

<table style="width:100%; border-collapse:collapse;">
  <tr style="background:#f2f2f2; font-weight:600;">
    <td style="padding:10px; border:1px solid #ddd;">File</td>
    <td style="padding:10px; border:1px solid #ddd;">Description</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">ads.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">Ad metadata (platform, ad type, demographic targeting)</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">ad_events.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">User activity events (impressions, clicks, shares, purchases)</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">campaigns.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">Campaign-level data including budgets</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">users.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">User demographic & location information</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">Dashboard (.pbix)</td>
    <td style="padding:10px; border:1px solid #ddd;">Final interactive Power BI dashboard</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">DAX Documentation</td>
    <td style="padding:10px; border:1px solid #ddd;">All measures, titles, tables and calculated columns</td>
  </tr>
</table>

<hr style="margin:40px 0;">

<!-- DASHBOARD ARCHITECTURE -->
<h2>
  <img src="https://img.icons8.com/ios/28/000000/combo-chart--v1.png" 
       style="vertical-align:middle; margin-right:10px;">
  Dashboard Architecture
</h2>

<p>The dashboard is divided into five analytical pages:</p>

<h3>1. Executive Overview</h3>
<ul>
  <li>Key campaign KPIs</li>
  <li>Platform distribution</li>
  <li>Top performing campaigns</li>
  <li>Monthly performance trendline</li>
  <li>Dynamic metrics selector</li>
</ul>

<h3>2. Audience Insights</h3>
<ul>
  <li>Gender, age, and country-based performance</li>
  <li>Engagement matrices</li>
  <li>Audience behaviour summary</li>
</ul>

<h3>3. ROI & Budget Efficiency</h3>
<ul>
  <li>CPA, CPC, CPE metrics</li>
  <li>ROI calculations</li>
  <li>Waterfall: Budget → Spend → ROI</li>
  <li>Cost-to-conversion scatter analysis</li>
</ul>

<h3>4. Time & Trend Analysis</h3>
<ul>
  <li>Hourly behaviour visualization</li>
  <li>Weekly performance by ad type</li>
  <li>Monthly trends</li>
  <li>Calendar distribution heatmap</li>
</ul>

<h3>5. Ad Type & Campaign Deep Dive</h3>
<ul>
  <li>Ad type cross-platform comparison</li>
  <li>Campaign-level full funnel</li>
  <li>Detailed performance tables</li>
</ul>

<hr style="margin:40px 0;">

<!-- DATA MODEL -->
<h2>
  <img src="https://img.icons8.com/external-flat-icons-inmotus-design/28/000000/external-data-analytics-analytics-flat-icons-inmotus-design.png"
       style="vertical-align:middle; margin-right:10px;">
  Data Model
</h2>

<pre style="background:#f8f8f8; padding:20px; border-radius:6px; font-size:14px;">
campaigns ───┬── ads ─── ad_events
             └── users
</pre>

<p>
This star-schema model ensures clean filtering, efficient querying, and accurate DAX behaviour.
</p>

<hr style="margin:40px 0;">

<!-- DAX SECTION -->
<h2>
  <img src="https://img.icons8.com/ios/28/000000/formula-fx.png" 
       style="vertical-align:middle; margin-right:10px;">
  Key DAX Measures
</h2>

<h3>Performance Measures</h3>
<pre style="background:#f8f8f8; padding:20px; border-radius:6px;">
Impressions = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Impression"))
Clicks = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Click"))
Engagement = [Clicks] + [Shares] + [Comments]
CTR = DIVIDE([Clicks], [Impressions], 0)
Engagement Rate = DIVIDE([Engagement], [Impressions], 0)
Conversion Rate = DIVIDE([Purchases], [Clicks], 0)
</pre>

<h3>Budget & ROI Measures</h3>
<pre style="background:#f8f8f8; padding:20px; border-radius:6px;">
Total Budget = SUM(campaigns[total_budget])
CPA = DIVIDE([Total Budget], [Purchases], 0)
CPC = DIVIDE([Total Budget], [Clicks], 0)
CPE = DIVIDE([Total Budget], [Engagement], 0)
Return of Investment (ROI) = [Purchases] * 1000
</pre>

<h3>Custom Tables</h3>
<pre style="background:#f8f8f8; padding:20px; border-radius:6px;">
Budget Flow = 
UNION(
  ROW("Stage", "Total Budget", "Value", [Total Budget]),
  ROW("Stage", "Spent Budget", "Value", [Spend Budget]),
  ROW("Stage", "ROI Value", "Value", [Return of Investment (ROI)])
)
</pre>

<hr style="margin:40px 0;">

<!-- HOW TO USE -->
<h2>
  <img src="https://img.icons8.com/ios-glyphs/28/000000/download--v1.png" 
       style="vertical-align:middle; margin-right:10px;">
  How to Use This Project
</h2>

<ol>
  <li>Clone the repository:</li>
<pre style="background:#f8f8f8; padding:20px; border-radius:6px;">git clone https://github.com/Rysin09/Meta-Ads-Performance-Analysis</pre>

  <li>Open the Power BI (.pbix) file</li>
  <li>Confirm data model relationships</li>
  <li>Review DAX expressions</li>
  <li>Explore all 5 dashboard pages</li>
</ol>

<hr style="margin:40px 0;">

<!-- INSIGHTS -->
<h2>
  <img src="https://img.icons8.com/ios-filled/28/000000/insight.png" 
       style="vertical-align:middle; margin-right:10px;">
  Analytical Insights Delivered
</h2>

<ul>
  <li>High-performing campaigns and audiences</li>
  <li>Platform-level ROI performance</li>
  <li>Budget effectiveness and spend optimization</li>
  <li>Engagement patterns across time</li>
  <li>Ad type performance comparison</li>
  <li>Full-funnel performance visualization</li>
</ul>

<hr style="margin:40px 0;">

<!-- AUTHOR -->
<h2>
  <img src="https://img.icons8.com/ios-glyphs/26/000000/user-male-circle.png" 
       style="vertical-align:middle; margin-right:10px;">
  Author
</h2>

<p>
This project was designed as a professional demonstration of data analytics, BI development, and applied marketing intelligence.  
It reflects expertise in Power BI, DAX modeling, data transformation, and storytelling with data.  
</p>

<h2 style="font-weight:600;">8. Author</h2>
<p>
Designed and developed as a portfolio project demonstrating applied analytics, 
data modeling expertise, and real-world marketing intelligence capabilities.
</p>

