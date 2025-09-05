📊 U.S. Leading Causes of Death (1999–2017) – Power BI Dashboard
📝 Overview

This Power BI project analyzes the leading causes of death in the United States from 1999–2018 using CDC/NCHS data. It explores national trends, state-by-state differences, and comparisons to the national average with interactive dashboards.

📂 Dataset

Source: CDC/NCHS, National Vital Statistics System

Data includes:

Cause of death (ICD-10)

Age-adjusted death rate (per 100,000, 2000 U.S. std. population)

State

Year

Death counts

🛠️ Tools

Power BI (Dashboard & DAX modeling)

DAX (Custom calculations)

Excel (Dataset preprocessing)

🧮 Key DAX Measures

Here are the main custom measures used in the report:

📌 Core Measures
`Total Deaths =
SUM('NCHS_-_Leading_Causes_of_Death_'[Deaths])`


Calculates the total number of deaths.

`(State) Average Age-Adjusted Death Rate =
AVERAGE('NCHS_-_Leading_Causes_of_Death_'[Age-adjusted Death Rate])`


Computes the state-level average age-adjusted death rate.

`(National) Average Age-Adjusted Death Rate =
CALCULATE(
    AVERAGE('NCHS_-_Leading_Causes_of_Death_'[Age-adjusted Death Rate]),
    ALL('NCHS_-_Leading_Causes_of_Death_'[State])
)`


Computes the national average, ignoring state filters.

📌 Comparative Measures
`% Difference from National =
DIVIDE(
    [(State) Average Age-Adjusted Death Rate] - [(National) Average Age-Adjusted Death Rate],
    [(National) Average Age-Adjusted Death Rate]
)`


Shows how much higher/lower a state’s death rate is compared to the national average.

`State Rank by Year and Cause =
RANKX(
    FILTER(
        ALL('NCHS_-_Leading_Causes_of_Death_'[State]),
        'NCHS_-_Leading_Causes_of_Death_'[Year] = MAX('NCHS_-_Leading_Causes_of_Death_'[Year]) &&
        'NCHS_-_Leading_Causes_of_Death_'[Cause Name] = MAX('NCHS_-_Leading_Causes_of_Death_'[Cause Name])
    ),
    [(State) Average Age-Adjusted Death Rate],
    ,
    DESC,
    DENSE
)`


Ranks states by death rate within a given year and cause.

📊 Dashboard Features

National Trends: Age-adjusted death rates over time by cause.

State-Level Insights: Top 5 and Bottom 5 states by cause and year.

Map Visuals: Geographic disparities in death rates.

Interactive Slicers: Filter by year, cause, and state.

Dynamic KPIs: Total deaths, national averages, differences, and ranks.


✅ Future Improvements

Add demographic breakdown (sex, race, age groups).

Create cumulative death counts visualization.

Publish interactive version with Power BI Service / Embedded.


<img width="1322" height="741" alt="image" src="https://github.com/user-attachments/assets/de69973b-4d19-4afd-82fa-084fceda9c10" />
<img width="1306" height="731" alt="image" src="https://github.com/user-attachments/assets/a12663f9-e735-48de-8aca-b8b78ec12011" />






