# META ANALYSIS – DAX DOCUMENTATION

**Project:** Meta Ads Performance Dashboard

**Author:** Aryan Singh

**Purpose:** Complete DAX Reference for Measures, Calculated Columns, Tables, Titles & Dynamic Components

---

# **1. DYNAMIC TITLES (For Visual Headings)**

### **1.1 Age Title**

**Purpose:** Dynamic chart title based on selected metric.

```
Age Title = SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " by Target Age"

```

### **1.2 Gender Title**

**Purpose:** Dynamic title for gender charts.

```
Gender Title = SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " by Gender"

```

### **1.3 Hourly Trend Title**

**Purpose:** Dynamic title for hourly trend charts.

```
Hourly Trend = "Hourly " & SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " Trend"

```

### **1.4 Weekly Trend Title**

**Purpose:** Dynamic weekly trend title.

```
Weekly Trend = "Weekly " & SELECTEDVALUE('Select Dynamic Measures'[Dynamic Title]) & " Trend"

```

---

# **2. BASIC EVENT MEASURES**

### **2.1 Impressions**

```
Impressions = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Impression"))

```

### **2.2 Clicks**

```
Clicks = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Click"))

```

### **2.3 Shares**

```
Shares = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Share"))

```

### **2.4 Comments**

```
Comments = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Comment"))

```

### **2.5 Purchases**

```
Purchases = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Purchase"))

```

---

# **3. DERIVED & PERFORMANCE MEASURES**

### **3.1 Engagement**

```
Engagement = [Shares] + [Clicks] + [Comments]

```

### **3.2 CTR (Click Through Rate)**

```
CTR (Click Through Rate) = DIVIDE([Clicks], [Impressions], 0)

```

### **3.3 Engagement Rate**

```
Engagement Rate = DIVIDE([Engagement], [Impressions], 0)

```

### **3.4 Conversion Rate**

```
Conversion Rate = DIVIDE([Purchases], [Clicks], 0)

```

### **3.5 Purchase Rate**

```
Purchase Rate = DIVIDE([Purchases], [Impressions], 0)

```

---

# **4. BUDGET & COST MEASURES**

### **4.1 Total Budget**

```
Total Budget = SUM(campaigns[total_budget])

```

### **4.2 Avg Budget per Campaign**

```
Avg Budget per Campaign = AVERAGE(campaigns[total_budget])

```

### **4.3 Spend Budget**

```
Spend Budget = [Total Budget]

```

### **4.4 Cost Per Acquisition (CPA)**

```
Cost Per Acquisition (CPA) = DIVIDE([Total Budget], [Purchases], 0)

```

### **4.5 Cost Per Click (CPC)**

```
Cost Per Click (CPC) = DIVIDE([Total Budget], [Clicks], 0)

```

### **4.6 Cost Per Engagement (CPE)**

```
Cost Per Engagement (CPE) = DIVIDE([Total Budget], [Engagement], 0)

```

---

# **5. ROI MEASURE**

### **5.1 Return on Investment (ROI)**

Assumed avg revenue per purchase = **1000**

```
Return of Investment (ROI) = [Purchases] * 1000

```

*(You can replace 1000 with your own APV.)*

---

# **6. DATE/TIME COLUMNS (Calculated Columns)**

### **6.1 Event Date**

```
Event Date = DATEVALUE(ad_events[timestamp])

```

### **6.2 Event Hour**

```
Event Hour = HOUR(ad_events[timestamp])

```

---

# **7. CALENDAR TABLE**

### **7.1 Create Calendar**

```
Calender table = CALENDAR(MIN(ad_events[Event Date]), MAX(ad_events[Event Date]))

```

### **7.2 Day Name**

```
Day Name = FORMAT('Calender table'[Date], "ddd")

```

### **7.3 Day Number**

```
Day Number = FORMAT('Calender table'[Date], "d")

```

### **7.4 Month**

```
Month = FORMAT('Calender table'[Date], "mmm")

```

### **7.5 Week Day**

```
Week Day = WEEKDAY('Calender table'[Date], 2)

```

### **7.6 Week Number**

```
Week Number = WEEKNUM('Calender table'[Date], 2)

```

---

# **8. DYNAMIC METRIC SELECTION (Parameter Table)**

### **8.1 Dynamic Measure Selection Table**

```
Select Dynamic Measures = {
    ("Impressions", NAMEOF('ad_events'[Impressions]), 0),
    ("Engagement", NAMEOF('ad_events'[Engagement]), 1),
    ("Clicks", NAMEOF('ad_events'[Clicks]), 2),
    ("Shares", NAMEOF('ad_events'[Shares]), 3),
    ("Comments", NAMEOF('ad_events'[Comments]), 4),
    ("Purchases", NAMEOF('ad_events'[Purchases]), 5)
}

```

---

# **9. CUSTOM TABLES FOR CHARTS**

## **9.1 Budget Flow Table**

Used for Waterfall Chart

```
Budget Flow =
UNION(
    ROW("Stage", "Total Budget", "Value", [Total Budget]),
    ROW("Stage", "Spent Budget", "Value", [Spend Budget]),
    ROW("Stage", "ROI Value", "Value", [Return of Investment (ROI)])
)

```

## **9.2 Campaign Funnel Table**

Used for Funnel Chart

```
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
    SELECTCOLUMNS(baseTable, "Campaign Name", "Stage", "Purchases", "Value", [Purchases])
)

```