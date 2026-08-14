# EV Battery Manufacturing & Quality Analytics Dashboard

## 📊 Project Overview

The **EV Battery Manufacturing & Quality Analytics Dashboard** is an interactive Power BI project designed to analyze electric vehicle battery cell production, manufacturing processes, supplier performance, and quality/defect patterns.

The dashboard transforms **20,000+ EV battery quality records** into an interactive three-page analytical report. It combines production KPIs, DAX calculations, manufacturing process analysis, supplier and shift comparisons, and defect analysis to help identify areas of strong performance and potential quality issues.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Monitor overall battery cell production.
* Compare production performance across manufacturing lines.
* Analyze production across different shifts.
* Compare supplier performance.
* Monitor good and defective battery cells.
* Analyze defect rates and overall quality.
* Identify common defect types.
* Analyze battery manufacturing parameters.
* Study relationships between temperature, capacity, resistance, and other process parameters.
* Compare QC grades across production.
* Provide interactive quality and defect analysis.
* Create an advanced multi-page Power BI dashboard with navigation.

---

# 🛠️ Tools & Technologies

* **Microsoft Power BI**
* **Power Query**
* **DAX**
* **Data Visualization**
* **Interactive Slicers**
* **Page Navigation**
* **Decomposition Tree**
* **Key Influencers**
* **Conditional Formatting**
* **Scatter Plot Analysis**
* **Matrix / Heatmap Analysis**

---

# 📁 Dataset

The project uses an **EV Battery QC synthetic defect dataset** containing battery-cell-level manufacturing and quality information.

### Dataset Size

* **20,000+ records**
* Each record represents an individual battery cell.

---

# 📋 Dataset Columns

| Column                     | Description                                         |
| -------------------------- | --------------------------------------------------- |
| `Cell_ID`                  | Unique identifier for each battery cell             |
| `Batch_ID`                 | Manufacturing batch identifier                      |
| `Production_Line`          | Production line where the cell was manufactured     |
| `Shift`                    | Manufacturing shift                                 |
| `Supplier`                 | Supplier associated with the battery cell           |
| `Ambient_Temp_C`           | Ambient temperature in Celsius                      |
| `Anode_Overhang_mm`        | Anode overhang measurement in millimeters           |
| `Electrolyte_Volume_ml`    | Electrolyte volume in milliliters                   |
| `Internal_Resistance_mOhm` | Internal resistance measured in milliohms           |
| `Capacity_mAh`             | Battery capacity in milliamp-hours                  |
| `Retention_50Cycle_Pct`    | Capacity retention after 50 cycles                  |
| `Defect_Type`              | Type of defect identified during quality inspection |
| `Inspector_Comment`        | Comments recorded during inspection                 |
| `QC_Grade`                 | Quality-control grade assigned to the battery cell  |

---

# 🧹 Data Preparation

Data preparation was performed before building the dashboard to make the dataset suitable for Power BI analysis.

### Main preparation activities

* Checked the dataset structure.
* Reviewed column data types.
* Verified numerical fields.
* Checked categorical fields.
* Reviewed duplicate records.
* Handled data-quality issues where required.
* Prepared fields for Power BI visualizations.
* Created a clean analytical dataset for dashboard development.

**Power Query** was used as the primary data transformation and preparation environment.

---

# 🧮 DAX Measures

Five main DAX measures were created for the dashboard.

### 1. Total Production

```DAX
Total Production =
DISTINCTCOUNT('Battery QC'[Cell_ID])
```

Measures the total number of manufactured battery cells.

---

### 2. Good Units

```DAX
Good Units =
CALCULATE(
    [Total Production],
    'Battery QC'[Defect_Type] = "None"
)
```

Measures cells that passed the defect classification.

---

### 3. Defective Units

```DAX
Defective Units =
CALCULATE(
    [Total Production],
    'Battery QC'[Defect_Type] <> "None"
)
```

Measures cells classified with a defect.

---

### 4. Defect Rate

```DAX
Defect Rate =
DIVIDE(
    [Defective Units],
    [Total Production],
    0
)
```

Measures the proportion of production classified as defective.

---

### 5. Quality %

```DAX
Quality % =
DIVIDE(
    [Good Units],
    [Total Production],
    0
)
```

Measures the proportion of production classified as good units.

> **Note:** The exact `"None"` condition should match the actual value used in the `Defect_Type` column of the dataset.

---

# 📊 Dashboard Structure

The Power BI report contains **three interconnected pages**.

Navigation buttons are used to move between the pages.

```text
EXECUTIVE OVERVIEW
        ↓
PRODUCTION & PROCESS ANALYTICS
        ↓
QUALITY & DEFECT ANALYTICS
```

---

# 🏠 Page 1 — Executive Overview

### Purpose

The Executive Overview provides a high-level summary of battery production and quality performance.

### KPI Cards

The page contains:

* **Defect Rate**
* **Defective Units**
* **Total Production**
* **Good Units**
* **Quality %**

### Visualizations

#### Production by Production Line

Compares total battery production across:

* Line 1
* Line 2
* Line 3

**Fields used:**

* Axis → `Production_Line`
* Values → `Total Production`

---

#### Production by Shift

Analyzes production volume across:

* Morning
* Evening
* Night

**Fields used:**

* Axis → `Shift`
* Values → `Total Production`

---

#### QC Grade Distribution

Shows the distribution of battery cells across QC grades.

**Fields used:**

* Legend → `QC_Grade`
* Values → `Total Production`

---

#### Defect Rate by QC Grade

Provides a visual comparison of defect-related performance across QC grades.

**Fields used:**

* Category → `QC_Grade`
* Values → `Defect Rate`

---

#### Capacity by Supplier

Compares battery capacity performance across suppliers.

**Fields used:**

* Category → `Supplier`
* Values → `Capacity_mAh`

---

### Interactive Filters

The page includes filters for:

* `QC_Grade`
* `Supplier`
* `Shift`

---

# ⚙️ Page 2 — Production & Process Analytics

### Purpose

This page focuses on manufacturing operations, suppliers, production lines, shifts, and battery process parameters.

### Visualizations

#### Production by Supplier

Compares production contribution from different suppliers.

**Fields:**

* Axis → `Supplier`
* Values → `Total Production`

---

#### Production by Line & Shift

Analyzes the distribution of production across production lines and shifts.

**Fields:**

* Axis → `Production_Line`
* Legend → `Shift`
* Values → `Total Production`

---

#### Capacity by Production Line

Compares battery capacity across production lines.

**Fields:**

* Axis → `Production_Line`
* Values → Average `Capacity_mAh`

---

#### Temperature vs Capacity

A scatter plot used to investigate the relationship between ambient temperature and battery capacity.

**Fields:**

* X-axis → `Ambient_Temp_C`
* Y-axis → `Capacity_mAh`
* Legend → `QC_Grade`
* Details → `Cell_ID`

---

### Process Parameters

The project analyzes the following manufacturing parameters:

* `Ambient_Temp_C`
* `Anode_Overhang_mm`
* `Electrolyte_Volume_ml`
* `Internal_Resistance_mOhm`
* `Capacity_mAh`
* `Retention_50Cycle_Pct`

These parameters provide a deeper view of battery manufacturing and performance.

---

# 🔍 Page 3 — Quality & Defect Analytics

### Purpose

The Quality & Defect Analytics page focuses on identifying defective production and understanding where quality problems occur.

### Visualizations

#### Defective Units by Defect Type

Identifies the number of defective cells associated with each defect category.

**Fields:**

* Axis → `Defect_Type`
* Values → `Defective Units`

---

#### Defective Units by Production Line

Compares defective cells across manufacturing lines.

**Fields:**

* Axis → `Production_Line`
* Values → `Defective Units`

---

#### Defect Rate by Production Line

Compares the defect rate between production lines.

**Fields:**

* Axis → `Production_Line`
* Values → `Defect Rate`

---

#### Defect Rate by Supplier

Compares defect-rate performance across suppliers.

**Fields:**

* Axis → `Supplier`
* Values → `Defect Rate`

---

#### Defect Rate by Shift

Analyzes defect-rate differences between manufacturing shifts.

**Fields:**

* Axis → `Shift`
* Values → `Defect Rate`

---

#### Defect Type Analysis

The dashboard includes defect categories such as:

* Critical Resistance
* High Internal Resistance
* Low Capacity
* Poor Retention
* Severe Capacity Fade
* Short Circuit Risk
* Other dataset-specific defect classifications

This helps identify the most frequently occurring quality issues.

---

# 🔎 Advanced Power BI Features

## Decomposition Tree

The Decomposition Tree is used for interactive defect analysis.

### Main metric

`Defective Units`

### Analysis dimensions

* `Production_Line`
* `Shift`
* `Supplier`
* `Defect_Type`
* `QC_Grade`

This allows users to drill down from overall defective production into specific operational categories.

---

## 🎯 Key Influencers

The Key Influencers visual is used to investigate factors associated with quality and defect outcomes.

Potential factors include:

* `Production_Line`
* `Shift`
* `Supplier`
* `Ambient_Temp_C`
* `Anode_Overhang_mm`
* `Electrolyte_Volume_ml`
* `Internal_Resistance_mOhm`
* `Capacity_mAh`
* `Retention_50Cycle_Pct`
* `QC_Grade`

---

# 🎛️ Interactive Features

The dashboard includes:

* Page navigation buttons
* Slicers
* Cross-filtering
* Interactive charts
* Drill-down analysis
* Decomposition Tree
* Key Influencers
* Conditional formatting
* Scatter plot analysis
* KPI cards
* Interactive production and quality comparisons

---

# 📌 Key Business Questions Answered

The dashboard is designed to answer questions such as:

### Production

* Which production line produces the most cells?
* Which shift contributes the most production?
* Which supplier contributes the highest production volume?
* How is production distributed across lines and shifts?

### Quality

* What percentage of cells are defective?
* Which production line has the highest defect rate?
* Which supplier has the highest defect rate?
* Which shift shows higher defect levels?
* What is the overall quality percentage?

### Battery Performance

* How does capacity vary across production lines?
* Is ambient temperature associated with capacity?
* How does internal resistance relate to capacity?
* How does electrolyte volume relate to capacity?
* How does retention vary across QC grades?

### Defect Analysis

* Which defect types occur most frequently?
* Which production line has the highest number of defective units?
* Which suppliers are associated with higher defect rates?
* Which combinations of line, shift, supplier, and defect type contribute most to defective production?

---

# 📈 Project Workflow

```text
Raw EV Battery QC Dataset
          ↓
     Data Cleaning
          ↓
      Power Query
          ↓
 Data Transformation
          ↓
      DAX Measures
          ↓
   Data Modeling
          ↓
  Interactive Visualizations
          ↓
  3-Page Power BI Dashboard
          ↓
Production & Quality Insights
```

---

---

# 🚀 Skills Demonstrated

### Power BI

* Dashboard Development
* Interactive Report Design
* KPI Development
* Data Visualization
* Slicers & Filters
* Page Navigation
* Drill-down Analysis
* Decomposition Tree
* Key Influencers
* Scatter Plot Analysis
* Conditional Formatting

### DAX

* `DISTINCTCOUNT`
* `CALCULATE`
* `DIVIDE`
* Filter Context
* KPI Measure Creation

### Power Query

* Data Cleaning
* Data Transformation
* Data Type Management
* Data Preparation

### Data Analytics

* Production Analysis
* Quality Analysis
* Defect Analysis
* Supplier Analysis
* Shift Analysis
* Process Parameter Analysis
* Manufacturing Performance Analysis

---

# 💡 Key Takeaway

This project demonstrates how Power BI can transform detailed **EV battery manufacturing and QC data** into an interactive analytical solution.

Instead of focusing only on production volume, the dashboard combines:

**Production → Process Parameters → Quality → Defects → Root-Cause Analysis**

This provides a complete view of manufacturing performance and helps identify areas that may require further investigation.

---

# 👨‍💻 Project Author

**Rohith K Mohan**

**Data Analytics | Power BI | Tableau | Excel | Python**

---

## ⭐ Project Highlights

> **20,000+ Battery QC Records | 3 Interactive Dashboard Pages | 5 DAX Measures | Power Query | Advanced Power BI Analytics**
