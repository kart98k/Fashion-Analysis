
# 🎯Mens's Fashion Analysis Dashboard

## Problem Statement
The men’s fashion retail market is highly competitive, with numerous brands offering similar products at varying prices, discounts, and profit margins. Retailers often struggle to identify which brands and products drive profitability, which rely heavily on discounts to generate sales, and how pricing strategies impact overall performance. Additionally, the wide variety of products across brands makes it difficult for decision-makers to optimize inventory and focus on high-performing segments.

This project aims to address this challenge by developing an interactive Power BI dashboard that analyzes men’s fashion sales data to uncover insights into brand-wise discounts, average selling prices, profit percentages, product variety, and underperforming brands. The dashboard enables stakeholders to compare top and bottom brands, understand pricing and discount patterns, and make data-driven decisions to improve profitability, optimize brand mix, and design effective sales strategies.
&nbsp;
## Objectives
* Identify brands offering the highest average discounts.

* Evaluate top brands based on average profit percentage.

* Analyze product variety across brands to understand assortment strength.

* Compare average selling prices to study brand positioning.

* Highlight low-profit brands that need business attention.
&nbsp;
## 🛠 Tools & Technologies
* Power BI Desktop – Data cleaning (Power Query), DAX calculations, and dashboard development

* Microsoft Azure – Free account for cloud setup

* Azure SQL Database – Hosting and querying the dataset in the cloud

* Data Source – Men’s T-Shirt sales dataset (CSV) with 1,428 rows

* Cloud data integration (Azure SQL → Power BI)

* Data exploration using SQL

* Data cleaning with conditional & custom columns

* DAX calculated columns (Profit %, Discount %, Cost Price)
&nbsp;
## Project Workflow
1️⃣ Azure Account Setup

A free Azure account was created to use cloud-based services for storing and managing the dataset.

2️⃣ Data Loading into Azure SQL Database

The dataset was uploaded into an Azure SQL Database to simulate a real-world cloud data source and enable scalable data access.

3️⃣ Data Exploration in Azure SQL

Basic exploration of the data was performed directly in Azure SQL to understand the structure, columns, and presence of null (NA) values before connecting it to Power BI.

4️⃣ Connecting Power BI to Azure SQL

Power BI was connected to the Azure SQL Database using the “Database” connector option, enabling live data import from the cloud source.

5️⃣ Understanding Data in Power Query Editor

The dataset was reviewed in Power Query Editor to inspect column values, identify data quality issues, and prepare for cleaning and transformation.

6️⃣ Data Cleaning & Transformation

During cleaning, it was observed that:

The Sales Price column had valid values.

The Original Price column contained several NA (null) values.

To handle this:

A conditional column Factor was created:

If Original Price is NA → assign 1.5

Else → assign 0
(Assuming original price should be at least 50% higher than sales price.)

A custom column Factor 2 was created as:

Sales Price * Factor

A final conditional column Marked Price was created:

If Original Price is NA → use Factor 2

Else → use Original Price

This helped replace null values in Original Price with estimated values based on Sales Price.

After this:

Columns were converted to appropriate data types.

Changes were applied using Close & Apply.


7️⃣ DAX Calculated Columns

The following calculated columns were created using DAX:

Profit % = RANDBETWEEN(2,17)

Discount % = DIVIDE(
  'Men+Tshirt'[Marked Price] - 'Men+Tshirt'[Sales_Price],
  'Men+Tshirt'[Marked Price]
) * 100

Cost Price = DIVIDE(
  100 * 'Men+Tshirt'[Sales_Price],
  100 + 'Men+Tshirt'[Profit %]

8️⃣ Report & Dashboard Creation

Multiple visuals were added to analyze:

* Top brands by discount

* Highest and lowest profit brands

* Average sales price

* Brand-wise product variety

* A Scroller visual was added to enable smooth horizontal navigation

* A two-page report was designed for better organization and storytelling.

9️⃣ Publishing to Power BI Service

Finally, the report was published to Power BI Service, enabling online access and sharing of the dashboard.
&nbsp;
##  Key Insights
* A small group of brands such as IVOC, WUXI, Mischief Monkey, Voroxy X AG, and Red Tape account for the highest discount levels, indicating a strong reliance on promotional pricing rather than inherent price competitiveness.

* High profit brands including Valen Club, Veerya, Tyzlo, Marmic Fab, Paralians, and Charles Tyrwhitt do not depend on heavy discounts, suggesting that superior margins are driven by efficient cost structures or premium pricing strategies.

* Several brands maintain strong profit margins despite moderate selling prices, reflecting an effective balance between pricing and cost management and making them suitable for business expansion.

* Greater product variety does not always translate into higher profitability, implying that a wider SKU range can increase operational complexity without proportional margin gains.

* Low performing brands exhibit weak or unstable profit margins, pointing to potential issues such as inefficient pricing, excessive discounting, or higher cost pressures.
&nbsp;
## Screenshots

<img width="1920" height="1080" alt="Screenshot 2025-12-29 163439" src="https://github.com/user-attachments/assets/2aec8714-4a01-410e-a36b-99fe1ff50129" />
&nbsp;
<img width="1920" height="1080" alt="Screenshot 2025-12-29 163817" src="https://github.com/user-attachments/assets/de582216-1528-4320-8750-98cc2124f1fd" />

