# Global STI Health Risk Analysis | Power BI Dashboard

An interactive Power BI dashboard developed to analyze global Sexually Transmitted Infection (STI) trends across 34 countries, 5 diseases, and 200,000 records spanning 2015 to 2025.

The dashboard combines KPI monitoring, disease distribution analysis, demographic breakdowns, geographic visualization, treatment trend tracking, and business insight generation through dynamic slicers and interactive charts.

<img width="800" height="450" alt="VideoProject211-ezgif com-video-to-gif-converter" src="https://github.com/user-attachments/assets/73c5118e-cf1e-485b-80fd-3fcd5767ca9d" />



## Project Structure

The project consists of the following components:

### Power BI Dashboard

The main reporting page that presents key metrics, charts, maps, and business insights in a single view. Users can interact with slicers to explore different segments of the data by country, disease, gender, and age group.

### Dataset

A 200,000-row synthetic dataset engineered using real-world WHO and UNAIDS statistical parameters. It contains country-level epidemiological data covering disease cases, deaths, treatment coverage, vaccination rates, and incidence rates across multiple demographic segments.

---

## KPI Overview

The dashboard presents five key health metrics that provide a quick snapshot of the global STI burden. All KPI cards update dynamically based on the selected filters, enabling focused analysis across different countries, diseases, and time periods.

<img width="265" height="717" alt="image" src="https://github.com/user-attachments/assets/5a70dfa5-4273-4221-b61e-9dcd87159e39" />  

| KPI | Description |
|---|---|
| Total Cases | Total number of STI cases recorded across all selected filters |
| Total Deaths | Total number of deaths attributed to STIs in the selected period |
| Avg Treatment Coverage | Average percentage of cases receiving active treatment |
| Top Region | The region carrying the highest STI case burden |
| Top Country | The country with the highest total STI case count |

### Current Dashboard Summary

Based on the complete dataset:

- **Total Cases:** 4.51 Billion
- **Total Deaths:** 14.62 Million
- **Avg Treatment Coverage:** 71.14%
- **Top Region:** Asia
- **Top Country:** China

These metrics serve as the foundation for evaluating global disease burden, treatment gaps, and healthcare delivery performance across regions.

---

## Charts & Visualizations

<img width="1188" height="720" alt="image" src="https://github.com/user-attachments/assets/a3f4e786-8fff-40d3-a3be-01fc19dbaf9d" />


### Cases & Death Trends

Tracks the number of new cases and deaths over time from 2015 to 2025. The chart highlights the COVID-19 shock period (2020–2021) where testing dropped globally, followed by a post-COVID surge in 2022–2023. This dual-line trend allows direct comparison of case trajectory against mortality patterns over the decade.

### Disease Distribution (Donut Chart)

Shows the percentage breakdown of total cases across all five diseases. Hepatitis B and HPV dominate with 44.8% and 43.1% respectively, while HIV/AIDs, Chlamydia, and Syphilis account for the remaining share. This gives an immediate visual of which diseases carry the highest global burden.

### Global Disease Distribution (Shape Map)

Visualizes the geographic spread of STI cases across 34 countries worldwide. Countries are shaded by total case volume, making high-burden regions immediately identifiable. Asia and Africa stand out as the most heavily affected areas globally.

### Cases by Gender & Disease (Clustered Bar Chart)

Compares male and female case counts across all five diseases side by side. The chart reveals that Hepatitis B and HPV carry a near-equal gender burden, while HIV/AIDs cases skew slightly male. This demographic breakdown helps identify gender-specific health intervention priorities.

### Cases by Age Group (Horizontal Bar Chart)

Displays the total case burden split across three age groups: 15–24, 25–49, and 50+. The 25–49 working-age group carries the highest burden at 1.70 billion cases, making it the most critical target demographic for health screening and intervention programmes.

### Incidence Rate by Region (Bar Chart)

Ranks all five global regions by their total incidence rate. Europe and Asia lead with 10.6M and 10.1M respectively, followed closely by Africa and the Americas. Oceania records the lowest incidence rate across all regions.

---

### Key Findings from the Dashboard

- Asia accounts for 64% of all global STI cases at 2.92 billion, driven primarily by China and India.
- Hepatitis B is responsible for 70.1% of all STI-related deaths despite having an available vaccine.
- HIV/AIDs, Syphilis, and Chlamydia have zero approved vaccine coverage globally, leaving 544 million+ cases with no immunisation solution.
- The 25–49 age group carries 37% of the total global disease burden at 1.70 billion cases.
- Global treatment coverage has shown no meaningful improvement over 10 years, remaining flat at 71.14%.
- China records the highest country-level case count at 1.19 billion, followed by India at 938 million.

---

## Interactive Filters

The dashboard includes dynamic slicers that allow users to explore health data from different perspectives. All charts, KPI cards, and maps update instantly based on the selected filters.

### Country Filter

<img width="718" height="92" alt="image" src="https://github.com/user-attachments/assets/97ef7a87-293a-4ce4-ad2f-d8146dae4d6d" />

Enables country-level analysis by filtering the dashboard to specific nations. Users can compare disease burden, treatment coverage, and demographic patterns across 34 countries spanning every global region.

### Dynamic Cross-Filtering

All dashboard visuals are fully interconnected. Any filter selection automatically updates:

- All KPI Cards (Total Cases, Total Deaths, Avg Treatment, Top Region, Top Country)
- Cases & Death Trends Line Chart
- Disease Distribution Donut Chart
- Global Disease Distribution Map
- Cases by Gender & Disease Bar Chart
- Cases by Age Group Bar Chart
- Incidence Rate by Region Bar Chart
- Treatment Coverage Trend
- Key Business Insights Text Panel

---

## Dataset Engineering

### Why a Synthetic Dataset?

Raw public data from the World Health Organization and UNAIDS is highly aggregated — typically providing one summary value per country per year. To build a truly interactive dashboard with drill-downs for age, gender, region, and disease over 11 years, a granular transactional dataset was required. Since real patient-level clinical data is restricted due to privacy regulations, a Python-based simulation engine was built to generate a mathematically realistic synthetic dataset.

### Phase 1 — WHO & UNAIDS Ground Truth Parameters

The simulation was not built on random numbers. The foundation was built using actual global health statistics sourced from the WHO Global Health Observatory (incidence and prevalence rates for each STI), UNAIDS (regional HIV prevalence multipliers and treatment coverage benchmarks), and World Bank population data (real 2020 base populations for all 34 countries across every region).

### Phase 2 — Python Data Engineering Pipeline

Using Python with Pandas and NumPy, an algorithm was written to simulate epidemiological data across 11 years (2015–2025). The pipeline included demographic stratification splitting national populations into Male/Female and three age groups (15–24, 25–49, 50+), disease-specific medical rules ensuring deaths and case fatality rates respected real-world patterns, and treatment-linked mortality where regions with lower treatment coverage automatically produced higher death rates.

### Phase 3 — Real-World Volatility

To prevent the dataset from producing flat, unrealistic trend lines, real-world volatility was engineered into the data. A COVID-19 shock was programmed for 2020–2021 simulating global testing drops and strained health systems, followed by a post-COVID surge in 2022–2023. Cases and deaths were given independent volatility curves, allowing Power BI to render accurate cross-over trend patterns rather than overlapping flat lines.

### Phase 4 — Scaling to 200,000 Records

To test enterprise-scale dashboard performance, a Reporting Batch methodology was applied. National demographic data was fractured into smaller simulated regional clinic batches across multiple rows. This expanded the dataset to exactly 200,000 transactional records. When Power BI applies SUM aggregation to these rows, it correctly rolls up to medically accurate national and global totals of 4.51 billion tracked cases and 14.62 million deaths over the decade.

---

## Tools & Techniques Used

- **Power BI Desktop** — Dashboard development, visualizations, KPI cards, slicers, shape maps
- **Power Query** — Data import, type conversion, ETL transformation pipeline
- **DAX (Data Analysis Expressions)** — Custom measures for Total Cases, Total Deaths, Avg Treatment Coverage, Top Region, Top Country using SUM(), AVERAGE(), TOPN(), SUMMARIZE(), MAXX(), VAR, and RETURN
- **Python (Pandas & NumPy)** — Synthetic dataset generation, demographic stratification, statistical simulation, COVID-19 volatility modelling
- **Excel** — Data cleaning, validation, duplicate checking, column formatting, CSV export
- **WHO Global Health Observatory** — Source parameters for incidence and prevalence rates
- **UNAIDS** — Regional HIV multipliers and treatment coverage benchmarks
- **World Bank** — Country-level population data

---

## Key Business Insights

### Highest Disease Burden Region

Asia records the highest STI burden globally with 2.92 billion cases, representing 64% of the worldwide total. This positions Asia — particularly China and India — as the largest addressable market for diagnostics, mobile health platforms, and public health intervention programmes.

### Critical Mortality Gap

Hepatitis B accounts for 70.1% of all STI-related deaths at 10.26 million fatalities, despite having an approved vaccine. Antiviral access and treatment delivery infrastructure remain a critical unmet need, particularly across lower-income regions in Asia and Africa.

### Vaccine Coverage Gap

HIV/AIDs, Syphilis, and Chlamydia collectively account for over 544 million cases globally with zero approved vaccine coverage. This represents a significant and largely unaddressed pharmaceutical research and development opportunity.

### Stagnant Treatment Coverage

Average global treatment coverage has remained flat at approximately 71% for the entire decade from 2015 to 2025. This decade-long stagnation indicates persistent systemic gaps in healthcare infrastructure, supply chain delivery, and access to medicines that remain unresolved.

### Working-Age Population Burden

The 25–49 age group carries 37% of the total global STI burden at 1.70 billion cases. This working-age concentration creates a strong business case for employer-sponsored health screening programmes and corporate wellness partnerships as a B2B healthcare delivery model.

---

## Skills Demonstrated

- Data Cleaning and Validation
- Synthetic Data Engineering
- Python Data Simulation
- Power BI Dashboard Development
- Power Query ETL
- DAX Measure Creation
- KPI Design and Tracking
- Geographic Data Visualization
- Demographic Analysis
- Healthcare Domain Analytics
- Business Intelligence Reporting
- Dashboard Storytelling
- Interactive Report Design

---

## Author

Soumyaditya Naskar
