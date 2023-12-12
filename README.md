# HR Attrition Analysis PowerBI

## Table of Contents

### Project Overview
This data analysis project aims to provide valuable insights to the Organisation on reducing Attrition Rates and suggest some Actionable 
recommendations to improve better work Environment.  

#### Data Sources
Employee data: The primary dataset is in CSV file "Hr-Employee-Attrition.csv" containing Employee Details of the Organisation

### Objective
- The organization is currently experiencing a period of increased employee turnover.
- In response, the organization has systematically gathered crucial information through employee feedback and exit interviews.
- My role involves analyzing this data comprehensively to identify patterns and reasons behind the heightened attrition rate.
- The objectives include providing insights on attrition rates by department, job role, and gender, understanding the reasons for attrition,
  identifying contributing factors, and suggesting actionable recommendations to reduce the attrition rate and enhance the work environment.

### Methodology

### Data Cleaning/Preparation:
In the initial Data Preparation, we performed the following Tasks:
1. Data Loading and Inspection.
2. Handling Missing Values & Removing Duplicates Values and Removing Redundant Column
3. Data Transformation step like Changed Datatypes for necessary columns.

### Data Modelling
Since There is only one table containing all information, data modelling process included creating Key Measures and Calculated columns for Analysis.

Name:[Hr-Employee-Attrition.csv]

Table: HR-Employee-Attrition

#### Columns:
- Age	
- Attrition	
- BusinessTravel	
- DailyRate	
- Department	
- DistanceFromHome	
- Education	
- EducationField	
- EmployeeCount	
- EmployeeNumber	
- EnvironmentSatisfaction
- Gender	
- HourlyRate	
- JobInvolvement	
- JobLevel	
- JobRole
- JobSatisfaction	
- MaritalStatus	
- MonthlyIncome
- MonthlyRate	
- NumCompaniesWorked	
- Over18	
- OverTime	
- PercentSalaryHike	
- PerformanceRating	
- RelationshipSatisfaction	
- StandardHours	
- StockOptionLevel	
- TotalWorkingYears	
- TrainingTimesLastYear	
- WorkLifeBalance	
- YearsAtCompany	
- YearsInCurrentRole	
- YearsSinceLastPromotion
- YearsWithCurrManager

...
Measures:

TotalEmployees = COUNTROWS(EmployeeData)
AverageSalary = AVERAGE(EmployeeData[Salary])
...
Calculated Columns:

YearsOfService = DATEDIFF(EmployeeData[JoinDate], TODAY(), YEAR
Developed various visuals such as Bar Charts, Line Charts, Funnel Charts, Donut Charts, Stacked Bar Charts, Clustered Bar Charts, and Gauge visuals for the Dashboards.
Implemented Slicers for filtering insights by Attrition, Department, Gender, and Job Role.
Tools Used:

PowerBI Desktop - For Analysis
MS PowerPoint - For Presentation
Screenpresso - For Video Presentation




Dataset: CSV File containing Employee details and Ratings based on Feedbacks.

