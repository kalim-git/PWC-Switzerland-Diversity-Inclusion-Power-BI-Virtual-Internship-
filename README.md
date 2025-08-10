# PWC Diversity and Inclusion Power BI Dashboard
## Dataset Used
- <a href="https://github.com/kalim-git/PWC-Switzerland-Customer-Retention-Power-BI-Virtual-Internship-/blob/main/Churn-Dataset.xlsx">Customer Retention Dataset</a>
## Background Information of the Task
The telecom Retention Manager has scheduled a meeting with the engagement partner at PwC to cover these points:
 - Customers in the telecom industry are hard-earned: we don’t want to lose them.
 - The retention department is here to get customers back in case of termination.
 - Currently, we get in touch after they have terminated the contract, but this is reactionary: it would be better to know in advance who is at risk.
 - We have done customer analysis with Excel: it has always ended in a dead-end.
 - We would like to know more about our customers: visualised clearly so that it’s self-explanatory for our management.

Your colleague, the engagement partner, asks you to do the following tasks:
1.	Define proper KPIs
2.	Create a dashboard for the retention manager reflecting the KPIs
3.	Write a short email to him (the engagement partner) explaining your findings, and include suggestions as to what needs to be changed

Here are some inputs:
 - **Customers** who left within the last month
 - **Services each customer has signed up for**: phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
 - **Customer account information**: how long as a customer, contract, payment method, paperless billing, monthly charges, total charges and number of tickets opened in the categories administrative and technical
 - **Demographic info about customers**: gender, age range, and if they have partners and dependents

## Object
The object of this analysis is to create a dashboard in PowerBI for Call Center Manager about Customer Retention that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset.
## Possible KPIs include (but not limited to):
- Customer Left
- Yearly Charges
- Monthly Charges
- Churn Rate
- Customers Retained
- Tenure
- Total Senior Citizen
- Number of Admin Tickets
- Number of Tech Tickets
- Payment Method
- Gender

## Table Details
The tabulation below shows the Customer retention table with its column names and their description:

| Column Name | Description |
|--- | --- |
| customerID | Represents the unique number of the customer in the dataset |
| gender | Describes the gender of the customer |
| SeniorCitizen |	Describes if the customer is a senior citizen |
| Partner | Describes if the customer has a partner |
| Dependents |	Describes if the customer has a dependent |
| tenure	| Describes how long as a customer |
| PhoneService |	If the customer has registered a phone service |
| MultipleLines |	If the customer has registered multiple lines |
| InternetService	| If the customer has registered for internet service |
| OnlineSecurity	| If the customer has registered for online security |
| OnlineBackup |	If the customer has registered for online backup |
| DeviceProtection	| If the customer has registered for device protection |
| TechSupport |	Describes if the customer has registered for tech support |
| StreamingTV	| If the customer has registered to stream tv |
| StreamingMovies |	If the customer has registered to stream movies |
| Contract |	Describes if the length of the contract of the customer |
| PaperlessBilling |	Describes if the customer has registered for paperless billing |
| PaymentMethod |	Describes the payment method of the customer |
| MonthlyCharges |	Represents the monthly charge incurred by the customer |
| TotalCharges |	Represents the total charge incurred by the customer |
| numAdminTickets	| Represents the number of admin tickets opened by the customer |
| numTechTickets	| Represents the number of tech tickets opened by the customer |
| Churn |	Describes if the customer is at risk of churn |



## Data Transformation
The Customer churn dataset has 23 columns and 7043 rows of observation.

Data transformation and cleaning were done in Power Query and the dataset was loaded into Microsoft Power BI Desktop for modelling.

In the new table, one additional conditional column was added called "Year" :
- Year = `Table.AddColumn(#"Changed Type", "# Year", each if [tenure] < 12 then "< 1 year" else if [tenure] < 24 then "< 2 years" else if [tenure] < 36 then "< 3 years" else if [tenure] < 48 then "< 4 years" else if    [tenure] < 60 then "< 5 years" else "< 6 years")`


## Data Visualization (Dashboard)
Data visualization for the dataset was done in Microsoft Power BI Desktop.
- <a href="https://github.com/kalim-git/PWC-Switzerland-Customer-Retention-Power-BI-Virtual-Internship-/blob/main/Customer%20Churn%20Dashboard.pbix">Dashboard</a>

**Welcome Page**
<img width="1277" height="718" alt="1 Welcome" src="https://github.com/user-attachments/assets/449f9c83-4a0d-4e5c-892d-e89dfcb0015d" />

**Churn Dashboard**
<img width="1283" height="713" alt="2 Churn" src="https://github.com/user-attachments/assets/4cd876d1-d421-4a50-a96d-fad9c881629f" />

**Risk Analysis**
<img width="1282" height="718" alt="3 Risk Analysis" src="https://github.com/user-attachments/assets/2cd9d237-6a26-456e-81df-7b22491fbe07" />

**Services**
<img width="1278" height="715" alt="4 Services" src="https://github.com/user-attachments/assets/3477019e-af40-4801-9c77-e9ba0887bf24" />

## Data Analysis
**Measures(DAX) used**
- Average Monthly Charges = `CALCULATE(AVERAGE('Churn-Dataset'[MonthlyCharges]),'Churn-Dataset'[Churn]="Yes")`
- Average Total Charges = `CALCULATE(AVERAGE('Churn-Dataset'[TotalCharges]),'Churn-Dataset'[Churn]="Yes")`
- Churn Rate % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[Churn]),'Churn-Dataset'[Churn]="Yes"),COUNT('Churn-Dataset'[Churn]),0)`
- Customers Churn = `CALCULATE(COUNT('Churn-Dataset'[customerID]),'Churn-Dataset'[Churn]="Yes")`
- Customers Retained = `CALCULATE(COUNT('Churn-Dataset'[customerID]),'Churn-Dataset'[Churn]="No")`
- Dependents % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[Dependents]),'Churn-Dataset'[Dependents]="Yes",'Churn-Dataset'[Churn]="Yes"), CALCULATE(COUNT('Churn-Dataset'[Dependents]), 'Churn-Dataset'[Churn]="Yes"), 0)`
- Device Protection % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[DeviceProtection]), 'Churn-Dataset'[DeviceProtection] ="Yes", 'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[DeviceProtection]),'Churn-Dataset'[Churn]="Yes"),0)`
- Online Backup % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[OnlineBackup]), 'Churn-Dataset'[OnlineBackup] ="Yes", 'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[OnlineBackup]),'Churn-Dataset'[Churn]="Yes"),0)`
- Online Security % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[OnlineSecurity]), 'Churn-Dataset'[OnlineSecurity] ="Yes", 'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[OnlineSecurity]),'Churn-Dataset'[Churn]="Yes"),0)`
- Phone Service % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[PhoneService]), 'Churn-Dataset'[PhoneService] ="Yes", 'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[PhoneService]),'Churn-Dataset'[Churn]="Yes"),0)`
- Partner % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[Partner]),'Churn-Dataset'[Partner]="Yes",'Churn-Dataset'[Churn]="Yes"), CALCULATE(COUNT('Churn-Dataset'[Partner]), 'Churn-Dataset'[Churn]="Yes"), 0)`
- Senior Citizen % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[SeniorCitizen]),'Churn-Dataset'[SeniorCitizen] = 1,'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[SeniorCitizen]),'Churn-Dataset'[Churn]="Yes"),0)`
- Streaming Movies % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[StreamingMovies]), 'Churn-Dataset'[StreamingMovies] ="Yes", 'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[StreamingMovies]),'Churn-Dataset'[Churn]="Yes"),0)`
- Streaming TV % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[StreamingTV]), 'Churn-Dataset'[StreamingTV] ="Yes", 'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[StreamingTV]),'Churn-Dataset'[Churn]="Yes"),0)`
- Tech Support % = `DIVIDE(CALCULATE(COUNT('Churn-Dataset'[TechSupport]), 'Churn-Dataset'[TechSupport] ="Yes", 'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[TechSupport]),'Churn-Dataset'[Churn]="Yes"),0)`

## Insights
As shown by Data Visualization, It can be deduced that:
-	Customers on the Two-Year contract, have been with the company for long, while most of the customers joined the company on Month-to-Month contract basis.
-	The company is at risk of losing recently joined customers. Specially those customers who decided for month-to-month contract.
-	7043 customers are at the risk of churn. and The churn rate is 26.54% and yearly charges is $16.06M charges. and Monthly Charges is $456.12K monthly charges.
-	2955 tech tickets were opened and 3632 admin tickets were opened.
-	Most of the churned customers did not sign up for Online Security and tech support and also did not sign up for Phone Services.
-	A lot of customers had an issue with Fiber Optic . Up to 42% of the customers churned were using Fiber Optic as their Internet Services.
-	If no Tech Support, Device Protection, and Online Security are provided then the chances of customers churning are high.
-	Tenure and contract play an important role in determining whether the customer will churn. Customers with monthly contracts i.e. lower tenure will switch frequently.

## Recommendation
-	The Company could try convincing customers to subscribe to One-Year and Two-Year contract. The short term contracts are not favorable to customers as they tend to pay more monthly.
-	Provide some offers to the senior citizens as they are stable customers, and offer some discounts on long tenure plans.
-	Giving the discount to customers based on some specific tasks is a good way to retain them, specially those month-to-month contract.
-	From analysis majority customers who churned did not sign up for Online Security and Tech Support. These are the important services that customers should signup for.
  The company should educate customers on the benefits of signing up for these services.
-	Increase sale of 1 and 2 year contract by 5% each and Yearly increase of automatic payments by 5%.
