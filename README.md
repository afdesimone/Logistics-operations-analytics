# Truck Logistics Operations & Driver Performance Analysis

## Project Overview
This project analyzes driver-level performance within a simulated truck logistics operation to understand how much variation in outcomes is driven by individual drivers versus system-level factors such as routing, dispatching, and standardized execution.

---

## Data Source
This project uses the *Logistics Operations Database* sourced from Kaggle:

🔗 https://www.kaggle.com/datasets/yogape/logistics-operations-database/data

The original dataset contains 14 CSV files representing operational tables such as drivers, trips, loads, safety incidents, fuel purchases, and maintenance records. These CSVs were imported into SQLite and cleaned to build the relational model used for analysis.

---

## Key Questions
- How consistent are driver performance metrics across the fleet?
- Do efficiency and reliability exhibit meaningful trade-offs?
- Does driver experience materially affect outcomes?
- Are revenue differences driven by performance or by scale of activity?

---

## Tools & Technologies
- **Database:** SQLite  
- **SQL Environment:** DBeaver  
- **Visualization:** Power BI  
- **Data Modeling:** Relational schema with aggregate performance views

---

## Data Exploration & Modeling Approach
Before defining the relational schema, I performed an initial exploratory review of the raw CSV files to understand table grain, id columns, and column-level data types. This step was used to identify natural keys, potential foreign key relationships, and aggregation levels across tables.

Based on this inspection, I designed the SQLite schema explicitly in SQL, rather than relying on auto-detected relationships inside a BI tool.

---

## Database Design
The schema includes dimension tables for customers, facilities, routes, drivers, trailers, and trucks along with fact tables capturing trips, loads, delivery events, fuel purchases, maintenance records, safety incidents, driver monthly metrics, and truck utilization metrics.

Two SQL views are created to support analytics and reporting:
- **Driver Performance Summary** (one row per driver)
- **Driver Monthly Performance** (one row per driver per month)

These views were created to reduce transformation logic inside Power BI and keep data transformations as upstream as possible.

---

## SQL Workflow

1. **Schema Creation**  
   Tables, relationships, and constraints are defined.

2. **Data Cleaning**  
   Invalid records are removed and boolean fields are standardized.

3. **Sanity Checks**  
   Row counts, key uniqueness, foreign key integrity, and numeric ranges are validated.

4. **Ad-Hoc Analysis**  
   Business-focused queries answer questions around revenue, trips, efficiency, and experience.

5. **View Creation**  
   Clean, analysis-ready datasets are produced for BI consumption.
   
---

## Power BI Report
The Power BI report focuses on **distribution and consistency**, rather than time-series trends.

Key elements include:
- Scatter plots showing relationships between trips, miles driven, fuel efficiency, and on-time delivery
- Histograms illustrating how driver KPIs cluster tightly around fleet averages
- Comparisons of revenue across experience levels

The overall takeaway is that **driver-level metrics exhibit limited dispersion**, suggesting outcomes are largely driven by system design rather than individual optimization.

---

## How to Use This Project

### Viewing the Analysis
- Open the Power BI `.pbix` file to explore the report and visuals.
- Screenshots of representative SQL outputs are included for reference.

### Reviewing the SQL Work
- The SQL scripts are fully readable and runnable in order.
- They are designed to clearly show schema design, data validation, and analytical logic.

> The SQLite database file is not included due to GitHub file size limits.  
> Reviewers are **not expected to rebuild or reload the database** to evaluate the project.

---

## Key Takeaways
- Driver performance metrics are tightly clustered across the fleet
- Efficiency and reliability do not show strong trade-offs
- Experience has limited impact on aggregate outcomes
- Results point toward centralized planning and standardized execution

---

## Future Work
Planned extensions of this project include:
- System-level analysis of routes, network efficiency, and utilization
- Incorporating additional operational tables into the analytical views
- Connecting multiple Power BI reports into a centralized operational dashboard
- Migrating the database to PostgreSQL for scalability

---

## Author
**Anthony Desimone**  
🔗 www.linkedin.com/in/anthonyfdesimone

Data Analytics | SQL | Power BI | Data Modeling
