<p align="center">
  <img src="Images/00-Project-Banner.png" alt="Repair & Return Operations Dashboard Banner" width="100%">
</p>

<h1 align="center">Repair & Return Operations Dashboard | Power BI</h1>

<p align="center">
A business intelligence solution for monitoring end-to-end repair and return operations, supplier performance, cycle time, aging, recovery progress, repeated failures, and critical stock risk.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI">
  <img src="https://img.shields.io/badge/DAX-Analytics-1f77b4?style=for-the-badge" alt="DAX">
  <img src="https://img.shields.io/badge/Power%20Query-ETL-2ca02c?style=for-the-badge" alt="Power Query">
  <img src="https://img.shields.io/badge/Data%20Modeling-Star%20Schema-orange?style=for-the-badge" alt="Data Modeling">
</p>

## Business value at a glance

**Decision:** Which repair cases need escalation, and where is the return pipeline blocked?

- The anonymized dashboard snapshot tracks **177 items**, including **107 open cases** across **11 suppliers**.
- Highlights **5 open cases older than 365 days**, with the oldest open case at **407 days**.
- Supports a prioritized follow-up queue using aging, process stage, supplier, and stock exposure.

**Inspect the work:** [Executive overview](Images/01-Executive-Overview.png) · [Data model](Images/17-Data-Model.png) · [Power Query workflow](Images/18-Power-Query-Workflow.png) · [Proposed action plan](Images/15-Proposed-Team-Action-Plan.png)

**Evidence boundary:** The public repository contains presentation assets and selected DAX examples. Source operational data and the PBIX are not published. These are snapshot findings and proposed decisions; no measured cycle-time reduction or financial recovery is claimed.

## 🎬 Dashboard Walkthrough

![Dashboard Walkthrough](GIFs/01-Dashboard-Walkthrough.gif)

## 📊 Project Snapshot

| KPI | Value |
|---|---:|
| Total tracked items | **177** |
| Completed items | **70** |
| Open items | **107** |
| Completion rate | **39.55%** |
| Suppliers monitored | **11** |
| Countries represented | **8** |
| Oldest open case | **407 days** |
| Open cases older than 365 days | **5** |

> Figures are based on the anonymized portfolio version of the dashboard.

## 🎯 Business Problem

Repair & Return processes often span suppliers, repair centers, logistics stages, warehouses, and internal teams. Without centralized reporting, management can struggle with visibility, aging cases, supplier follow-up, cycle-time bottlenecks, overdue targets, and recovery planning.

This dashboard centralizes those signals into one analytical environment.

## ✅ What the Dashboard Enables

- Monitor open, completed, and incoming repair items
- Identify operational stopping points and bottlenecks
- Analyze supplier concentration and performance
- Track overdue targets and upcoming warehouse returns
- Compare forecast and actual recovery performance
- Measure cycle time by process stage
- Detect repeat failures
- Assess critical spare-parts and stock exposure
- Translate findings into clear action priorities

## 🖼️ Dashboard Pages

### Executive Overview
<p align="center"><img src="Images/01-Executive-Overview.png" width="100%" alt="Executive Overview"></p>

### Stopping Point Analysis
<p align="center"><img src="Images/02-Stopping-Point-Analysis.png" width="100%" alt="Stopping Point Analysis"></p>

### System Analysis
<p align="center"><img src="Images/03-System-Analysis.png" width="100%" alt="System Analysis"></p>

### Supplier Performance
<p align="center"><img src="Images/04-Supplier-Performance.png" width="100%" alt="Supplier Performance"></p>

### Aging & Critical Attention
<p align="center"><img src="Images/06-Aging-Critical-Attention.png" width="100%" alt="Aging and Critical Attention"></p>

### Upcoming Returns
<p align="center"><img src="Images/07-Upcoming-Returns.png" width="100%" alt="Upcoming Returns"></p>

### Cumulative Forecast vs Actual
<p align="center"><img src="Images/09-Cumulative-S-Curve.png" width="100%" alt="Cumulative Forecast vs Actual"></p>

### Cycle Time by Step
<p align="center"><img src="Images/11-Cycle-Time-by-Step.png" width="100%" alt="Cycle Time by Step"></p>

### Repeat Failure Watchlist
<p align="center"><img src="Images/13-Repeat-Failure-Watchlist.png" width="100%" alt="Repeat Failure Watchlist"></p>

### Critical Stock Risk
<p align="center"><img src="Images/14-Critical-Stock-Risk.png" width="100%" alt="Critical Stock Risk"></p>

### Proposed Team Action Plan
<p align="center"><img src="Images/15-Proposed-Team-Action-Plan.png" width="100%" alt="Proposed Team Action Plan"></p>

## 🧱 Solution Architecture

The project follows an end-to-end BI workflow:

```text
Operational Excel Tracker
        ↓
Power Query Transformation
        ↓
Power BI Data Model
        ↓
DAX Measures & Business Logic
        ↓
Interactive KPI & Operational Dashboards
```

<p align="center"><img src="Images/16-Solution-Architecture.png" width="100%" alt="Solution Architecture"></p>

## 🗂️ Data Model

The analytical model uses a central operational fact table supported by calendar, mapping, and status tables. The design applies one-to-many relationships, controlled filter direction, dedicated measures, and reusable business classifications.

<p align="center"><img src="Images/17-Data-Model.png" width="100%" alt="Data Model"></p>

## 🔄 Power Query Workflow

Power Query was used to standardize source data, apply types, clean text fields, preserve operational blanks where needed, prepare date fields, and create business classifications before loading the model.

<p align="center"><img src="Images/18-Power-Query-Workflow.png" width="100%" alt="Power Query Workflow"></p>

## 🧮 DAX Highlights

```DAX
Total Items =
CALCULATE(
    COUNTROWS(TRACKER),
    TRACKER[PJ] = "TSML3"
)
```

```DAX
Completed Items =
CALCULATE(
    COUNTROWS(TRACKER),
    TRACKER[PJ] = "TSML3",
    TRACKER[STATUS] = "Completed"
)
```

```DAX
Open Items =
[Total Items] - [Completed Items]
```

```DAX
Completion Rate =
DIVIDE(
    [Completed Items],
    [Total Items],
    0
)
```

```DAX
Upcoming in 30 Days =
CALCULATE(
    COUNTROWS(TRACKER),
    TRACKER[EXP. ETA WD] >= TODAY(),
    TRACKER[EXP. ETA WD] <= TODAY() + 30
)
```

## 💡 Business Impact

The dashboard is designed to support operational decisions by centralizing reporting, highlighting aging and bottlenecks, and connecting supplier follow-up and stock risk with the repair pipeline. Implementation outcomes have not been measured in this portfolio.

## 🛠️ Tools & Skills

`Power BI` `DAX` `Power Query` `Excel` `Data Modeling` `Operations Analytics` `Supply Chain Analytics` `KPI Design` `Data Storytelling`

## 📁 Repository Contents

```text
PowerBi-Repair-Return-Operations-Dashboard/
├── README.md
├── Images/
├── GIFs/
├── LICENSE
├── SECURITY.md
├── CONTRIBUTING.md
└── .gitignore
```

> The repository contains the anonymized portfolio presentation assets and analytical documentation. Source operational data is not published.

## 👤 Author

**Hussieni Gamal**  
Data Analyst | Business Intelligence | Power BI | SQL | Excel | Python

[LinkedIn](https://www.linkedin.com/in/hussieni-gamal-549b68134/) • [GitHub Profile](https://github.com/HussieniGamal) • [Portfolio](https://sites.google.com/view/hussienigamal/home)
