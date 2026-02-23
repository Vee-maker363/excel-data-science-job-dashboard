# excel-data-science-job-dashboard
An interactive Excel dashboard analysing data science roles across countries, job schedules, and salary ranges. Demonstrates advanced Excel techniques including dynamic filtering, median-based salary analysis, XLOOKUP integration, and KPI-driven visual design. 

.![dashboard_gif](https://github.com/user-attachments/assets/8d2a9958-2d68-4344-95b5-aefd7abd9c8c)


# Data Science Role Comparison Dashboard (Excel)  
## Overview  
This project presents an interactive Excel dashboard designed to compare data science roles across countries, job schedules, and salary ranges.

The dashboard enables users to dynamically explore:

- Median salary by job role

- Median salary by country

- Most-used applicant platforms

- Number of applicants under selected criteria

It is important to note that this project deliberately does not emphasise deep data cleaning or normalisation. Those processes are reserved for a later project. Here, the intention was to demonstrate how analysts can still extract meaningful insights through careful function design, structured compilation, and logical filtering, even when working with imperfect or partially standardised data. 
## Project Objective  
The primary objective was to build a decision-ready dashboard capable of answering practical labour-market questions:

- How do median salaries differ across data science roles?

- How does compensation vary by country?

- Which platforms are most frequently used by applicants?

- How does applicant volume change based on selected criteria?

All outputs are driven by three filters:

- Job Role

- Country

- Job Schedule

This structure mirrors how business users explore hiring and compensation data in real-world settings.  
# Data Compilation and the Role of Excel Functions  
The first major technical step involved compiling reference data into a dedicated sheet; for this, I named the sheet data count. This sheet acts as the backbone of the workbook, supplying clean and validated inputs to calculation sheets and the dashboard itself.
The UNIQUE function was used extensively at this stage to extract distinct values for key fields such as job titles, countries, and job schedules. This addressed the issue of repeated values in the raw dataset and provided a reliable source for dropdown selections and controlled calculations. Without this step, maintaining consistency across filters and calculations would have been significantly more difficult.  

<img width="974" height="484" alt="image" src="https://github.com/user-attachments/assets/9ead4a63-40ff-46d0-8a43-6803459933d6" />  

Once unique values were extracted, the SORT function was applied to organise the results in a meaningful way. Job titles were sorted in descending order to support ranked comparisons, while countries were sorted in ascending order to improve readability and navigation. While this may appear cosmetic, structured ordering plays an important role in clarity and usability within analytical workflows.
For the job schedule column, a more complex combination of functions was required. By combining FILTER, NOT, ISNUMBER, and SEARCH, the job schedule data was refined to better represent employment types such as full-time, part-time, and contract roles. This approach addressed inconsistencies in how schedules were recorded and ensured that downstream calculations reflected the intended categories.
In addition, a combination of COUNT and IF was introduced to dynamically count the number of job records that met all three criteria: job role, country, and job schedule. This directly supports the applicant-count KPI and demonstrates how conditional logic can be layered into summary metrics without relying solely on PivotTables.  

# Median Salary Calculations Across Criteria

After compiling the dataset, separate calculation sheets were created for job role, country, and job schedule. Initially, each sheet calculated median salary values based solely on its primary dimension — for example, median salary by job title on the role sheet and by country on the country sheet.

The MEDIAN function was deliberately selected instead of the average to reduce the impact of salary skew and outliers, which are common in compensation data. This aligns with standard labour-market analysis practice, where the median provides a more reliable representation of typical earnings.

To achieve full dashboard alignment, these calculations were later refined. Each median formula was expanded to incorporate all three criteria — job role, country, and job schedule. This ensured that salary values dynamically reflected the selected filters and that all outputs responded consistently to user input across the dashboard.  

<img width="566" height="190" alt="image" src="https://github.com/user-attachments/assets/1db4d0c5-9df7-4948-ab87-eabf93842f25" />  

# Managing Edge Cases and Calculation Errors

During country-level analysis, certain filter combinations produced **#NUM! errors** due to insufficient data for specific job role and schedule selections. Instead of concealing these issues, they were addressed explicitly using the **FILTER** and **SORT** functions to remove invalid outputs and display only meaningful results.

This approach preserves analytical transparency and reflects real-world practice, where analysts must manage sparse data carefully without compromising the integrity of the analysis.  

# Platform Analysis and KPI Logic

A dedicated sheet was created to analyse applicant platform usage, applying the same three criteria (job role, country, job schedule) used throughout the workbook. This ensured logical consistency across calculations.

The result enables identification of the most frequently used platform under selected conditions and feeds directly into the KPI section. This reinforces a key design principle: dashboard metrics should be built on consistent, reusable logic rather than isolated calculations.  

# Dashboard Construction and Interactivity

The dashboard was developed alongside the calculation logic to ensure alignment between analysis and presentation. **Data Validation** was used to create dynamic dropdown selectors populated from structured reference data, improving input accuracy and overall robustness.

A bar chart was chosen to display median salaries by job role due to its clarity in presenting ranked comparisons, especially when evaluating multiple roles simultaneously.  

<img width="939" height="603" alt="image" src="https://github.com/user-attachments/assets/2f7c555c-a6fc-4122-8dbe-a3e59b9a7101" />


