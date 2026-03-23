### Measure: Churned Customers
- **Type:** Measure
- **Purpose:** Counts the number of customers who have churned (Churn Label = Yes).
- **DAX Formula:**
```
Churned Customers = COUNTROWS(FILTER(Customers, Customers[Churn Label] = "Yes"))
```
- **Used in:** Churn Overview dashboard, Churn Reasons treemap, Revenue Impact calculations


# pages

## Overview

Let's show the visuals, the title being the visuals actual titles

### Total Customers
type: Card 1
Data field: Customer_Total

### Churn Rate %
type: Card 2
Data field: Churn_Rate

### Customers Churned
type: Card 3
Data field: Customers_Churned

### Current Monthly Revenue
type: Card 4
Data field: Revenue_Monthly_Current_Speculated

### Revenue Lost Due to Churn
type: Card 5
Data field: Revenue_Monthly_Churners
Postfix Label: "/month"

### Monthly Revenue: Current vs From Churners
type: Pie Chart
Values: Revenue_Monthly_Current_Speculated, Revenue_Monthly_Churners
Tooltips: Revenue Shrinking Rate

### Active vs Churned Customers by Contract Type
type: Clustered Column Chart 1
X-axis: Contract Type
Y-axis: Customers_Churned, Customers_Active

### Average Account Length (months)
type: Clustered Column Chart 2
Y-axis: Customer_Churned_AccountLength_Average, Customer_Active_AccountLength_Average

### Average Monthly Charge
type: Card 6
Data field: Revenue_Monthly_Average

### Average Churner Monthly Charge
type: Card 7
Data field: Customer_Churned_Charges_Average

## Churn Overview

### Plans
type: 100% Stacked Bar Chart 1
Y-axis: Plans
X-axis: Customers_Churned, Customers_Active
Tooltips: GB_Monthly_Average

### Payment Method
type: 100% Stacked Bar Chart 2
Y-axis: Payment Method
X-axis: Customers_Churned, Customers_Active

### Contract Type
type: Clustered Column Chart
Y-axis: Contract Type
X-axis: Customers_Churned, Customers_Active

### Customers in Groups
type: 100% Stacked Column Chart
Y-axis: Number of Customers in Group
X-axis: Customers_Churned, Customers_Active

## Customer Behaviour

### Service Calls Average by Churn Status
type: Funnel 1
Category: Churn Label
Values: Service Calls Average

### Churners by Extra Charges
type: Stacked Column Chart
X-axis: Extra Charged
Y-axis: Customers_Churned

### Average Account Length
type: Clustered Bar Chart
X-axis: Avg Active Customers Account Length, Avg Churners Account Length

### Average Monthly Charge by Churn Status
type: Funnel 2
Category: Churn Label
Values: Revenue_Monthly_Average

## Geographic Analysis

### Total Churned Customers by States
type: Map
Location: StateLongName
Bubble size: Customers_Churned
Tooltips: Revenue_Monthly_Average, Churn_Rate

### Top 5 Highest Churned Customers States
type: Stacked Bar Chart
Y-axis: StateLongName
X-axis: Customers_Churned
Filters: StateLongName Top 5 Customers_Churned

### Top 5 Highest Churn Rate States
type: Funnel
Category: StateLongName
Values: Churn_Rate

### Churn Rate by States
type: Filled Map
Location: StateLongName
Tooltips: Churn_Rate, Revenue_Monthly_Average, Customers_Churned
Filters: StateLongName Top 5 Churn_Rate

## Churn Reasons

### Churned Customers by Categories
type: Stacked Bar Chart 1
Y-axis: Churn Category
X-axis: Customers_Churned
Tooltips: Churn_Category_Rate

### Churned Customers by Churn Reason
type: Treemap
Category: Churn Reason
Values: Customers_Churned
Filters: Churn Reason Top 5 Customers

### Churn Category and Reason Breakdown
type: Stacked Bar Chart 2
Y-axis: Churn Category, Churn Reason
X-axis: Customers_Churned
Drill-down: active

## Past Speculations

### Churn Rate Percentage Value
type: Card 1
Data field: Slicer_Selected_Churn_Rate_Percentage

### Select Churn Rate
type: Slicer
Field: Slicer_Churn_Rate

### Revenue Churners Staying
type: Card 2
Data field: Revenue_NoLongerChurner
Tooltip fields: Revenue_Growth_Percentage

### Current Revenue + Revenue Churners Staying
type: Card 3
Data field: Revenue_NoLongerChurner_Active_Sum

### Current Revenue
type: Card 4
Data field: Revenue_Running_Total

### Churned Customers
type: Card 5
Data field: Customers_Churned

### Churners No Longer
type: Card 6
Data field: Customer_NoLongerChurner

### Churners Still
type: Card 7
Data field: Customer_StillChurner

### Average Account Length (months)
type: Textbox

### Active Customer 
type: Card 8
Data field: Customer_Active_AccountLength_Average

### Churned Customer
type: Card 9
Data field: Customer_Churned_AccountLength_Average

### No Longer Churner
type: Card 10
Data field: Customer_NoLongerChurner_AccountLength_Average

### Revenue From No Longer Churners Staying Extra Months
type: Line and Clustered Column Chart
X-axis: Slicer_Months
Column y-axis: Customer_NoLongerChurner, Customers_Churned
Line y-axis: Revenue_NoLongerChurner
Tooltips: Average of Account Length (in months)

## Future Speculations

### Select Churn Rate
type: Slicer 1
Field: Slicer_Churn_Rate

### Select a Month Range
type: Slicer 2
Field: MonthNumber

### Total Revenue Lost by Months
type: Stacked Column Chart
X-axis: MonthNumber(bins)
Y-axis: Revenue_Lost_Total

### Monthly Revenue Decreased by
type: Card 1
Value: Label_Revenue_Decrease_Absolute_Percentage

### Churn Rate %
type: Card 2
Value: Slicer_Selected_Churn_Rate_Percentage

### Monthly Revenue: Future Speculation vs Current
type: Line Chart
X-axis: MonthNumber
Y-axis: Revenue_Monthly_Future_Speculated, Revenue_Monthly_Current_Speculated

### Total Lost Revenue
type: Card 3
Value: Revenue_Lost_Total
Tooltips: Revenue_Churners_Stayed_Total

### Total Surviving Revenue
type: Card 4
Value: Revenue_Remaining_Total

### Total Customers Churners
type: Card 5
Data field: Future_Customer_Churned

### Customers Remaining (Total)
type: Card 6
Data field: Future_Customer_Remaining_Total

# Tables and Measures/Columns

## _Measures

### Measures



#### Churn_Category_Rate
- **Type:** Measure
- **Purpose:** Calculates the Churn Rate without filtering.
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
- **Used in:** Churn Customers by Categories

#### Churn_Rate
- **Type:** Measure
- **Purpose:** Calculates the churn rate for the entire dataset
- **DAX Formula:**
```
Churn_Rate = DIVIDE([Customer_Churned], [Customer_All])
```
- **Used in:** many visuals



Current_Revenue_Monthly_Churner_Sum = CALCULATE(SUM('Databel - Data'[Monthly Charge]), 'Databel - Data'[Churn Label]="Yes")

Customer_Active = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Churn Label] = "No")

Customer_Active_AccountLength_Average = CALCULATE(AVERAGE('Databel - Data'[Account Length (in months)]), 'Databel - Data'[Churn Label]="No")

Customer_All = COUNTROWS('Databel - Data')   

Customer_Churned = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Churn Label] = "Yes")

Customer_Churned_AccountLength_Average = CALCULATE(AVERAGE('Databel - Data'[Account Length (in months)]), 'Databel - Data'[Churn Label]="Yes")

Customer_Churned_Charges_Average = CALCULATE(AVERAGE('Databel - Data'[Monthly Charge]), 'Databel - Data'[Churn Label]="Yes") 

GB_Monthly_Average = AVERAGE('Databel - Data'[Avg Monthly GB Download])

Revenue_Monthly_Average = AVERAGE('Databel - Data'[Monthly Charge])

Revenue_Monthly_Charges_Total = SUM('Databel - Data'[Monthly Charge])

Revenue_Monthly_Churners = [Churn_Rate] * [Revenue_Monthly_Charges_Total]

Revenue_Running_Total = SUM('Databel - Data'[Total Charges])

Revenue_Shrinking_Rate = DIVIDE([Current_Revenue_Monthly_Churner_Sum], [Revenue_Monthly_Charges_Total])

ServiceCalls_Average = AVERAGE('Databel - Data'[Customer Service Calls])

## Churn Rate Percentage

### Measures

Slicer_Selected_Churn_Rate_Percentage = SELECTEDVALUE('Churn Rate Percentage'[Slicer_Churn_Rate])

### Calculated Columns

Slicer Churn Rate
```DAX
Churn Rate Percentage = GENERATESERIES(0.0000, 0.2686, 0.0001)
```

## Databel - Data

### Calculated Columns

Extra Charged
```DAX
Extra Charged = IF(OR('Databel - Data'[Extra Data Charges]<>0, 'Databel - Data'[Extra International Charges]<>0), "Yes", "No")
```

Plans
```DAX
= Table.AddColumn(#"Replaced Value1", "Plans", each if ([Unlimited Data Plan] = "Yes" and [Intl Plan] = "Yes" ) then "International and Unlimited Data Plan" else if ([Unlimited Data Plan] = "Yes" and [Intl Plan] = "No") then "Unlimited Data Plan" else if ([Unlimited Data Plan] = "No" and [Intl Plan] = "Yes") then "International Plan" else "No additional plans
")
```

## Months

### Measures

Slicer_Selected_Months = SELECTEDVALUE('Months'[Slicer_Months], 24)

### Calculated Columns

Slicer_Months
```DAX
Months = GENERATESERIES(1, 24, 1)
```

## Percentage

### Measures

Slicer_Percentage_Churn_Rate = ([Churn_Rate] * Percentage[Slicer_Percentage])

Slicer_Selected_Percentage = SELECTEDVALUE('Percentage'[Slicer_Percentage_Churn_Rate], 100)

### Calculated Columns

Slicer_Percentage
```DAX
Percentage = GENERATESERIES(0.01, 1.01, 0.01)
```


## Speculations Future

### Measures

Churn_Rate_Monthly = 
DIVIDE([Slicer_Selected_Churn_Rate_Percentage], 18)

Customer_Active_ExpectedToChurn = [Customer_Active] * [Churn_Rate] 

Future_Customer_Churned = 
[Customer_Active_ExpectedToChurn] - [Future_Customer_Remaining_Churnable]

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

Future_Customer_Remaining_Churnable = 
VAR MonthNum = MAX('Speculations Future'[MonthNumber])
VAR BaseCustomers = [Customer_Active_ExpectedToChurn]
VAR Rate = [Churn_Rate_Monthly]
RETURN
    BaseCustomers * POWER(1 - Rate, MonthNum - 1)

Future_Customer_Remaining_Total = 
[Future_Customer_Stable] + [Future_Customer_Remaining_Churnable]

Future_Customer_Stable = 
[Customer_Active] - [Customer_Active_ExpectedToChurn]

Label_Revenue_Decrease_Absolute_Percentage = 
VAR InitialRevenue = [Revenue_Monthly_Current_Speculated]
VAR FinalRevenue = [Revenue_Monthly_Future_Speculated]
VAR Diff = InitialRevenue - FinalRevenue
VAR Pct = DIVIDE(Diff, InitialRevenue)
RETURN
FORMAT(Diff, "Currency") & " (" & FORMAT(Pct, "0.0%") & ")"

Revenue_Churners_Stayed_Total = [Revenue_Remaining_Total] + [Revenue_Lost_Total]

Revenue_Lost_Total = 
SUMX(
    VALUES('Speculations Future'[MonthNumber]),
    [Revenue_Lost_MonthlyCohort]
)

Revenue_Lost_MonthlyCohort = 
VAR MonthNum = MAX('Speculations Future'[MonthNumber])
VAR MaxMonth =
    MAXX(ALLSELECTED('Speculations Future'), 'Speculations Future'[MonthNumber])
VAR RemainingMonths = MaxMonth - MonthNum
VAR Churned = [Future_Customer_Churned_Monthly]
VAR AvgRevenue = [Revenue_Monthly_Average]
RETURN
    Churned * RemainingMonths * AvgRevenue

Revenue_Monthly_Current_Speculated = [Customer_Active] * [Revenue_Monthly_Average]

Revenue_Monthly_Future_Speculated = 
[Future_Customer_Remaining_Total] * [Revenue_Monthly_Average]

Revenue_Remaining_Total = 
[Future_Customer_Remaining_Total] * [Revenue_Monthly_Average] * MAX('Speculations Future'[MonthNumber])

### Calculated Columns

MonthNumber
```DAX
Speculations Future = GENERATESERIES(1, 48, 1)
```

## Speculations Past

### Measures

Customer_NoLongerChurner = [Customer_Churned] - [Customer_StillChurner]

Customer_NoLongerChurner_AccountLength_Average = [Customer_Churned_AccountLength_Average] + Months[Slicer_Selected_Months]

Customer_StillChurner = [Customer_All] * 'Churn Rate Percentage'[Slicer_Selected_Churn_Rate_Percentage] 

Revenue_Growth_Percentage = ([Revenue_NoLongerChurner_Active_Sum] / [Revenue_Running_Total]) - 1.0

Revenue_NoLongerChurner = IF([Customer_NoLongerChurner]>0, [Customer_NoLongerChurner] * [Customer_Churned_Charges_Average] * Months[Slicer_Selected_Months], 0)

Revenue_NoLongerChurner_Active_Sum = _Measures[Revenue_Running_Total] + [Revenue_NoLongerChurner] 

### Calculated Columns

MonthNumber
```DAX
Speculations Past = GENERATESERIES(1, 24, 1)
```