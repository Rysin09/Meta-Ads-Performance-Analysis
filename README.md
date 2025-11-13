<!-- ========================== TITLE =============================== -->
<h1 align="center" style="font-size:38px; font-weight:700; margin-bottom:10px;">
  Meta Ads Performance Analysis Dashboard
</h1>

<p align="center" style="font-size:16px; max-width:780px; margin:auto;">
  A comprehensive marketing intelligence and data engineering project integrating 
  <strong>Azure Data Pipelines</strong>, <strong>Power BI</strong>, <strong>DAX</strong>, and a refined 
  <strong>star-schema data model</strong>.  
  This solution transforms raw Meta Ads datasets into actionable insights on campaign performance, 
  audience behaviour, spending efficiency, and ROI — designed for real business decision-making.
</p>

<br><br>

<!-- ======================= TECH STACK BADGES ======================= -->
<h2 style="font-weight:600;">Tech Stack Used</h2>

<p style="margin-bottom:25px;">

  <!-- Power BI -->
  <img src="https://img.shields.io/badge/Power%20BI-Visualization-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=black">

  <!-- DAX -->
  <img src="https://img.shields.io/badge/DAX-Business%20Analytics-blue?style=for-the-badge">

  <!-- Azure -->
  <img src="https://img.shields.io/badge/Azure-ETL%20Pipelining-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white">

  <!-- ADF -->
  <img src="https://img.shields.io/badge/Azure%20Data%20Factory-Pipelines-FF6A00?style=for-the-badge&logo=microsoft-azure&logoColor=white">

  <!-- SQL -->
  <img src="https://img.shields.io/badge/SQL-Data%20Processing-005C84?style=for-the-badge&logo=postgresql&logoColor=white">

  <!-- Python -->
  <img src="https://img.shields.io/badge/Python-Optional%20Data%20Cleaning-3776AB?style=for-the-badge&logo=python&logoColor=white">

  <!-- GitHub -->
  <img src="https://img.shields.io/badge/GitHub-Version%20Control-181717?style=for-the-badge&logo=github&logoColor=white">

</p>

<hr style="margin:35px 0;">


<!-- ======================= PROJECT OVERVIEW ======================== -->
<h2 style="font-weight:600;">Project Overview</h2>

<p>
This project combines <strong>Data Engineering</strong> and <strong>Business Intelligence</strong> 
to provide a holistic analysis of Meta Ads campaigns (Facebook & Instagram).  
The dataset undergoes cloud-based processing through an 
<strong>Azure ETL Pipeline</strong>, enabling clean, scalable, and automated data ingestion before 
visualization inside Power BI.
</p>

<p>The solution provides insights into:</p>

<ul>
  <li>Campaign performance and KPI behaviour</li>
  <li>Audience demographics and regional trends</li>
  <li>Cost efficiency and ROI measurement</li>
  <li>Hourly, weekly, and monthly engagement patterns</li>
  <li>Ad-type performance throughout the conversion funnel</li>
</ul>


<hr style="margin:35px 0;">


<!-- ======================= AZURE ETL PIPELINE ====================== -->
<h2 style="font-weight:600;">Azure ETL Pipeline Architecture (Highlight)</h2>

<p>
A full <strong>Azure-based ETL pipeline</strong> was implemented to automate the ingestion and transformation 
of ads, events, campaigns, and user datasets before loading into Power BI for reporting.
</p>

<h3>✔ Cloud Pipeline Components Used</h3>
<ul>
  <li><strong>Azure Data Factory (ADF)</strong> – Orchestrated ETL workflow</li>
  <li><strong>Azure Storage (Blob / Data Lake)</strong> – Raw and cleansed data zones</li>
  <li><strong>Azure SQL Database</strong> – Curated tables feeding Power BI</li>
  <li><strong>Mapping Data Flows</strong> – Transformations: cleaning, filtering, joining</li>
  <li><strong>Triggers</strong> – Automated data refresh scheduling</li>
</ul>

<h3>✔ ETL Pipeline Workflow</h3>

<pre style="background:#f8f8f8; padding:18px; border-radius:6px;">
[Meta Ads CSVs] 
        ↓
[Azure Blob Storage - Raw Zone]
        ↓   (ADF Ingestion Pipeline)
[Azure Data Flow - Transformations]
        ↓   - Cleanup  
            - Data validation
            - Standardization
            - Dimensional modeling
        ↓
[Azure SQL Database - Curated Zone]
        ↓
[Power BI Semantic Model]
        ↓
[Final Interactive Dashboard]
</pre>

<p>
This Azure integration ensures <strong>high scalability, automated updating, cleaner data pipelines, 
and enterprise-grade reliability</strong>, making the project suitable for real-world production use cases.
</p>


<hr style="margin:40px 0;">


<!-- ====================== REPOSITORY FILES ======================== -->
<h2 style="font-weight:600;">Repository Contents</h2>

<table style="width:100%; border-collapse: collapse;">
  <tr style="background:#f4f4f4; font-weight:600;">
    <td style="padding:10px; border:1px solid #ddd;">File</td>
    <td style="padding:10px; border:1px solid #ddd;">Description</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">ads.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">Ad metadata (platform, ad_type, demographics)</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">ad_events.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">User interactions: impressions, clicks, shares, purchases</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">campaigns.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">Campaign budgets and settings</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">users.csv</td>
    <td style="padding:10px; border:1px solid #ddd;">User demographics: age, gender, country</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">.pbix Dashboard</td>
    <td style="padding:10px; border:1px solid #ddd;">Final Power BI report</td>
  </tr>

  <tr>
    <td style="padding:10px; border:1px solid #ddd;">DAX Documentation</td>
    <td style="padding:10px; border:1px solid #ddd;">Complete DAX formula reference</td>
  </tr>
</table>


<hr style="margin:40px 0;">


<!-- ====================== DASHBOARD PAGES ========================= -->
<h2 style="font-weight:600;">Dashboard Pages</h2>

<h3>1. Executive Overview</h3>
<ul>
  <li>Key KPIs</li>
  <li>Top campaigns</li>
  <li>Platform performance</li>
  <li>Monthly trends</li>
  <li>Dynamic measure switching</li>
</ul>

<h3>2. Audience Insights</h3>
<ul>
  <li>Gender & Age segmentation</li>
  <li>Country map visualization</li>
  <li>Demographic engagement matrix</li>
</ul>

<h3>3. ROI & Budget Efficiency</h3>
<ul>
  <li>CPA, CPC, CPE, ROI, ROAS</li>
  <li>Budget waterfall</li>
  <li>CTR vs Conversion – budget-influenced scatter plot</li>
</ul>

<h3>4. Time & Trend Analysis</h3>
<ul>
  <li>Hourly peak times</li>
  <li>Weekly ad-type analysis</li>
  <li>Monthly trendlines</li>
  <li>Calendar activity heatmap</li>
</ul>

<h3>5. Ad Type & Campaign Deep Dive</h3>
<ul>
  <li>Ad type comparison</li>
  <li>Full campaign funnel</li>
  <li>Detailed campaign table</li>
</ul>


<hr style="margin:40px 0;">


<!-- ============================ MODEL ============================= -->
<h2 style="font-weight:600;">Data Model (Star Schema)</h2>

<pre style="background:#f8f8f8; padding:20px; border-radius:6px; font-size:14px;">
campaigns ───┬── ads ─── ad_events
             └── users
</pre>

<p>
Designed for accuracy, maintainability, and fast analytical performance across Power BI reports.
</p>

<hr style="margin:40px 0;">


<!-- ============================ DAX =============================== -->
<h2 style="font-weight:600;">Key DAX Measures</h2>

<h3>Performance Measures</h3>
<pre style="background:#f8f8f8; padding:20px; border-radius:6px;">
Impressions = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Impression"))
Clicks = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Click"))
Engagement = [Clicks] + [Shares] + [Comments]
CTR = DIVIDE([Clicks], [Impressions], 0)
Conversion Rate = DIVIDE([Purchases], [Clicks], 0)
</pre>

<h3>Budget & ROI</h3>
<pre style="background:#f8f8f8; padding:20px; border-radius:6px;">
Total Budget = SUM(campaigns[total_budget])
CPA = DIVIDE([Total Budget], [Purchases], 0)
CPC = DIVIDE([Total Budget], [Clicks], 0)
CPE = DIVIDE([Total Budget], [Engagement], 0)
Return of Investment (ROI) = [Purchases] * 1000   -- Assumed APV
</pre>

<h3>Funnel & Waterfall Tables</h3>
<pre style="background:#f8f8f8; padding:20px; border-radius:6px;">
Budget Flow =
UNION(
  ROW("Stage", "Total Budget", "Value", [Total Budget]),
  ROW("Stage", "Spent Budget", "Value", [Spend Budget]),
  ROW("Stage", "ROI Value", "Value", [Return of Investment (ROI)])
)
</pre>

<hr style="margin:40px 0;">


<!-- ============================ HOW TO USE ======================== -->
<h2 style="font-weight:600;">How to Run This Project</h2>

<ol>
  <li>Clone the repository</li>
<pre style="background:#f8f8f8; padding:18px; border-radius:6px;">
git clone https://github.com/Rysin09/Meta-Ads-Performance-Analysis
</pre>

  <li>Open the Power BI (.pbix) file</li>
  <li>Ensure model relationships are correct</li>
  <li>Review DAX formulas</li>
  <li>Explore all 5 dashboard pages</li>
</ol>

<hr style="margin:40px 0;">


<!-- ============================ INSIGHTS ========================== -->
<h2 style="font-weight:600;">Insights Delivered</h2>

<ul>
  <li>Top-performing campaigns & demographics</li>
  <li>Platform-level ROI (Facebook vs Instagram)</li>
  <li>Spend optimization & overspending detection</li>
  <li>Peak engagement time windows</li>
  <li>Best-converting ad formats</li>
  <li>End-to-end funnel visibility</li>
</ul>

<hr style="margin:40px 0;">


<!-- ============================ AUTHOR ============================ -->
<h2 style="font-weight:600;">Author</h2>

<p>
This project showcases expertise in 
<strong>Azure ETL Pipelines</strong>, 
<strong>Power BI Development</strong>, 
<strong>DAX Engineering</strong>, 
<strong>Data Modeling</strong>, and  
<strong>Marketing Analytics</strong>.  
For collaboration or suggestions, feel free to open an Issue or Pull Request.
</p>

