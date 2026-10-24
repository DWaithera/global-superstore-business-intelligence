# Global Superstore | Business Intelligence & Commercial Analytics

**Power BI · DAX · Power Query · Sales Performance · Profitability Analysis**

An end-to-end Business Intelligence project exploring commercial performance through sales trends, product profitability, geographic markets, and customer segments. The project demonstrates how transactional data can be transformed into reliable performance measures, interactive dashboards, and evidence-based business recommendations.

---

## 1. Business Problem

Revenue alone does not provide a complete picture of commercial performance. A business may generate substantial sales while experiencing differences in profitability across products, markets, and customer segments.

The challenge is to turn transactional records into a consistent view of performance that helps management distinguish revenue contribution from profitability and identify areas requiring further investigation.

I developed this Power BI solution to answer five questions:

- How do sales and profit change over time?
- Which categories, regions, and customer segments contribute most to sales?
- Where do revenue contribution and profitability differ?
- Which products and sub-categories warrant closer examination?
- What should management investigate to improve commercial decision-making?

**Objective:** Build an interactive business intelligence solution that connects reliable KPI calculations with commercially relevant analysis.

## 2. Dashboard Overview

The dashboard is organised into three pages, each designed around a different management perspective.

### Executive Performance

Provides a consolidated view of Total Sales, Total Profit, Total Orders, Average Order Value, and Profit Margin. Supporting visuals examine performance over time, regional revenue contribution, category performance, and customer-segment revenue mix.

**Business application:** Monitor commercial performance and identify areas requiring deeper analysis.

### Profitability & Product Intelligence

Examines sub-category profitability, revenue contribution, high- and low-profit products, discount patterns, and product-level performance using sales, profit, quantity, and profit margin.

**Business application:** Identify products and sub-categories that warrant profitability reviews rather than relying on revenue rankings alone.

### Regional & Customer Intelligence

Explores geographic performance and compares sales and profit across customer segments using interactive filters.

**Business application:** Investigate differences across markets and customer groups to help prioritise further analysis.

### Dashboard Screenshots

Add screenshots exported from the completed Power BI report.

**Executive Performance**

![Executive Performance dashboard](screenshots/executive-performance.png)

**Profitability & Product Intelligence**

![Profitability and Product Intelligence dashboard](screenshots/profitability-product-intelligence.png)

**Regional & Customer Intelligence**

![Regional and Customer Intelligence dashboard](screenshots/regional-customer-intelligence.png)

*These image paths must match the actual filenames uploaded to the repository.*

## 3. Key Findings & Business Recommendations

The dashboard supports analysis of revenue contribution, profitability differences, product performance, and customer segments. The final published findings must be supported by verified values from the completed report.

The following are the principal analytical questions and the decisions they can inform.

| Analytical question | Evidence to evaluate | Potential business response |
|---|---|---|
| Which product categories generate the strongest commercial returns? | Sales, profit, and profit margin by category | Investigate material profitability differences and their underlying drivers |
| Where does revenue performance diverge from profitability? | Compare sales contribution with profit and margin | Prioritise areas where high revenue does not translate into comparable profitability |
| Which products warrant further investigation? | Product-level sales, profit, quantity, and margin | Review pricing, product mix, costs, or discounting where the evidence indicates a problem |
| How do commercial results differ across regions? | Regional sales and profit comparisons | Investigate material differences and identify opportunities for deeper market analysis |
| How does performance vary by customer segment? | Segment-level sales, profit, and margin | Evaluate whether segment differences warrant changes in commercial priorities |

These are analytical pathways, not claims that the underlying conditions have already been established.

**Finalisation requirement:** Before publication, replace this table with three to five quantified findings from the dashboard. Each finding should state what the data shows, provide the supporting figures, explain the business implication, and recommend an appropriate next action.

## 4. Technical Implementation

### Technology stack

| Technology | Application |
|---|---|
| Microsoft Power BI Desktop | Interactive dashboard development and analysis |
| Power Query | Data inspection, date parsing, type correction, and text cleaning |
| DAX | Reusable KPI calculations |
| Power BI visualisations | Trend analysis, contribution analysis, product comparisons, and profitability diagnostics |
| GitHub | Project documentation and portfolio publication |
| Word/PDF | Business intelligence documentation and executive reporting |

### Data preparation

The Orders dataset contains **51,290 rows and 24 columns**.

The preparation work included:

- Inspecting column types, data validity, errors, and missing values.
- Converting Order Date and Ship Date to date values using the appropriate date format and locale.
- Applying Trim and Clean transformations to selected text fields.
- Checking Row ID uniqueness and blank values.
- Investigating repeated Order IDs in the context of order-line records.
- Reviewing missing Postal Code values and retaining nulls rather than inventing replacements.

### Data quality decisions

**Order IDs:** The dataset contains multiple line items per order. I therefore used a distinct count of Order ID to measure order volume rather than treating each row as a separate order.

**Row ID:** The uniqueness check found 51,290 rows before and after duplicate removal in the separate validation query. The original dataset was preserved.

**Postal Code:** Approximately 81% of values are missing. These nulls were retained, and the limitation was documented rather than obscured through fabricated replacements.

These decisions reflect an important principle in data preparation: transformations must respect the meaning and granularity of the source records.

## 5. KPI Framework

The dashboard uses five DAX measures to maintain consistent calculations across its analytical pages.

| KPI | Definition | Business purpose |
|---|---|---|
| Total Sales | Sum of Sales | Measures recorded sales value |
| Total Profit | Sum of Profit | Measures reported profit |
| Total Orders | Distinct count of Order ID | Counts distinct orders |
| Average Order Value | Total Sales ÷ Total Orders | Measures average sales value per order |
| Profit Margin | Total Profit ÷ Total Sales | Measures reported profit relative to sales |

### DAX measures

**Total Sales**
```dax
Total Sales =
SUM('Global_Superstore2_Orders'[Sales])
```

**Total Profit**
```dax
Total Profit =
SUM('Global_Superstore2_Orders'[Profit])
```

**Total Orders**
```dax
Total Orders =
DISTINCTCOUNT('Global_Superstore2_Orders'[Order ID])
```

**Average Order Value**
```dax
Average Order Value =
DIVIDE([Total Sales], [Total Orders], 0)
```

**Profit Margin**
```dax
Profit Margin =
DIVIDE([Total Profit], [Total Sales], 0)
```

`DIVIDE` provides a defined result when the denominator is zero. Profit Margin is formatted as a percentage in Power BI.

## 6. Analytical Methodology

The project follows a structured business intelligence workflow:

1. **Business understanding:** Define the commercial questions and decisions the analysis should support.
2. **Data inspection:** Examine dataset structure, data types, completeness, and record identifiers.
3. **Data preparation:** Correct data types, parse dates, clean selected text fields, and document quality issues.
4. **KPI development:** Implement reusable DAX measures for consistent performance calculations.
5. **Exploratory analysis:** Compare sales, profit, and margin across relevant commercial dimensions.
6. **Dashboard development:** Organise visualisations into three pages aligned with management questions.
7. **Business reporting:** Document the methodology and prepare executive reporting.

An important analytical distinction is maintained throughout: observed relationships do not automatically establish causation. For example, a relationship between discount levels and profit does not prove that discounts caused a change in profitability.

## 7. Limitations & Next Steps

### Limitations

- Substantial Postal Code missingness limits the completeness of postal-level analysis.
- The analysis is primarily descriptive and does not establish causal relationships.
- Findings describe the available dataset and should not automatically be generalised to other businesses or periods.
- Business recommendations require validated figures and appropriate operational context.

### Next steps

- Validate headline KPI values and quantified findings against the final dashboard.
- Complete the executive report with evidence-backed insights and recommendations.
- Export and publish the three dashboard screenshots.
- Add KPI definitions and data preparation documentation.
- Verify repository paths, filenames, and instructions for accessing the project.
- Investigate opportunities for more repeatable data validation and reporting.

## 8. Repository Contents

The repository will contain the following artefacts as they are finalised:

```text
global-superstore-business-intelligence/
│
├── README.md
├── dashboard/
│   ├── Global_Superstore_Dashboard.pbix
│   └── exports/
├── reports/
│   ├── BI_Overview_Report.pdf
│   └── Executive_Report.docx
├── documentation/
│   ├── KPI_definitions.md
│   ├── data_preparation.md
│   └── data_dictionary.md
└── screenshots/
    ├── executive-performance.png
    ├── profitability-product-intelligence.png
    └── regional-customer-intelligence.png
```

The final structure must match the files actually committed to GitHub.

### Accessing the project

**Requirements:** Microsoft Power BI Desktop and access to the underlying dataset.

1. Download the published `.pbix` file.
2. Open it in Power BI Desktop.
3. Explore the three dashboard pages and available filters.
4. Refer to the BI Overview Report for the methodology and KPI definitions.
5. Refer to the Executive Report for validated findings and recommendations.

The source dataset is not included by default. Anyone reproducing the analysis must obtain it through an appropriate permitted source and configure the Power BI file accordingly.


## 9. Author

**Damaris Waithera**  
*Business Intelligence & Data Analytics*

I am interested in using data to solve practical business problems, improve performance visibility, and support better commercial decisions.

My focus includes business intelligence, sales and revenue analytics, product performance, and customer insights.

I approach analytics as a combination of technical execution and business reasoning: understanding the question, preparing reliable data, developing appropriate measures, validating the evidence, and communicating findings in a form that supports decisions.
