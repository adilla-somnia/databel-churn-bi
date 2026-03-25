###### TECHNICAL.md

# Technical Support Documentation - Databel Churn BI

This document provides a comprehensive overview of the custom measures and columns used in the Power BI visuals of this project.

The first section provides a detailed list of each page in the Power BI report, along with the visuals and their associated measures. The second section contains a detailed list of all measures and calculated columns, along with their DAX formulas, explanations, and usage

## How to Read This Document

This document is divided into two main sections:

1. **Report Structure**
    - Lists each report page
    - Lists each visual and the measures used

2. **Data Model & DAX**
    - Contains all measures and calculated columns
    - Includes DAX formulas and explanations
    - "Used in" references the visuals and pages where the measure is used.
    - "Used by" references other measures that depend on this one for calculation.

Use this document as a reference to understand how each visual is built and how calculations are defined.

## Report Pages and Visuals

### 1. Overview

![Overview Page Screenshot](/images/technical/overview.png)

---

#### Total Customers
- Type: Card 1
- Data field: Customer_Total

#### Churn Rate %
- Type: Card 2
- Data field: Churn_Rate

#### Customers Churned
- Type: Card 3
- Data field: Customers_Churned

#### Current Monthly Revenue
- Type: Card 4
- Data field: Revenue_Monthly_Current_Speculated

#### Revenue Lost Due to Churn
- Type: Card 5
- Data field: Revenue_Monthly_Churners
Postfix Label: "/month"

#### Monthly Revenue: Current vs From Churners
- Type: Pie Chart
- Values: Revenue_Monthly_Current_Speculated, Revenue_Monthly_Churners
- Tooltips: Revenue_Shrinking_Rate

#### Active vs Churned Customers by Contract Type
- Type: Clustered Column Chart 1
- X-axis: Contract Type
- Y-axis: Customers_Churned, Customers_Active

#### Average Account Length (months)
- Type: Clustered Column Chart 2
- Y-axis: Customer_Churned_AccountLength_Average, Customer_Active_AccountLength_Average

#### Average Monthly Charge
- Type: Card 6
- Data field: Revenue_Monthly_Average

#### Average Churner Monthly Charge
- Type: Card 7
- Data field: Customer_Churned_Charges_Average

---

### 2. Churn Overview

![Churn Overview Page Screenshot](/images/technical/churn_overview.png)

---

#### Plans
- Type: 100% Stacked Bar Chart 1
- Y-axis: Plans
- X-axis: Customers_Churned, Customers_Active
- Tooltips: GB_Monthly_Average

#### Payment Method
- Type: 100% Stacked Bar Chart 2
- Y-axis: Payment Method
- X-axis: Customers_Churned, Customers_Active

#### Contract Type
- Type: Clustered Column Chart
- Y-axis: Contract Type
- X-axis: Customers_Churned, Customers_Active

#### Customers in Groups
- Type: 100% Stacked Column Chart
- Y-axis: Number of Customers in Group
- X-axis: Customers_Churned, Customers_Active

---

### 3. Customer Behavior

![Customer Behavior Page Screenshot](/images/technical/customer_behavior.png)

---

#### Service Calls Average by Churn Status
- Type: Funnel 1
- Category: Churn Label
- Values: Service_Calls_Average

#### Churners by Extra Charges
- Type: Stacked Column Chart
- X-axis: Extra Charged
- Y-axis: Customers_Churned

#### Average Account Length
- Type: Clustered Bar Chart
- X-axis: Customer_Active_AccountLength_Average, Customer_Churned_AccountLength_Average

#### Average Monthly Charge by Churn Status
- Type: Funnel 2
- Category: Churn Label
- Values: Revenue_Monthly_Average

---

### 4. Geographic Analysis

![Geographic Analysis Page Screenshot](/images/technical/geographic_analysis.png)

---

#### Total Churned Customers by States
- Type: Map
- Location: StateLongName
- Bubble size: Customers_Churned
- Tooltips: Revenue_Monthly_Average, Churn_Rate

#### Top 5 Highest Churned Customers States
- Type: Stacked Bar Chart
- Y-axis: StateLongName
- X-axis: Customers_Churned
- Filters: StateLongName Top 5 Customers_Churned

#### Top 5 Highest Churn Rate States
- Type: Funnel
- Category: StateLongName
- Values: Churn_Rate

#### Churn Rate by States
- Type: Filled Map
- Location: StateLongName
- Tooltips: Churn_Rate, Revenue_Monthly_Average, Customers_Churned
- Filters: StateLongName Top 5 Churn_Rate

---

### 5. Churn Reasons

![Churn Reasons Page Screenshot](/images/technical/churn_reasons.png)

---

#### Churned Customers by Categories
- Type: Stacked Bar Chart 1
- Y-axis: Churn Category
- X-axis: Customers_Churned
- Tooltips: Churn_Category_Rate

#### Churned Customers by Churn Reason
- Type: Treemap
- Category: Churn Reason
- Values: Customers_Churned
- Filters: Churn Reason Top 5 Customers

#### Churn Category and Reason Breakdown
- Type: Stacked Bar Chart 2
- Y-axis: Churn Category, Churn Reason
- X-axis: Customers_Churned
- Drill-down: active

---

### 6. Past Speculations

![Past Speculations Page Screenshot](/images/technical/past_speculations.png)

---

#### Churn Rate Percentage Value
- Type: Card 1
- Data field: Slicer_Selected_Churn_Rate_Percentage

#### Select Churn Rate
- Type: Slicer
- Field: Slicer_Churn_Rate

#### Revenue Churners Staying
- Type: Card 2
- Data field: Revenue_NoLongerChurner
- Tooltip fields: Revenue_Growth_Percentage

#### Current Revenue + Revenue Churners Staying
- Type: Card 3
- Data field: Revenue_NoLongerChurner_Active_Sum

#### Current Revenue
- Type: Card 4
- Data field: Revenue_Running_Total

#### Churned Customers
- Type: Card 5
- Data field: Customers_Churned

#### Churners No Longer
- Type: Card 6
- Data field: Customer_NoLongerChurner

#### Churners Still
- Type: Card 7
- Data field: Customer_StillChurner

#### Average Account Length (months)
- Type: Textbox

#### Active Customer 
- Type: Card 8
- Data field: Customer_Active_AccountLength_Average

#### Churned Customer
- Type: Card 9
- Data field: Customer_Churned_AccountLength_Average

#### No Longer Churner
- Type: Card 10
- Data field: Customer_NoLongerChurner_AccountLength_Average

#### Revenue From No Longer Churners Staying Extra Months
- Type: Line and Clustered Column Chart
- X-axis: Slicer_Months
- Column - Y-axis: Customer_NoLongerChurner, Customers_Churned
- Line - Y-axis: Revenue_NoLongerChurner
- Tooltips: Average of Account Length (in months)

---

### 7. Future Speculations

![Future Speculations Page Screenshot](/images/technical/future_speculations.png)

---

#### Select Churn Rate
- Type: Slicer 1
- Field: Slicer_Churn_Rate

#### Select a Month Range
- Type: Slicer 2
- Field: MonthNumber

#### Total Revenue Lost by Months
- Type: Stacked Column Chart
- X-axis: MonthNumber(bins)
- Y-axis: Revenue_Lost_Total

#### Monthly Revenue Decreased by
- Type: Card 1
- Value: Label_Revenue_Decrease_Absolute_Percentage

#### Churn Rate %
- Type: Card 2
- Value: Slicer_Selected_Churn_Rate_Percentage

#### Monthly Revenue: Future Speculation vs Current
- Type: Line Chart
- X-axis: MonthNumber
- Y-axis: Revenue_Monthly_Future_Speculated, Revenue_Monthly_Current_Speculated

#### Total Lost Revenue
- Type: Card 3
- Value: Revenue_Lost_Total
- Tooltips: Revenue_Churners_Stayed_Total

#### Total Surviving Revenue
- Type: Card 4
- Value: Revenue_Remaining_Total

#### Total Customers Churners
- Type: Card 5
- Data field: Future_Customer_Churned

#### Customers Remaining (Total)
- Type: Card 6
- Data field: Future_Customer_Remaining_Total

---

## Tables and Measures/Columns

### _Measures

<span style="background-color: red; color: white; padding: 0.2em 0.4em; border-radius: 3px;">This table contains the main measures used throughout this project's visuals.</span>

---

#### Churn_Category_Rate
- **Type:** Measure
- **Purpose:** Calculates the churn rate without applying any filters.
- **DAX Formula:**
```
Churn_Category_Rate = 
DIVIDE(
    [Customer_Churned],
    CALCULATE(
        [Customer_Churned],
        ALL('Databel - Data')
    )
)
```
- **Used in:** 
    - Churn Reasons
        - Churned Customers by Categories

---

#### Churn_Rate
- **Type:** Measure
- **Purpose:** Calculates the proportion of churned customers relative to the total customer base.
- **DAX Formula:**
```
Churn_Rate = DIVIDE([Customer_Churned], [Customer_All])
```
- **Used in:** 
    - Overview
        - Churn Rate %
    - Geographic Analysis
        - Total Churned Customers by States
        - Top 5 Highest Churn Rate States
        - Churn Rate by States

---

#### Current_Revenue_Monthly_Churner_Sum
- **Type:** Measure
- **Purpose:** Estimates the total monthly revenue the company is losing due to churned customers, based on their average monthly charge.
- **DAX Formula:**
```
Current_Revenue_Monthly_Churner_Sum = CALCULATE(
    SUM('Databel - Data'[Monthly Charge]),
    'Databel - Data'[Churn Label]="Yes")
```
- **Used by:** 
    - `Revenue_Shrinking_Rate`

---

#### Customer_Active
- **Type:** Measure
- **Purpose:** Calculates the total of active customers.
- **DAX Formula:**
```
Customer_Active = CALCULATE(
    COUNTROWS('Databel - Data'),
    'Databel - Data'[Churn Label] = "No")
```
- **Used by:** 
    - `Customer_Active_ExpectedToChurn`
    - `Future_Customer_Stable`
    - `Revenue_Monthly_Current_Speculated`

---

#### Customer_Active_AccountLength_Average
- **Type:** Measure
- **Purpose:** Calculates the active customers' account length average.
- **DAX Formula:**
```
Customer_Active_AccountLength_Average = CALCULATE(
    AVERAGE('Databel - Data'[Account Length (in months)]),
    'Databel - Data'[Churn Label]="No")
```
- **Used in:** 
    - Overview
        - Average Account Length (months)
    - Customer Behavior
        - Average Account Length
    - Past Speculations
        - (Average Account length) Active Customer

---

#### Customer_All
- **Type:** Measure
- **Purpose:** Calculates the total of customers, active and churners.
- **DAX Formula:**
```
Customer_All = COUNTROWS('Databel - Data')   
```
- **Used in:** 
    - `Customer_StillChurner`
    - `Churn_Rate`

---

#### Customer_Churned
- **Type:** Measure
- **Purpose:** Calculates the total of churned customers.
- **DAX Formula:**
```
Customer_Churned = CALCULATE(
    COUNTROWS('Databel - Data'),
    'Databel - Data'[Churn Label] = "Yes")
```
- **Used by:** 
    - `Churn_Category_Rate`
    - `Churn Rate`
    - `Customer_NoLongerChurner`

---

#### Customer_Churned_AccountLength_Average
- **Type:** Measure
- **Purpose:** Calculates the churned customers' account length average.
- **DAX Formula:**
```
Customer_Churned_AccountLength_Average = CALCULATE(
    AVERAGE('Databel - Data'[Account Length (in months)]),
    'Databel - Data'[Churn Label]="Yes")
```
- **Used in:** 
    - Overview
        - Average Account Length (months)
    - Customer Behavior
        - Average Account Length

---

#### Customer_Churned_Charges_Average
- **Type:** Measure
- **Purpose:** Calculates the churned costumer's average monthly charge.
- **DAX Formula:**
```
Customer_Churned_Charges_Average = CALCULATE(
    AVERAGE('Databel - Data'[Monthly Charge]),
    'Databel - Data'[Churn Label]="Yes") 
```
- **Used in:** 
    - Overview
        - Average Churner Monthly Charge

---

#### GB_Monthly_Average
- **Type:** Measure
- **Purpose:** Calculates the average GB monthly use.
- **DAX Formula:**
```
GB_Monthly_Average = AVERAGE('Databel - Data'[Avg Monthly GB Download])
```
- **Used in:** 
    - Churn Overview
        - Plans

---

#### Revenue_Monthly_Average
- **Type:** Measure
- **Purpose:** Calculates the average monthly revenue across all customers.
- **DAX Formula:**
```
Revenue_Monthly_Average = AVERAGE('Databel - Data'[Monthly Charge])
```
- **Used in:** 
    - Overview
        - Average Monthly Charge
    - Customer Behavior
        - Average Monthly Charge by Churn Status
    - Geographic Analysis
        - Total Churned Customers by States
        - Churn Rate by States

---

#### Revenue_Monthly_Charges_Total
- **Type:** Measure
- **Purpose:** Calculates the total revenue from all customers' monthly charges(which is an average).
- **DAX Formula:**
```
Revenue_Monthly_Charges_Total = SUM('Databel - Data'[Monthly Charge])
```
- **Used by:** 
    - `Revenue_Monthly_Churners`
    - `Revenue_Shrinking_Rate`

---

#### Revenue_Monthly_Churners
- **Type:** Measure
- **Purpose:** Calculates the monthly revenue from churners.
- **DAX Formula:**
```
Revenue_Monthly_Churners = [Churn_Rate] * [Revenue_Monthly_Charges_Total]
```
- **Used in:** 
    - Overview
        - Revenue Lost Due to Churn

---

#### Revenue_Running_Total
- **Type:** Measure
- **Purpose:** Calculates the actual revenue running total of Databel.
- **DAX Formula:**
```
Revenue_Running_Total = SUM('Databel - Data'[Total Charges])
```
- **Used in:** 
    - Past Speculations
        - Current Revenue

---

#### Revenue_Shrinking_Rate
- **Type:** Measure
- **Purpose:** Calculates the proportion which the company's revenue is shrinking due to churning.
- **DAX Formula:**
```
Revenue_Shrinking_Rate = DIVIDE([Current_Revenue_Monthly_Churner_Sum], [Revenue_Monthly_Charges_Total])
```
- **Used in:** 
    - Overview
        - Monthly Revenue: Current vs From Churners

---

#### ServiceCalls_Average
- **Type:** Measure
- **Purpose:** Calculates the average amount of service calls per customer.
- **DAX Formula:**
```
ServiceCalls_Average = AVERAGE('Databel - Data'[Customer Service Calls])
```
- **Used in:** 
    - Customer Behavior
        - Service Calls Average by Churn Status

---

### Churn Rate Percentage

<span style="background-color: #019219; color: white; padding: 0.2em 0.4em; border-radius: 3px;">This table contains the churn rate related slicer used in the speculation pages of this project.</span>

---

#### Slicer_Selected_Churn_Rate_Percentage
- **Type:** Measure
- **Purpose:** Filters the churn rate based on user selection to provide custom speculations.
- **DAX Formula:**
```
Slicer_Selected_Churn_Rate_Percentage = SELECTEDVALUE('Churn Rate Percentage'[Slicer_Churn_Rate])
```
- **Used in:** 
    - Past Speculations
        - Churn Rate Percentage Value

---

#### Slicer_Churn_Rate
- **Type:** Calculated Column
- **Purpose:** Defines a range of churn rate options (from 0 to the actual churn rate) for user selection.
- **DAX Formula:**
```
Churn Rate Percentage = GENERATESERIES(0.0000, 0.2686, 0.0001)
```
- **Used in:** 
    - Past Speculations
        - Select Churn Rate
    - Future Speculations
        - Select Churn Rate

---

### Databel - Data

<span style="background-color: #010392; color: white; padding: 0.2em 0.4em; border-radius: 3px;">This table is the core dataset of this project and contains all Databel's customers information.</span>

---

#### Extra Charged
- **Type:** Calculated Column
- **Purpose:** Identifies whether a customer has incurred extra charges, such as for exceeding data usage or international usage.
- **DAX Formula:**
```
Extra Charged = IF(OR('Databel - Data'[Extra Data Charges]<>0, 'Databel - Data'[Extra International Charges]<>0), "Yes", "No")
```
- **Used in:** 
    - Customer Behavior
        - Churners by Extra Charges

---

#### Plans
- **Type:** Calculated Column
- **Purpose:** Categorizes customers based on their selected plans, combining options like unlimited data or international usage if they have both.
- **DAX Formula:**
```
= Table.AddColumn(#"Replaced Value1",
"Plans",
    each if ([Unlimited Data Plan] = "Yes" and [Intl Plan] = "Yes" )
        then "International and Unlimited Data Plan"

    else if ([Unlimited Data Plan] = "Yes" and [Intl Plan] = "No")
        then "Unlimited Data Plan"

    else if ([Unlimited Data Plan] = "No" and [Intl Plan] = "Yes")
        then "International Plan"

    else "No additional plans
")
```
- **Used in:** 
    - Churn Overview
        - Plans

---

### Months

<span style="background-color: #7a6401; color: white; padding: 0.2em 0.4em; border-radius: 3px;">This table contains the months slicer used in the past speculation report page.</span>

---

#### Slicer_Selected_Months
- **Type:** Measure
- **Purpose:** Filters the range of months selected for future speculations, with a default value of 24 months.
- **DAX Formula:**
```
Slicer_Selected_Months = SELECTEDVALUE('Months'[Slicer_Months], 24)
```
- **Used by:** 
    - `Customer_NoLongerChurner_AccountLength_Average`
    - `Revenue_NoLongerChurner`

---

#### Slicer_Months
- **Type:** Calculated Column
- **Purpose:** Generates a series of month numbers used for selecting a range of months used in the past speculation page.
- **DAX Formula:**
```
Months = GENERATESERIES(1, 24, 1)
```
- **Used in:** 
    - `Slicer_Selected_Months`
    
---

### Speculations Future

<span style="background-color: #ff0062; color: white; padding: 0.2em 0.4em; border-radius: 3px;">This table contains the measures used to speculate churning and revenue decrease in the future.</span>

---

#### Churn_Rate_Monthly
- **Type:** Measure
- **Purpose:** Calculates the monthly churn rate for use in future speculations.
- **DAX Formula:**
```
Churn_Rate_Monthly = 
DIVIDE([Slicer_Selected_Churn_Rate_Percentage], 18)
```
- **Used by:** 
    - `Future_Customer_Remaining_Churnable`

---

#### Customer_Active_ExpectedToChurn
- **Type:** Measure
- **Purpose:** Calculates the expected number of active customers that will churn in the future based on the current churn rate.
- **DAX Formula:**
```
Customer_Active_ExpectedToChurn = [Customer_Active] * [Churn_Rate] 
```
- **Used by:**
    - `Future_Customer_Churned`
    - `Future_Customer_Churned_Monthly`
    - `Future_Customer_Remaining_Churnable`
    - `Future_Customer_Stable`

---

#### Future_Customer_Churned
- **Type:** Measure
- **Purpose:** Calculates the total customers that churned in the future speculation.
- **DAX Formula:**
```
Future_Customer_Churned = 
[Customer_Active_ExpectedToChurn] - [Future_Customer_Remaining_Churnable]
```
- **Used in:** 
    - Future Speculations
        - Total Customers Churners

---

#### Future_Customer_Churned_Monthly
- **Type:** Measure
- **Purpose:** Calculates the number of churned customers each month based on the difference in churnable customers between the current and previous month.
- **DAX Formula:**
```
Future_Customer_Churned_Monthly = 
VAR MonthNum = MAX('Speculations Future'[MonthNumber])

VAR CurrentCustomers = [Future_Customer_Remaining_Churnable]

VAR PrevCustomers =
    IF(
        MonthNum = 1,
        [Customer_Active_ExpectedToChurn],
        CALCULATE(
            [Future_Customer_Remaining_Churnable],
            'Speculations Future'[MonthNumber] = MonthNum - 1
        )
    )
RETURN
    PrevCustomers - CurrentCustomers
```
- **Used by:** 
    - `Revenue_Lost_MonthlyCohort`

---

#### Future_Customer_Remaining_Churnable
- **Type:** Measure
- **Purpose:** Estimates the number of churnable customers remaining in future speculations, adjusted for the monthly churn rate.
- **DAX Formula:**
```
Future_Customer_Remaining_Churnable = 
VAR MonthNum = MAX('Speculations Future'[MonthNumber])

VAR BaseCustomers = [Customer_Active_ExpectedToChurn]

VAR Rate = [Churn_Rate_Monthly]

RETURN
    BaseCustomers * POWER(1 - Rate, MonthNum - 1)
```
- **Used by:** 
    - `Future_Customer_Remaining_Total`
    - `Future_Customer_Churned`
    - `Future_Customer_Churned_Monthly`

---

#### Future_Customer_Remaining_Total
- **Type:** Measure
- **Purpose:** Calculates how many active customers are left in the future speculation.
- **DAX Formula:**
```
Future_Customer_Remaining_Total = [Future_Customer_Stable] + [Future_Customer_Remaining_Churnable]
```
- **Used by:** 
    - `Future_Customer_Remaining_Total`

---

#### Future_Customer_Stable
- **Type:** Measure
- **Purpose:** Calculates how many active customers are expected not to churn based on the current churn rate.
- **DAX Formula:**
```
Future_Customer_Stable = [Customer_Active] - [Customer_Active_ExpectedToChurn]
```
- **Used by:** 
    - `Future_Customer_Remaining_Total`

---

#### Label_Revenue_Decrease_Absolute_Percentage
- **Type:** Measure
- **Purpose:** Displays the monthly revenue decrease as both an absolute value (in currency) and a percentage, comparing initial and final revenue figures.
- **DAX Formula:**
```
Label_Revenue_Decrease_Absolute_Percentage = 
VAR InitialRevenue = [Revenue_Monthly_Current_Speculated]

VAR FinalRevenue = [Revenue_Monthly_Future_Speculated]

VAR Diff = InitialRevenue - FinalRevenue

VAR Pct = DIVIDE(Diff, InitialRevenue)

RETURN
    FORMAT(Diff, "Currency") & " (" & FORMAT(Pct, "0.0%") & ")"
```
- **Used in:** 
    - Future Speculations
        - Monthly Revenue Decreased by

---

#### Revenue_Churners_Stayed_Total
- **Type:** Measure
- **Purpose:** Calculates the total revenue if the churners had stayed in the future speculation.
- **DAX Formula:**
```
Revenue_Churners_Stayed_Total = [Revenue_Remaining_Total] + [Revenue_Lost_Total]
```
- **Used in:** 
    - Future Speculations
        - Total Lost Revenue

---

#### Revenue_Lost_Total
- **Type:** Measure
- **Purpose:** Calculates the total revenue lost from churners in the future speculation.
- **DAX Formula:**
```
Revenue_Lost_Total = 
SUMX(
    - Values('Speculations Future'[MonthNumber]),
    [Revenue_Lost_MonthlyCohort]
)
```
- **Used in:** 
    - Future Speculations
        - Total Lost Revenue
        - Total Revenue Lost by Months

---

#### Revenue_Lost_MonthlyCohort
- **Type:** Measure
- **Purpose:** Estimates the revenue lost for each cohort of churned customers, considering the number of months they would have remained active and their average monthly revenue, based on future churn speculations.
- **DAX Formula:**
```
Revenue_Lost_MonthlyCohort = 
VAR MonthNum = MAX('Speculations Future'[MonthNumber])

VAR MaxMonth =
    MAXX(ALLSELECTED('Speculations Future'), 'Speculations Future'[MonthNumber])

VAR RemainingMonths = MaxMonth - MonthNum

VAR Churned = [Future_Customer_Churned_Monthly]

VAR AvgRevenue = [Revenue_Monthly_Average]

RETURN
    Churned * RemainingMonths * AvgRevenue
```
- **Used by:**
    - `Revenue_Lost_Total`

---

#### Revenue_Monthly_Current_Speculated
- **Type:** Measure
- **Purpose:** Estimates the company's current total monthly revenue from active customers, based on the average monthly charge.
- **DAX Formula:**
```
Revenue_Monthly_Current_Speculated = [Customer_Active] * [Revenue_Monthly_Average]
```
- **Used in:** 
    - Overview
        - Current Monthly Revenue
        - Monthly Revenue: Current vs From Churners
    - Future Speculation
        - Monthly Revenue: Future Speculation vs Current

---

#### Revenue_Monthly_Future_Speculated
- **Type:** Measure
- **Purpose:** Estimates the company's total monthly revenue from active customers, projected based on future speculations.
- **DAX Formula:**
```
Revenue_Monthly_Future_Speculated = [Future_Customer_Remaining_Total] * [Revenue_Monthly_Average]
```
- **Used in:** 
    - Future Speculations
        - Monthly Revenue: Future Speculation vs Current

---

#### Revenue_Remaining_Total
- **Type:** Measure
- **Purpose:** Calculates the total remaining revenue from active customers in future speculations.
- **DAX Formula:**
```
Revenue_Remaining_Total = 
[Future_Customer_Remaining_Total] * [Revenue_Monthly_Average] * MAX('Speculations Future'[MonthNumber])
```
- **Used in:** 
    - Future Speculations
        - Total Surviving Revenue

---

#### MonthNumber
- **Type:** Calculated Column
- **Purpose:** Holds the month numbers for the future speculations.
- **DAX Formula:**
```
Speculations Future = GENERATESERIES(1, 48, 1)
```
- **Used in:** 
    - Future Speculations
        - Select a Month Range

---

### Speculations Past

<span style="background-color: #7bbd00; color: white; padding: 0.2em 0.4em; border-radius: 3px;">This table contains the measures used to show how churning affected revenue in the past.</span>

---

#### Customer_NoLongerChurner
- **Type:** Measure
- **Purpose:** Calculates the number of customers who have stopped being churners in the past speculation period.
- **DAX Formula:**
```
Customer_NoLongerChurner = [Customer_Churned] - [Customer_StillChurner]
```
- **Used in:** 
    - Past Speculations
        - Churners No Longer
        - Revenue From No Longer Churners Staying Extra Months

---

#### Customer_NoLongerChurner_AccountLength_Average
- **Type:** Measure
- **Purpose:** Calculates the average account length for customers who are no longer churners, based on past speculation.
- **DAX Formula:**
```
Customer_NoLongerChurner_AccountLength_Average = [Customer_Churned_AccountLength_Average] + Months[Slicer_Selected_Months]
```
- **Used in:** 
    - Past Speculations
        - (Account Length Average) No Longer Churner

---

#### Customer_StillChurner
- **Type:** Measure
- **Purpose:** Calculates the number of customers still considered churners in the past speculation period.
- **DAX Formula:**
```
Customer_StillChurner = [Customer_All] * 'Churn Rate Percentage'[Slicer_Selected_Churn_Rate_Percentage] 
```
- **Used in:** 
    - Past Speculations
        - Churners Still

---

#### Revenue_Growth_Percentage
- **Type:** Measure
- **Purpose:** Calculates the revenue growth percentage due to reduced churn in the past speculation period.
- **DAX Formula:**
```
Revenue_Growth_Percentage = ([Revenue_NoLongerChurner_Active_Sum] / [Revenue_Running_Total]) - 1.0
```
- **Used in:** 
    - Past Speculations
        - Revenue Churners Staying

---

#### Revenue_NoLongerChurner
- **Type:** Measure
- **Purpose:** Calculates the revenue generated from customers who are no longer churners in the past speculation period, factoring in their average charges and additional months of retention.
- **DAX Formula:**
```
Revenue_NoLongerChurner = IF([Customer_NoLongerChurner]>0, [Customer_NoLongerChurner] * [Customer_Churned_Charges_Average] * Months[Slicer_Selected_Months], 0)
```
- **Used in:** 
    - Past Speculations
        - Revenue Churners Staying
        - Revenue From No Longer Churners Staying Extra Months

---

#### Revenue_NoLongerChurner_Active_Sum
- **Type:** Measure
- **Purpose:** Calculates the sum of the current running total revenue and the revenue generated if churners had stayed in the past speculation period.
- **DAX Formula:**
```
Revenue_NoLongerChurner_Active_Sum = _Measures[Revenue_Running_Total] + [Revenue_NoLongerChurner] 
```
- **Used in:** 
    - Past Speculations
        - Current Revenue + Revenue Churners Staying

---