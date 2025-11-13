<h1>Meta Ads Performance Analysis Dashboard</h1>

<p>
This project presents a comprehensive analysis of Meta Ads (Facebook & Instagram) performance using 
<strong>Power BI</strong>, <strong>DAX</strong>, and a structured <strong>data modeling</strong> approach. 
The goal is to provide actionable insights into campaign performance, audience behavior, 
budget utilization, and ROI efficiency.
</p>

<hr>

<h2>Project Overview</h2>
<p>
The dashboard offers data-driven insights for marketing teams to evaluate:
</p>
<ul>
  <li>Campaign efficiency and performance trends</li>
  <li>Cost and ROI analysis across campaigns and platforms</li>
  <li>Demographic behavior (age, gender, region)</li>
  <li>Time-based engagement patterns</li>
  <li>Ad-type effectiveness and funnel performance</li>
</ul>

<hr>

<h2>Repository Contents</h2>
<table>
  <tr><th>File</th><th>Description</th></tr>
  <tr><td>ads.csv</td><td>Ad-level information including platform, ad type, and targeting details</td></tr>
  <tr><td>ad_events.csv</td><td>User interaction logs such as impressions, clicks, shares, and purchases</td></tr>
  <tr><td>campaigns.csv</td><td>Campaign metadata including total budget</td></tr>
  <tr><td>users.csv</td><td>User demographic information (age, gender, country)</td></tr>
  <tr><td>Power BI File (.pbix)</td><td>Complete dashboard with all visuals and calculations</td></tr>
  <tr><td>DAX Documentation</td><td>Fully documented measures, calculated columns, titles, and tables</td></tr>
</table>

<hr>

<h2>Dashboard Structure (5 Pages)</h2>

<h3>1. Executive Overview</h3>
<ul>
  <li>KPI metrics (Impressions, Clicks, Engagement, Purchases)</li>
  <li>Platform distribution analysis</li>
  <li>Top performing campaigns</li>
  <li>Monthly engagement and metric trends</li>
  <li>Dynamic measure switching</li>
</ul>

<h3>2. Audience Insights</h3>
<ul>
  <li>Age and gender performance breakdown</li>
  <li>Country-wise engagement map</li>
  <li>Matrix of demographic engagement rates</li>
  <li>Dynamic demographic titles</li>
</ul>

<h3>3. ROI & Budget Efficiency</h3>
<ul>
  <li>Cost metrics (CPA, CPC, CPE)</li>
  <li>ROI and ROAS calculations</li>
  <li>Waterfall analysis of Budget → Spend → ROI</li>
  <li>Scatter plot showing CTR vs Conversion vs Budget</li>
  <li>Campaign-wise cost-efficiency comparison</li>
</ul>

<h3>4. Time & Trend Analysis</h3>
<ul>
  <li>Hourly performance trends</li>
  <li>Weekly engagement by ad type</li>
  <li>Monthly conversion and engagement trends</li>
  <li>Date-based calendar visual patterns</li>
</ul>

<h3>5. Ad Type & Campaign Deep Dive</h3>
<ul>
  <li>Ad type performance matrix across platforms</li>
  <li>Campaign funnel (Impressions → Clicks → Purchases)</li>
  <li>Detailed campaign-level metric table</li>
  <li>Ad creative effectiveness analysis</li>
</ul>

<hr>

<h2>Data Model</h2>
<pre>
campaigns ───┬── ads ─── ad_events
             └── users
</pre>

<p>
A star-schema model is implemented with <strong>ad_events</strong> as the fact table and campaigns, ads, users, and calendar tables as dimensions. 
This ensures scalable performance and accurate DAX evaluation.
</p>

<hr>

<h2>Key DAX Measures</h2>

<h3>Performance Metrics</h3>
<pre>
Impressions = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Impression"))
Clicks = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Click"))
Engagement = [Clicks] + [Shares] + [Comments]
CTR = DIVIDE([Clicks], [Impressions], 0)
Engagement Rate = DIVIDE([Engagement], [Impressions], 0)
Conversion Rate = DIVIDE([Purchases], [Clicks], 0)
</pre>

<h3>Budget & ROI Metrics</h3>
<pre>
Total Budget = SUM(campaigns[total_budget])
CPA = DIVIDE([Total Budget], [Purchases], 0)
CPC = DIVIDE([Total Budget], [Clicks], 0)
CPE = DIVIDE([Total Budget], [Engagement], 0)
Return of Investment (ROI) = [Purchases] * 1000   // Assumed APV
</pre>

<h3>Dynamic Titles</h3>
<pre>
Age Title = SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " by Target Age"
Gender Title = SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " by Gender"
Hourly Trend = "Hourly " & SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " Trend"
Weekly Trend = "Weekly " & SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " Trend"
</pre>

<h3>Custom Tables</h3>
<h4>Budget Flow Table</h4>
<pre>
Budget Flow =
UNION(
    ROW("Stage", "Total Budget", "Value", [Total Budget]),
    ROW("Stage", "Spent Budget", "Value", [Spend Budget]),
    ROW("Stage", "ROI Value", "Value", [Return of Investment (ROI)])
)
</pre>

<h4>Campaign Funnel Table</h4>
<pre>
Campaign Funnel =
VAR baseTable =
    SUMMARIZECOLUMNS(
        campaigns[campaign_id],
        campaigns[name],
        "Impressions", CALCULATE(COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Impression"))),
        "Clicks", CALCULATE(COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Click"))),
        "Purchases", CALCULATE(COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Purchase")))
    )
RETURN
UNION(
    SELECTCOLUMNS(baseTable, "Campaign Name", [name], "Stage", "Impressions", "Value", [Impressions]),
    SELECTCOLUMNS(baseTable, "Campaign Name", [name], "Stage", "Clicks", "Value", [Clicks]),
    SELECTCOLUMNS(baseTable, "Campaign Name", [name], "Stage", "Purchases", "Value", [Purchases])
)
</pre>

<hr>

<h2>How to Use This Project</h2>
<ol>
  <li>Clone the repository</li>
<pre>git clone https://github.com/Rysin09/Meta-Ads-Performance-Analysis</pre>
  <li>Open the Power BI (.pbix) file</li>
  <li>Ensure data model relationships are correctly created</li>
  <li>Review and apply DAX measures</li>
  <li>Explore interactive dashboard pages</li>
</ol>

<hr>

<h2>Insights Delivered</h2>
<ul>
  <li>Platform-wise ROI comparison</li>
  <li>Audience demographic behavior</li>
  <li>Campaign-level performance benchmarks</li>
  <li>Budget utilization and cost efficiency</li>
  <li>Time-based engagement distribution</li>
  <li>Ad type success and funnel performance</li>
</ul>

<hr>

<h2>Author</h2>
<p>
This project was developed as a professional demonstration of Power BI analytics, DAX modeling, 
and marketing data intelligence. Suggestions and contributions are welcome through GitHub issues or pull requests.
</p>
