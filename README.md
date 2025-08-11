# PWC Diversity and Inclusion Power BI Dashboard
## Dataset Used
- <a href="https://github.com/kalim-git/PWC-Switzerland-Diversity-Inclusion-Power-BI-Virtual-Internship-/blob/main/Diversity-Inclusion-Dataset.xlsx">Diversity & Inclusion Dataset</a>
## Background Information of the Task
Task is to do the following:
- Define relevant KPIs in hiring, promotion, performance and turnover, and create a visualisation.
- Write what you think some root causes of their slow progress might be.

Calculating the following measures could help to define proper KPIs:
- Count of men
- Count of women
- Count of leavers
- % employees promoted (FY21)
- % of women promoted
- % of hires men
- % of hires women
- % turnover
- Average performance rating: men
- Average Performance rating: women

## Object
The object of this analysis is to create a dashboard in PowerBI to represent HR data, particularly focusing on gender related KPIs. Also to identify and discuss potential root causes for the slow progress in achieving gender balance at the executive management level.

## KPIs include (but not limited to):
- Hiring
- Promotions (this year)
- Turnover Rate
- Performance Rating
- Executive Gender Balance
- Age Group

## Table Details
The tabulation below shows the Customer retention table with its column names and their description:

| Column Name | Description |
| --- | --- |
| EmployeeID | Represents the unique number of the employee in the dataset |
| Gender | Describes the gender of the employee |
| Job Level after FY20 promotions |	Describes the job level of the employee after being promoted in FY20 |
| New hire FY20? |	If the employee is a new hire in FY20 |
| FY20 Performance Rating	| The performance rating of the employee in FY20 |
| Promotion in FY21? | If the employee is being promoted in FY21 |
| In base group for Promotion FY21	| If the employee is being selected for promoted in FY21 |
| Target hire balance	| Describes the target hire balance of the employee |
| FY20 leaver?	| If the employee is a leaver in FY20 |
| In base group for turnover FY20	| Describes if the employee is in a group for turnover in FY20 |
| Department @01.07.2020	| Represents the department each employee belongs to as at January 7, 2020 |
| Leaver FY	| If the employee is a leaver in a FY |
| Job Level after FY21 promotions	| Describes the job level of the employee after being promoted in FY21 |
| Last Department in FY20	| Represents the last department each employee belongs in FY20 |
| FTE group	| Describes if the employee belongs to a FTE group |
| Time type	| Represents the contract type employee |
| Department & JL group PRA status	| Describes the department and JL group PRA status of the employee |
| Department & JL group for PRA	| Represents the department and JL group PRA of the employee |
| Job Level group PRA status	| Describes the job level group PRA status of the employee |
| Job Level group for PRA	| Represents the job level group PRA of the employee |
| Time in Job Level @01.07.2020	| Describes the time in job level of the employee |
| Job Level before FY20 promotions	| Describes the job level employee before being promoted in FY20 |
| Promotion in FY20?	| If the employee is being promoted in FY20 |
| FY19 Performance Rating	| Describes the performance rating of the employee in FY19 |
| Age group	| Describes the age group of the employee |
| Age @01.07.2020	| Represents the age of the employee as at January 07, 2020 |
| Nationality 1	| Describes the nationality of the employee in state level |
| Region group: nationality 1	| Represents the nationality of the employee in country level |
| Broad region group: nationality 1	| Represents the nationality of the employee in regional level |
| Last hire date	| Describes the last hire date of the employee |
| Years since last hire	| Represents the number of years since last hire of the employee |
| Rand	| Generates random number for each entry in the dataset |

## Data Transformation
The Diversity & Inclusion dataset has 32 columns and 500 rows of observation.

Data transformation and cleaning were done in Power Query and the dataset was loaded into Microsoft Power BI Desktop for modelling.

## Data Visualization (Dashboard)
Data visualization for the dataset was done in Microsoft Power BI Desktop.
- <a href="https://github.com/kalim-git/PWC-Switzerland-Diversity-Inclusion-Power-BI-Virtual-Internship-/blob/main/Diversity%20%26%20Inclusion.pbix">Dashboard</a>

**Hiring, Promotions, Turnover Rate**
  <img width="1278" height="715" alt="page 1" src="https://github.com/user-attachments/assets/b2bd4b61-1191-4a80-9956-568c79dbfa99" />

**Performance Rating, Executive Gender Balance, Age Group**
  <img width="1284" height="718" alt="Page 2" src="https://github.com/user-attachments/assets/1c41c68d-1e85-4821-9edd-85ee66d1fa7e" />

**Job Diversity, Nationality of Employees, Regional Diversity**
  <img width="1285" height="716" alt="Page 3" src="https://github.com/user-attachments/assets/514c5421-ff13-400b-877b-cf6514d0eb3b" />

 
## Data Analysis
**Measures(DAX) used:**
- Average Rating Men = `CALCULATE(AVERAGE( 'Pharma Group AG'[FY20 Performance Rating]),'Pharma Group AG'[Gender]="Male")`
- Average Rating Women = `CALCULATE(AVERAGE( 'Pharma Group AG'[FY20 Performance Rating]),'Pharma Group AG'[Gender]="Female")`
- Employee Turnover = `DIVIDE('Pharma Group AG'[# of Leavers],COUNT('Pharma Group AG'[Employee ID]),0)`
- Count of Leavers = `CALCULATE(COUNTA('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Leaver FY] = "FY20")`
- Total Men = `CALCULATE(DISTINCTCOUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Gender] = "Male")`
- Total Women = `CALCULATE(DISTINCTCOUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Gender] = "Female")`
- Promoted in FY20 = `CALCULATE(COUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Promotion in FY20?]="Yes")+CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),'Pharma Group AG'[Promotion in FY21?]="Yes")`
- Promoted in FY21 = `CALCULATE(COUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Promotion in FY21?]="Yes")`
- Promoted in FY21 in % = `Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Promotion in FY21?]="Yes"),Calculate(distinctcount('Pharma Group AG'[Employee ID]),'Pharma Group AG'[In base group for Promotion FY21]="Yes"))`
- Men Hired in % = `DIVIDE('Pharma Group AG'[# of Men],'Pharma Group AG'[# of Men]+'Pharma Group AG'[# of Women])`
- Women Hired in % = `DIVIDE('Pharma Group AG'[# of Women],'Pharma Group AG'[# of Men]+'Pharma Group AG'[# of Women])`
- Women Promoted in % = `Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Promotion in FY21?]="Yes",'Pharma Group AG'[Gender]="Female"),Calculate(distinctcount('Pharma Group AG'[Employee ID]),'Pharma Group AG'[In base group for Promotion FY21]="Yes"))`

## Insights
As shown by Data Visualization, It can be deduced that:
- Overall, the company seems to have a good gender balance in terms of hiring, with women making up just under half (41%) of new hires. However, there is a significant disparity in promotion rates, with only 25% of promotions going to women. Specially from the Senior Manager level the gender gap keeps increasing. This suggests that there may be barriers in place that are preventing women from being promoted at the same rate as men.
- It is noticiable that in executive roles men tends to get promotion in less time than women.
- The turnover rate is higher for women than for men. This could be due to a number of factors, including the gender pay gap, a lack of opportunities for advancement, or a hostile work environment.
- The average performance rating of the employees decreased from to in FY20.
- Maximum hiring of employees is done from Switzerland ,France & Germany respectively, hence in order to increase diversity need to hire talented employees from different part of globe.
- The slow progress in the executive level is of the fact that only less than 20% female is promoted to this managerial and executive roles.
- Employee promotion rate is increase by 3% in FY21 than FY20.
- FY20 Hires vs FY21 Job Level: While the number of females hired increased slightly from FY20 (40) to FY21 (41), the number of females in senior positions (director and above) remained the same (3) in both years. This indicates a potential gap in promoting women to higher-level positions.
- Women are more likely to be in lower-level positions, such as junior officers and managers, while men are more likely to be in higher-level positions, such as directors and executives. This suggests that there may be a lack of opportunities for women to progress to senior leadership positions.
- The most common age group is 20-29 having 223 employees fall in this category.

## Recommendation
To ensure progress in diversity and inclusion in the executive level:
- More women should be hired and most especially promoted because the gap in the ratio of men to women is quite large.
- For the Executive and Director position ,female employee count as well as the promotion count is too low compared to male employee hence more women should be hired as well as promoted.
- Age group 30-39 has more rate of promotion compared to 40-49 age group, experience should be considered as one of the criteria for promotion checklist.
- Have to create a safe environment for women so that they stay and contribute at the organisation with their expertise.

