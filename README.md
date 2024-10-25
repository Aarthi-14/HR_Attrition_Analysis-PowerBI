# HR Attrition Analysis-PowerBI Project 

## Table of Contents
- [Project Overview](#project-overview) 
- [Data Sources](#data-sources)
- [Tools Used](#tools-used) 
- [Objective](#objective)
- [Methodology](#methodology)
  - [Data Cleaning and Transformation](#data-cleaning-and-transformation)
  - [Data Modelling](#data-modelling)
      - [Columns](#columns)
      - [Key Measures](#key-measures)
      - [DAX Calculated Columns](#dax-calculated-columns)
  - [Data Visualization](#data-visualization)
      - [Executive Summary](#executive-summary)
      - [Workforce Analysis](#workforce-analysis)
      - [Correlation Analysis](#correlation-analysis)
  - [Key Insights](#key-insights)
  - [Succession Planning](#succession-planning)
  - [Recommendations](#recommendations)
- [Conclusion](#conclusion)
  
### Project Overview
This data analysis project aims to provide valuable insights to the Organisation on reducing Attrition Rates and suggest some Actionable 
recommendations to improve better work Environment.  

#### Data Sources
Employee data: The primary dataset is in CSV file "Hr-Employee-Attrition.csv" containing Employee Details of the Organisation.

### Tools Used
- PowerBI Desktop : For Analysis
- MS PowerPoint : For Presentation
- Screenpresso : For Recording Video
- Canva : For Video Editing

### Objective
- The organization is currently experiencing a period of increased employee turnover.
- In response, the organization has systematically gathered crucial information through employee feedback and exit interviews.
- My role involves analyzing this data comprehensively to identify patterns and reasons behind the heightened attrition rate.
- The objectives include providing insights on attrition rates by department, job role, and gender, understanding the reasons for attrition,
  identifying contributing factors, and suggesting actionable recommendations to reduce the attrition rate and enhance the work environment.

### Methodology

### Data Cleaning and Transformation
In the initial Data Preparation, we performed the following Tasks:
1. Data Loading and Inspection.
2. Handling Missing Values & Removing Duplicates Values and Removing Redundant Column
3. Data Transformation step like Changed Datatypes for necessary columns.

### Data Modelling
Since There is only one table containing all information, data modelling process included creating Key Measures and Calculated columns for Analysis.

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
- Monthly Rate
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
1. Executive Summary
2. Workforce Analysis 
3. Correlation Analysis
     
### Executive Summary
This Page presents a comprehensive view of overall attrition trends. 
- Key metrics include Attrition Rate, Total Employees, Attrition Count and Attrition count by Department/Job Role/Gender/Age Category/Education.
- Users can Interact with Visualization by using slicers for Gender/Department/Job Role.

![Executive View](https://github.com/user-attachments/assets/a4038b3d-e636-46e2-958a-9b8fd7499e25)

 
 1. Total No. Of Employees, Attrition Count and Attrition Rate.
    - Used Card Visuals that gives the Total No. of Employees, Attrition Count and Attrition Rate.

![2024-10-25_13h08_01](https://github.com/user-attachments/assets/16291876-7a4e-40b6-81f6-f8ce9ae3c21d)

      
 2.  Attrition count by Department:
    - Used Funnel Chart for this visualization that gives attrition trends by department.
     
  ![2024-10-25_13h08_39](https://github.com/user-attachments/assets/047bd33a-747b-4273-9a59-c72b6c1c4831)

 
 4. Attrition by Job Role:
    - Used Waterfall Chart for this visualization that gives attrition count of the Employees by Job Role.

 ![2024-10-25_13h08_48](https://github.com/user-attachments/assets/78c37806-ff4e-411d-885c-7b1423fbf4ad)

 7. Attrition by Gender:
    - Used Donut Chart for this visualization that gives attrition count of the Employees by Gender.
      
![2024-10-25_13h08_16](https://github.com/user-attachments/assets/fe9db66f-095d-4a7a-9b8e-73ef25757297)


8. Attrition by Age Category:
    - Created Calculated DAX column for Age category.
    - Used Donut Chart for this visualization that gives attrition count of the Employees by Age Category.
      
![2024-10-25_13h08_29](https://github.com/user-attachments/assets/68e5f6e4-d64d-4443-80ad-9cee1f4e59db)


 9. Attrition by Education:
    - Used Clustered Bar Chart for this visualization that gives attrition Rate of the Employees by Education.

![2024-10-25_13h08_59](https://github.com/user-attachments/assets/e4c542ad-2dbd-4252-b2d3-88de11f9e5d3)

### Workforce Analysis

This page presents a comprehensive view of Workforce. 
- By establishing a relation, with Attrition Rates to various metrics such as Average Monthly Salary, Average Monthly Rate, Average Training times last year  gives key valuable Insights that leads to higher Attrition Rates.
- Users can Interact with any Visualization by using slicers for Gender/Department/Job Role.Implemented Slicers for filtering insights by Attrition, Department, Gender, and Job Role.

![workforce analysis](https://github.com/user-attachments/assets/596e2e18-240c-4e3d-a028-9fc76cc6678d)


 1. Attrition Rate Vs Average Monthly Salary by Job Role:
    - In this Line Chart Visual, Average Monthly of the Employees by Job Role is compared with Attrition Rate which provides an information that the Attrition Rate is higher for the Job Roles with Lower Pay such as Sales Representative and Lab Techncian role.
    - Users can Interact with any Visualization by using slicers for Gender/Department.

![2024-10-25_13h09_28](https://github.com/user-attachments/assets/1a49d927-3a3e-46a6-b53c-932bb6485742)

 2. Attrition Rate Vs Average Monthly Salary and Average Rate by Job Role:
    - In this Line and Clustered Column Chart Visual, Average Monthly Salary of the Employees and Average Rate by Job Role is compared with Attrition Rate which provides an information that the AVerage Monthly Salary is too low comparing to Average Monthly Rate fixed by the Company for the Job Roles Sales Representative and Lab Technician. It also corresponds to Higher Attrition Rate.
    - Users can Interact with any Visualization by using slicers for Gender/Department.

  ![2024-10-25_13h09_38](https://github.com/user-attachments/assets/035269e9-88f3-4509-ac67-846213bcfacb)

 3. Attrition Rate Vs Average Training times Last year by Job Role:
    - In this Line Chart Visual, Average Training Times of the Employees by Job Role is compared with Attrition Rate which provides an information that the Job Role Sales Representative has Undergone Highest Training Times last Year has Highest Attrition Rate which clearly shows that Company incured Loss on Training Cost for these Job Roles.
    - Users can Interact with any Visualization by using slicers for Gender/Department.

![2024-10-25_13h10_07](https://github.com/user-attachments/assets/fc6b5b0f-646e-47b8-94e5-2ab95f80502f)
   
 4. Attrition Count Vs Average Work Life Balance:
    - Used Donut Chart for this visualization that gives attrition count based on the Average Work Life Balance.
    - Users can Interact with any Visualization by using slicers for Gender/Department.

![2024-10-25_13h09_51](https://github.com/user-attachments/assets/8a0c8fd4-6cca-4059-ab91-3ff47f935113)

### Correlation Analysis

This page presents a comprehensive view of overall Workforce trends by Attrition. 
  - Key metrics include indices like Environment satisfaction Index, Job satisfaction index, Job Involvement Index, Average Tenure at the Company by Job Role are there in this Page.
  - Users can Interact with any Visualization by using slicers for Gender/Department/Job Role/Attrition.

![Correlation Analysis](https://github.com/user-attachments/assets/c0ac7c4c-4cd6-4641-ab56-670c85a2e6c4)


1. This dashboard presents a comprehensive view of overall Employee Wellness.
     - Analysing by the Key metrics include Relationship Satisfaction Index, Performance Satisfaction Index,Environment Satisfaction Index, Overtime Rate, Training Rate, Business Travel, Managerial Change Rate to find the Impact On Higher Attrition Rates.
     - Users can Interact with Visualization by using slicers for Gender/Department/Job Role.
     
![2024-10-25_13h10_24](https://github.com/user-attachments/assets/8fb89342-aeb7-40ca-99cf-c57b2f8f2c7b)

2. Average Tenure at the Company by Job Role:
   - Used clustered Bar Chart for this visual to analyze Employees Tenure Patterns Based on the Job Role.
   - User can interact with these Metrics by using Slicers For Department/Gender/Attrition/Job Role.
  
    ![2024-10-25_13h10_42](https://github.com/user-attachments/assets/881a2c88-deb1-4dc1-9a7d-d1dc592783c8)

3. Average Tenure since Last Promotion by Job Role Vs Attrition Rate:
   - Used Line and clustered Column Chart for this visual to analyze Employees Tenure Patterns Based on the Job Role with Attrition Rate.
   - User can interact with these Metrics by using Slicers For Department/Gender/Attrition/Job Role.

    ![2024-10-25_13h10_34](https://github.com/user-attachments/assets/62946847-af0c-4268-833a-54a70abf671b)

4. Managerial Change Rate Vs Attrition Rate:
    - In this Line and Clustered Column Chart Visual, Mnagerial Change Rate of the Employees by Job Role is compared with Attrition Rate which provides an information that the Job Role Sales with Highest Business Travel has Highest Attrition Rate for the Sales Representative Job Role.
    - Users can Interact with any Visualization by using slicers for Gender/Department.

    ![2024-10-25_13h10_51](https://github.com/user-attachments/assets/8d81e504-543d-454b-be86-f67c65621c91)

### Key Insights

#### Attrition Rate Trends:
- Out of 1470 Total Employees, 237 Employees left the company which estimates 16.12 % Attrition Rate.
#### Departmental Variances:
- 133  is the Attrition count in R&D Department, followed by Sales Department with 92 Attrition count.
- Lab Technician is the Job Role which has the Highest Attrition Count of 62 in R&D Department with Average Monthly salary of 3237.14.
- Sales Representative is the Job Role which has Highest Attrition Rate of 39.76% with Average Monthly salary of 2626.
#### Demographic Analysis:
- Attrition by Gender gives an Insight that out of 237 Employees, 150 are the Male Employees and 87 are the Female Employees.
- The Average Age of the Employees Under Attrition Category is 34.
#### Correlation with Satisfaction Surveys:
- The Job Satisfaction Index is 2 (Employees under Attrition Category) which shows Employees are dissatisfied with their Job.
- The Average Work-Life Balance of the Employees under Attrition category is 3(Average).
#### Identification of High-Risk Roles:
- Sales Representative, Sales Executive, Lab Technician Job Roles are at Higher likelihood of Attrition by Job role.
#### Cost Analysis:
 -  As per the Analysis, Sales Representative and Lab Technician are the Job roles that undergone Highest Average Training Times Last Year have the Highest Attrition Rate which indicates that company has incured loss on both Recruitment cost and Training cost.

### Succession Planning Opportunities:

1. Identifying High-Potential Employees
2. Developing Leadership Training Programs
3. Creating Talent Pipelines
4. Cross-Training and Skill Development
5. Knowledge Transfer Programs
6. Succession Planning for Critical Departments
7. Creating Mentorship Programs
8. Encouraging Career Development Discussions
9. Internal Promotions and Advancements
10. Strategic Recruitment for Critical Roles
11. Employee Engagement Initiatives

### Recommendations

 #### Competitive Compensation Strategies:
Keep up with market rates to ensure employees receive competitive salaries and comprehensive compensation packages.
 #### Career Growth Opportunities:
Foster an environment that provides clear pathways for career advancement and growth within the organization.
 #### Cultivating a Positive Workplace Culture:
Actively work to improve workplace culture, creating an environment that promotes collaboration, inclusion, and employee satisfaction.
 #### Prioritizing Work-Life Balance:
Recognize and prioritize the importance of work-life balance to enhance employee well-being and job satisfaction.
 #### Recognition and Rewards Programs:
Implement effective programs to recognize and reward employees for their contributions and achievements.
 #### Strategic Recruitment Practices:
Ensure that the recruitment process aligns with the specific job roles, bringing in individuals who are well-suited for the positions.
 #### Leadership and Management Transformation:
Overhaul leadership and management styles to foster a more efficient, supportive, and empowering work environment.
 #### Flexible Work Arrangements for Overtime:
Offer flexibility to employees who work overtime, allowing for adaptable work arrangements that accommodate their needs

### Challenges faced
Navigating data challenges, including quality issues and limited historical data, integrating diverse data sources, Communicating complex findings effectively and adapting to unexpected external factors. Balancing technology/tool challenges, obtaining comprehensive employee feedback, and aligning analysis with organizational goals pose additional complexities.

### Conclusion:
In conclusion, this HR Attrition Analysis project has provided valuable insights into the organization's workforce dynamics. By analyzing trends, identifying key factors contributing to attrition, and offering actionable recommendations, this analysis contributes to informed decision-making. We acknowledge the lessons learned during this project and look forward to applying these insights in future HR analytics initiatives.
