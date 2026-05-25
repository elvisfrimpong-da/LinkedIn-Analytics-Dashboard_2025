
# LinkedIn Analytics Dashboard (2025)

## Overview

This project analyzes LinkedIn performance data for the year 2025, focusing on follower growth and engagement trends. The dashboard was built in Power BI to track month-over-month (MoM) performance, identify growth patterns, and highlight periods of strong or weak engagement.

The goal of the project is to demonstrate practical data modeling, DAX calculations, and analytical storytelling using real-world social media analytics data.

---

## Objectives

* Analyze monthly new follower acquisition
* Measure engagement performance and its relationship with follower growth
* Track month-over-month growth trends
* Present insights through clean, executive-ready KPIs and visuals

---

## Dataset

The dataset consists of LinkedIn analytics exports for 2025, including:

* Daily new followers
* Daily engagement metrics (impressions and engagements)
* Connection-level metadata

> Note: 2024 data was not available. Year-over-year analysis was intentionally excluded to maintain analytical integrity.

---

## Data Model

The Power BI model follows a star-schema structure:

* A central **Dates** table
* Fact tables for **Followers**, **Engagement**, and **Connections**
* A dedicated **Measures** table for all DAX calculations

This structure ensures accurate time intelligence and scalable analysis.

---

## Key Metrics

* **Total Followers (New)**
* **Total Engagements**
* **Month-over-Month Follower Growth (%)**
* **Month-over-Month Engagement Growth (%)**

Custom DAX measures were used to calculate previous-month values, growth rates, and KPI indicators.

---

## DAX Measures (Copy & Paste)

<details>
<summary><strong>Followers – Core Measures</strong></summary>

```DAX
Total Followers =
SUM ( FOLLOWERS[New followers] )
```

```DAX
Followers Previous Month =
CALCULATE (
    [Total Followers],
    DATEADD ( Dates[Date], -1, MONTH )
)
```

```DAX
Followers Growth =
[Total Followers] - [Followers Previous Month]
```

```DAX
Followers Growth % =
DIVIDE ( [Followers Growth], [Followers Previous Month], 0 )
```

</details>

<details>
<summary><strong>Followers – KPI Text & Icons</strong></summary>

```DAX
Followers Icon =
SWITCH (
    TRUE (),
    [Followers Growth] > 0, "▲",
    [Followers Growth] < 0, "▼",
    "●"
)
```

```DAX
Followers MoM KPI Text =
VAR GrowthPct =
    FORMAT ( [Followers Growth %], "0.0%" )
RETURN
[Followers Icon] & " " & GrowthPct & " MoM"
```

```DAX
Followers MoM Color =
SWITCH (
    TRUE (),
    [Followers Growth] > 0, "#2E7D32",
    [Followers Growth] < 0, "#C62828",
    "#6E6E6E"
)
```

</details>

<details>
<summary><strong>Engagement – Core Measures</strong></summary>

```DAX
Total Engagements =
SUM ( ENGAGEMENT[Engagements] )
```

```DAX
Engagements Previous Month =
CALCULATE (
    [Total Engagements],
    DATEADD ( Dates[Date], -1, MONTH )
)
```

```DAX
Engagements Growth =
[Total Engagements] - [Engagements Previous Month]
```

```DAX
Engagements Growth % =
DIVIDE ( [Engagements Growth], [Engagements Previous Month], 0 )
```

</details>

<details>
<summary><strong>Engagement – KPI Text & Icons</strong></summary>

```DAX
Engagement MoM Icon =
SWITCH (
    TRUE (),
    [Engagements Growth] > 0, "▲",
    [Engagements Growth] < 0, "▼",
    "●"
)
```

```DAX
Engagement MoM KPI Text =
VAR GrowthPct =
    FORMAT ( [Engagements Growth %], "0.0%" )
RETURN
[Engagement MoM Icon] & " " & GrowthPct & " MoM"
```

```DAX
Engagement MoM Color =
SWITCH (
    TRUE (),
    [Engagements Growth] > 0, "#2E7D32",
    [Engagements Growth] < 0, "#C62828",
    "#6E6E6E"
)
```

</details>

---

## Dashboard Features

* KPI cards showing total followers and engagements with MoM comparison
* MoM trend lines for followers and engagements
* Combo chart explaining monthly follower additions alongside MoM growth
* Clear visual hierarchy and consistent formatting
* Key insights section summarizing analytical findings

---

## Key Insights

* Engagement growth peaked in October and was followed by the strongest positive follower growth, suggesting engagement activity precedes audience expansion.
* August recorded the weakest performance, with negative follower MoM growth aligning with the lowest engagement levels.
* Sustained engagement growth generally resulted in more stable follower acquisition.

---

## Tools & Technologies

* Power BI Desktop
* DAX (Data Analysis Expressions)
* Power Query
* Microsoft Excel (data source)

---

## Limitations

* Analysis is limited to 2025 due to lack of historical (2024) data
* Results reflect available LinkedIn export metrics and do not include content-level attribution

---

## Preview

Dashboard screenshots are included in this repository to illustrate the final output.
![WhatsApp Image 2026-01-02 at 10 28 51](https://github.com/user-attachments/assets/4cb4dd17-e9d2-440b-bd0a-25bde0b496d7)

---
## Author

**Elvis Frimpong**  
Data Analyst | Agricultural Engineer  
LinkedIn: [linkedin.com/in/elvisfrimpong](https://www.linkedin.com/in/elvisfrimpong)

---
