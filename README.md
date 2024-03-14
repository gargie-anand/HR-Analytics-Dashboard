# HR-Analytics-Dashboard
- The HR Analytics Dashboard is a comprehensive tool focusing on three main sections: Attrition, Demographics, and Employee Satisfaction.
- Each section provides valuable data-driven insights essential for informed decision-making and strategic planning within the HR department.
  
![1](https://github.com/gargie-anand/HR-Analytics-Dashboard/assets/163330089/56296e4c-233c-4f5c-9c72-1626fb785698)

## Table of Content
- [Problem Statement](https://github.com/gargie-anand/HR-Analytics-Dashboard/edit/main/README.md#problem-statement)
- [Tools Used](https://github.com/gargie-anand/HR-Analytics-Dashboard/edit/main/README.md#tools-used)
- [Data Source](https://github.com/gargie-anand/HR-Analytics-Dashboard/edit/main/README.md#data-source)
- [Data Preparation](https://github.com/gargie-anand/HR-Analytics-Dashboard/edit/main/README.md#data-preparation)
- [DAX Codes](https://github.com/gargie-anand/HR-Analytics-Dashboard/edit/main/README.md#dax-codes)
- [Dashboards](https://github.com/gargie-anand/HR-Analytics-Dashboard/edit/main/README.md#dashboards)
- [Recommendation](https://github.com/gargie-anand/HR-Analytics-Dashboard/edit/main/README.md#recommendation)

## Problem Statement
Build a HR Analytics Dashboard, Attrition, Employee satisfaction

## Tools Used
Microsoft Power BI

## Data Source
HR Aanlytics Dataset: https://drive.google.com/drive/folders/18mQalCEyZypeV8TJeP3SME_R6qsCS2Og

## Data Preparation
After importing the csv file `HR Analytics Dataset`, cleaned the data in the power query.

Dataset contained `38 rows` and `1481 rows`.
- The headers were promoted.
- The column `YearsWithCurrManager` was removed.
- Duplicates were removed.
- `TravelRarely` was changed to `Travel_Rarely` to remove redundancy.
- Data types were adjusted.
 
## DAX Codes

### Measures Used:
- ActiveEmployees =  `CALCULATE([TotalEmployees], FILTER(HR_Analytics, HR_Analytics[Attrition] = "No"))`
  
- Attrition Rate = `SUM(HR_Analytics[AttritionCount])/SUM(HR_Analytics[EmployeeCount])`
  
- AverageSalary = `AVERAGE(HR_Analytics[MonthlyIncome])`
  
- InactiveEmployees = `CALCULATE([TotalEmployees], FILTER(HR_Analytics, HR_Analytics[Attrition] = "Yes"))`
  
- OverallSatisfactionLevel = 
    `AVERAGEX(
        'HR_Analytics',
        (
            'HR_Analytics'[EnvironmentSatisfaction] + 
            'HR_Analytics'[JobSatisfaction] + 
            'HR_Analytics'[RelationshipSatisfaction] + 
            'HR_Analytics'[WorkLifeBalance]
        ) / 4
    )`
  
- TotalEmployees = `DISTINCTCOUNT(HR_Analytics[EmpID])`

### Columns used:
- AttritionCount = `IF('HR_Analytics'[Attrition] = "Yes", 1, 0)`

## Dashboards

### Attrition:
- HR Department can calulate the Attrition trends through this dashboard.
- `237` employees left the company out of `1470`.
- More number of males `150` left company than female `87`.
- Total of `116` employees left from Age Group `26-35`.
- More number of employees working in job role `Laboratory Technicians`, `Sales Executive`, `Research Scientist` rated the job satisfaction as `1`.
- `163` employees which left were earning upto 5k.
- `30.53%` of the employees which left were working overtime in comparison to `10.44%` which stayed.
  
  ![2](https://github.com/gargie-anand/HR-Analytics-Dashboard/assets/163330089/4e2d2ea0-37cd-48b2-b9a0-fb17a0c11a2a)

### Demographics:
- Highest number of employee are in the Age Group `26-35`.
- Employees with background in `Life Sciences` has the highest number of employee count followed by `Medical` and `Marketing`.
- Employees earning upto 5k are higher in comparison with other higher income slabs.
- Married employees consist of highest number of employee count of `673`.
- Male employees are earning more than Female employees across all Age Group.
- Employee count of Male are higher than Female employees across all Age Group.

![3](https://github.com/gargie-anand/HR-Analytics-Dashboard/assets/163330089/679f8769-2e31-4eeb-9b8d-bddc629a7974)

### Employee Satisfaction:
- Satisfaction level is almost same across all Age Group, Gender and Department.

![4](https://github.com/gargie-anand/HR-Analytics-Dashboard/assets/163330089/04be6fc0-65f5-4783-b21a-c27afe8ba19b)

## Recommendation
- The company can implement regular surveys or feedback mechanisms to gather insights into employee satisfaction and identify areas for improvement.
- Potential reasons can be explored behind the higher percentage of employees leaving who work overtime. It may indicate potential burnout or dissatisfaction with workload. 
- Investigate why certain job roles, such as Laboratory Technicians, Sales Executives, and Research Scientists, have higher rates of dissatisfaction. Addressing these issues could help reduce attrition.
- Implement regular surveys or feedback mechanisms to gather insights into employee satisfaction and identify areas for improvement.
