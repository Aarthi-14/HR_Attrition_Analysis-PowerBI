# HR Attrition Analysis-PowerBI Project

## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Objective](#objective)
- [Methodology](#methodology)
  - [Data Cleaning/Preparation](#data-cleaning/preparation)
  - [Data Modelling](#data-modelling)
      - [Columns](#columns)
      - [Key Measures](#key-measures)
      - [DAX Calculated Columns](#dax-calculated-columns)
  - [Data Visualization](#data-visualization)
      - [OverAll KPI Dashboard](#overall-kpi-dashboard)
  
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

### Data Cleaning/Preparation
In the initial Data Preparation, we performed the following Tasks:
1. Data Loading and Inspection.
2. Handling Missing Values & Removing Duplicates Values and Removing Redundant Column
3. Data Transformation step like Changed Datatypes for necessary columns.

### Data Modelling
Since There is only one table containing all information, data modelling process included creating Key Measures and Calculated columns for Analysis.

Name:[Hr-Employee-Attrition.csv]

Table: HR-Employee-Attrition

#### Columns
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


#### Key Measures
1. Attrition Count:
   - Measures the No. of employees who left the organization.
   - Formula: Attrition Count = CALCULATE(COUNTROWS('HR-Employee-Attrition'), 'HR-Employee-Attrition'[Attrition] = "Yes")
2. Total No.of Employees:
   - Measures the Total No. of Employees in the Company
   - Formula: Total No.of Employees = COUNT('HR-Employee-Attrition'[EmployeeNumber]) 
3. Attrition Rate:
   - Measures the percentage of employees who left the organization.
   - Formula: Attrition rate % = DIVIDE([Attrition Count],[Total No.of Employees],0)*100
4. Average Monthly Salary:
   - Gives the average monthly income of employees.
   - Formula: AVERAGE_Monthly_SALARY = CALCULATE(AVERAGE('HR-Employee-Attrition'[MonthlyIncome]))
5. Average Tenure at the Current Role:
   - Calculates the average number of years departing employees spent at the company.
   - Formula: Average_Tenure_at_currentRole = CALCULATE(AVERAGE('HR-Employee-Attrition'[YearsInCurrentRole]))
6. Average Age of the Employees:
   - Provides the average age of employees who have left the organization
   - Formula: AVG_Age = CALCULATE(VALUE(AVERAGE(('HR-Employee-Attrition'[Age]))))
7. Average Distance From Home:
   - Indicates the average distance from home for employees.
   - Formula: AVG_Distance_from_Home = CALCULATE(AVERAGE('HR-Employee-Attrition'[DistanceFromHome]))
8. Average Percentage Hike:
   - Provides the average percentage hike given to the Employees.
   - Formula: Avg_Perc_Hike = CALCULATE(AVERAGE('HR-Employee-Attrition'[PercentSalaryHike]))
9. Average Monthly Rate:
    - Measures the Average rate fixed by the company.
    - Formula: AVG_Rate = CALCULATE(AVERAGE('HR-Employee-Attrition'[MonthlyRate]))
10. Average Tenure at the Company:
    - Measures the Average Tenure of the Employees at the company.
    - Formula: AVG_Tenure_at_the_Company = CALCULATE(AVERAGE('HR-Employee-Attrition'[YearsAtCompany]))
11. Average Tenute since Last Promotion:
    - Measures the Average Tenure of the Employees since Last Promotion
    - Formula: AVG_Tenure_since_LastPromotion = CALCULATE(AVERAGE('HR-Employee-Attrition'[YearsSinceLastPromotion]))
12. Average Work-Life Balance:
    - Indicates the average work-life balance satisfaction of departing employees.
    - Formula: AVG_WorkLife_Balance = CALCULATE(AVERAGE('HR-Employee-Attrition'[WorkLifeBalance]),
                                                'HR-Employee-Attrition'[Attrition] = "Yes")
13. Environment Satisfaction Index:
    - Represents the average level of satisfaction with the work environment.
    - Formula: Environment_Satisfaction_Index = CALCULATE(AVERAGE('HR-Employee-Attrition'[EnvironmentSatisfaction]))
14. Job Involvement Index:
    - Represents the average level of job involvement among employees.
    - Formula: Job_Involvement_Index = CALCULATE(AVERAGE('HR-Employee-Attrition'[JobInvolvement]))
15. Job Satisfaction Index:
    - Represents the average level of job satisfaction among employees.
    - Formula: Job_Satisfaction_Index = CALCULATE(AVERAGE('HR-Employee-Attrition'[JobSatisfaction]))
16. Managerial Change Rate:
    - Measures the percentage of employees who recently changed managers.
    - Formula: Managerial_Change_Rate = COUNTROWS(FILTER('HR-Employee-Attrition', 'HR-Employee-Attrition'[YearsWithCurrManager] = 0)) / COUNTROWS('HR-Employee-Attrition')
17. OverTime Rate:
    - Indicates the percentage of departing employees who worked overtime.
    - Formula: OverTime_Rate = DIVIDE(
                          COUNTROWS(FILTER('HR-Employee-Attrition', 'HR-Employee-Attrition'[OverTime_New] = 1)),
                          [Total No.of Employees],0) * 100
18. Performance Rating Index:
    - Analyzes the distribution of performance ratings.
    - Formula: Performane_Rating_Index = AVERAGE('HR-Employee-Attrition'[PerformanceRating])
19. Ralationship Satisfaction Index:
    - Represents the average level of relationship satisfaction among employees.
    - Formula: Relationship_Satis_Index = CALCULATE(AVERAGE('HR-Employee-Attrition'[RelationshipSatisfaction]))
20. Training Rate:
    - Measures the percentage of employees who underwent training.
    - Formula: Training_Rate = DIVIDE(sum('HR-Employee-Attrition'[TrainingTimesLastYear]), [Attrition Count], 0) *100


#### DAX Calculated Columns

1. Age Category:
   - Purpose: Categorizes employees into specific age groups for demographic analysis.
   - Formula: Age_Category = SWITCH(
                      TRUE(),
                      VALUE('HR-Employee-Attrition'[Age]) < 30, "BELOW 30",
                      AND(VALUE('HR-Employee-Attrition'[Age]) >= 30, VALUE('HR-Employee-Attrition'[Age]) <= 40), "30-40",
                      VALUE('HR-Employee-Attrition'[Age]) > 40, "ABOVE 40",
                      BLANK())
   - Description: The Age Category DAX column uses the SWITCH function to categorize employees into different age groups based on their age.

2. Distance from Home:
   - Purpose: Categorizes employees based on the distance of their home from the workplace. 
   - Distancefromhom = SWITCH(
                          TRUE(),
                          VALUE('HR-Employee-Attrition'[DistanceFromHome]) < 10, "< 10 km",
                          AND(VALUE('HR-Employee-Attrition'[DistanceFromHome])>= 10, VALUE('HR-Employee-Attrition'[DistanceFromHome]) <= 20), "10 -20 km",
                          VALUE('HR-Employee-Attrition'[DistanceFromHome]) > 20, "20-30 km",
                          BLANK())
   - Description: The DistanceFromHome Category DAX column categorizes employees based on the distance (in kilometers) from their home to the workplace using the SWITCH function

### Data Visualization
Introduction:
Visualizations play a crucial role in translating raw data into actionable insights. In this section, we will explore the key visualizations used to analyze HR attrition trends.

Key Visualizations:
1. OverAll KPI Dashboard
2. Company's Perspective Dashboard
3. Workforce Analysis Dashboard
4. Employee Wellness Dashboard

## Key Insights
     1. Out of 1470 Total Employees, 237 is the Attrition Count which estimates 16.12 % Attrition Rate.
     2. R&D Department has the Highest Attrition Count of 133, followed by Sales Department with 92 Attrition count.
     3. Attrition by Gender gives an Insight that out of 237 Employees, 150 are the Male Employees and 87 are the Female Employees.
     4. Lab Technician is the Job Role which has Highest Attrition count of 62 by Job Role.
     
#### OverAll KPI Dashboard
This dashboard presents a comprehensive view of overall attrition trends. 
- Key metrics include Attrition Rate, Total Employees, Attrition Count and Attrition count by Department/Job Role/Gender/Age Category/Education.
- Users can Interact with Visualization such as slicers for Gender/Department/Job Role.

![overallkpi](https://github.com/Aarthi-14/HR_Attrition_Analysis-PowerBI/assets/147639053/39fada9b-2ccd-4198-839a-fc6d9df6684f)   
 



 1. Attrition count by Department:
    - Used Funnel Chart for this visualization that gives attrition trends by department.
  
      ![Attritionbydept](https://github.com/Aarthi-14/HR_Attrition_Analysis-PowerBI/assets/147639053/326d6a9f-9e4b-4351-b25c-7369a8d4f4a5)
 
 2. Attrition by Job Role:
    - Used Clustered column Chart for this visualization that gives attrition trends by Job Role.
  
      ![attritionbyjobrole](https://github.com/Aarthi-14/HR_Attrition_Analysis-PowerBI/assets/147639053/4c9bca1b-83ee-4286-b2f0-b21c8acac31f)
 
 3. Attrition by Gender:
    - Used Donut Chart for this visualization that gives attrition count by Gender.

      ![attrition by gender](https://github.com/Aarthi-14/HR_Attrition_Analysis-PowerBI/assets/147639053/48a008b6-30fb-4f40-96ac-19978aa735ef)

4. Attrition by Age Category:
    - Used Donut Chart for this visualization that gives attrition count by Age Category.
    - Created Calculated DAX column for Age category.
  
      ![attrition by age](https://github.com/Aarthi-14/HR_Attrition_Analysis-PowerBI/assets/147639053/b7ef8e66-85c6-40f8-8fc3-51db87867059)

Implemented Slicers for filtering insights by Attrition, Department, Gender, and Job Role.
Tools Used:

PowerBI Desktop - For Analysis
MS PowerPoint - For Presentation
Screenpresso - For Video Presentation




Dataset: CSV File containing Employee details and Ratings based on Feedbacks.

