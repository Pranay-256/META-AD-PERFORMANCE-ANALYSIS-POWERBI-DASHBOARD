# 📢 Meta Ad Performance Analysis Dashboard

An interactive and dynamic **Power BI Dashboard** developed to analyze advertising performance across **Meta platforms** such as **Facebook** and **Instagram**.

This project focuses on analyzing:

- Impressions
- Clicks
- Shares
- Comments
- Purchases
- Engagements
- Conversion Metrics
- Audience Demographics
- Campaign Performance

The dashboard provides dynamic insights using **Measure Parameters**, allowing users to switch between multiple event-based analyses interactively.

---

# 📌 Project Objective

The objective of this project is to help businesses and marketers analyze Meta advertisement performance and generate actionable marketing insights through interactive visualizations and KPI analysis.

The dashboard helps users:

- Track ad campaign performance
- Compare Facebook vs Instagram ads
- Analyze engagement and conversion metrics
- Monitor audience demographics
- Analyze campaign trends over time
- Identify high-performing ad types
- Optimize advertising strategies

---

# 🧰 Tools & Technologies Used

| Tool | Purpose |
|---|---|
| Power BI | Dashboard Development |
| Power Query | ETL & Data Transformation |
| DAX | Measures & Calculations |
| Excel / CSV | Data Source |
| Data Modeling | Relationship Management |
| Dynamic Parameters | Dynamic KPI & Visual Switching |
| Time Intelligence | Trend Analysis |

---

# 📂 Dataset Structure

The project follows a dimensional data modeling approach.

## Fact Table

- `ad_events`

## Dimension Tables

- `ads`
- `campaigns`
- `users`
- `Calendar Table`

---

# ⚙️ ETL Process

The project follows a complete ETL pipeline.

## 1️⃣ Extract

Imported raw advertising datasets into Power BI.

---

## 2️⃣ Transform

Performed data cleaning and transformation using Power Query.

### Data Cleaning Activities

- Corrected data types
- Standardized date formats
- Removed inconsistent values
- Validated relationship keys
- Cleaned missing records

---

## 3️⃣ Load

Loaded transformed datasets into Power BI for modeling and visualization.

---

# 🏗️ Data Modeling

The model contains:

- One Fact Table
- Multiple Dimension Tables

The structure resembles a **Hybrid Schema Structure** because of additional relationships between Ads and Campaign tables along with Calendar Table integration for Time Intelligence calculations.

### Relationships Created

| From Table | To Table | Relationship |
|---|---|---|
| campaigns | ads | One-to-Many |
| ads | ad_events | One-to-Many |
| users | ad_events | One-to-Many |
| Calendar Table | ad_events | One-to-Many |

---

# 📅 Calendar Table

A dedicated Calendar Table was created using the `event_date` column from the `ad_events` table for Time Intelligence analysis.

```DAX
Calender table = 
CALENDAR(
    MIN(ad_events[event_date]),
    MAX(ad_events[event_date])
)
```

---

## Calendar Columns

```DAX
Month = FORMAT('Calender table'[Date],"MMM")

Day Name = FORMAT('Calender table'[Date], "ddd")

Day Number = FORMAT('Calender table'[Date], "d")

Week Day = WEEKDAY('Calender table'[Date], 2)

Week Number = WEEKNUM('Calender table'[Date], 2)
```

---

# 🧠 Dynamic Measure Parameter Feature

One of the major highlights of this project is the implementation of a **Dynamic Measure Parameter**.

A parameter table called:

```text
Select Dynamic Measure
```

was created using values from the `event_type` column.

The dashboard dynamically switches between:

- Impressions
- Engagements
- Clicks
- Shares
- Comments
- Purchases

---

# ⚡ Dynamic Dashboard Functionality

Based on the selected Event Type:

✅ KPI Headers Change Dynamically  
✅ Visual Titles Update Automatically  
✅ Insights Change Dynamically  
✅ Charts Display Corresponding Analysis  

For example:

If the user selects:

```text
Engagements
```

then all KPI cards, visual titles, and dashboard insights dynamically switch to Engagement-related analysis.

---

# 📊 Dashboard Features

## ✅ KPI Cards

The dashboard contains KPI cards for:

- Impressions
- Clicks
- Shares
- Comments
- Purchases
- Engagements
- CTR (Click Through Rate)
- ER (Engagement Rate)
- CR (Conversion Rate)
- PR (Purchase Rate)
- Total Budget
- Avg. Budget Per Campaign

---

## ✅ Platform Toggle Buttons

The dashboard contains interactive buttons for:

- Facebook
- Instagram

These buttons allow users to analyze platform-specific ad performance separately.

---

## ✅ Tooltip KPI Feature

When hovering over the:

```text
Analysis by Month
```

visual, additional KPI details are displayed through a custom Tooltip Page.

This improves analytical depth and user interaction.

---

# 🎛️ Interactive Slicers

The dashboard contains dynamic slicers for:

- Select Event Type
- Campaign Name
- Target Interests

Target Interests include:

- Art
- Fashion
- Finance
- Food
- Gaming
- Photography
- Sports
- Technology
- Travel

---

# 📈 Visualizations Used

| Visualization | Purpose |
|---|---|
| KPI Cards | Performance Tracking |
| Donut Chart | Gender-based Analysis |
| Age Distribution Chart | Age-wise Performance |
| Weekly Trend Chart | Weekly Event Trends |
| Hourly Trend Chart | Hourly Event Trends |
| Map Visual | Country-wise Analysis |
| Calendar Visual | Monthly Analysis |
| Matrix Table | Ad Type Performance |

---

# 🧮 Main Measures Used

## Event Measures

```DAX
Impressions = 
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Impression"
    )
)

Clicks = 
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Click"
    )
)

Comments = 
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Comment"
    )
)

Purchases = 
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Purchase"
    )
)

Shares = 
COUNTROWS(
    FILTER(
        ad_events,
        ad_events[event_type] = "Share"
    )
)
```

---

## Engagement Measure

```DAX
Engagements = 
[Clicks] + [Shares] + [Comments]
```

---

## Budget Measures

```DAX
Total Budget = 
SUM(campaigns[total_budget])

Avg. Budget Per Campaign = 
AVERAGE(campaigns[total_budget])
```

---

# 📊 Rate Measures

## CTR (Click Through Rate)

```DAX
CTR (Click Through Rate) = 
DIVIDE([Clicks],[Impressions],0)
```

---

## ER (Engagement Rate)

```DAX
ER (Engagement Rate) = 
DIVIDE([Engagements], [Impressions], 0)
```

---

## CR (Conversion Rate)

```DAX
CR (Conversion Rate) = 
DIVIDE([Purchases], [Clicks], 0)
```

---

## PR (Purchase Rate)

```DAX
PR (Purchase Rate) = 
DIVIDE([Purchases], [Impressions], 0)
```

---

# 🖼️ Dashboard Preview

## Dashboard Image 1

![Dashboard Image 1](Images/image%201.png)

---

## Dashboard Image 2

![Dashboard Image 2](Images/image%202.png)

---

## Dashboard Image 3

![Dashboard Image 3](Images/image%203.png)

---

# 🚀 Project Highlights

✅ Dynamic Measure Parameters  
✅ Interactive KPI Switching  
✅ Facebook & Instagram Analysis  
✅ Time Intelligence Analysis  
✅ Dynamic Dashboard Titles  
✅ Tooltip Reporting  
✅ Advanced DAX Calculations  
✅ Interactive Visualizations  
✅ Marketing Analytics  

---

# 🧠 Key Business Insights

Using this dashboard, businesses can:

- Analyze campaign effectiveness
- Compare platform performance
- Identify high-performing audience groups
- Optimize advertising budgets
- Improve audience targeting
- Track engagement trends
- Monitor conversions and purchases
- Make data-driven marketing decisions

---

# 📚 Skills Demonstrated

- Power BI
- Power Query
- DAX
- Data Modeling
- Dynamic Parameters
- Time Intelligence
- KPI Reporting
- Dashboard Design
- Marketing Analytics
- Data Visualization

---

# 📌 Conclusion

The Meta Ad Performance Analysis Dashboard transforms raw advertising event data into meaningful business insights through interactive visualizations, dynamic KPI analysis, and advanced DAX calculations.

This project demonstrates practical implementation of:

- ETL Process
- Data Cleaning
- Dynamic Measures
- Data Modeling
- Time Intelligence
- Interactive Reporting
- Marketing Analytics

The dashboard helps businesses and marketers optimize advertising performance and make data-driven marketing decisions using interactive and dynamic analytics.

---

# 👨‍💻 Author

**Pranay Jha**

If you liked this project, feel free to ⭐ the repository.
