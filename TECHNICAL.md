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
Data field: Total Customers

### Churn Rate %
type: Card 2
Data field: Churn Rate

### Customers Churned
type: Card 3
Data field: Churned Customers

### Current Monthly Revenue
type: Card 4
Data field: Current Monthly Total Revenue Speculated

### Revenue Lost Due to Churn
type: Card 5
Data field: Revenue Lost Due to Churn
Postfix Label: "/month"

### Monthly Revenue: Current vs From Churners
type: Pie Chart
Values: Current Monthly Total Revenue Speculated, Revenue Lost Due to Churn
Tooltips: Revenue Shrinking Rate

### Active vs Churned Customers by Contract Type
type: Clustered Column Chart 1
X-axis: Contract Type
Y-axis: Churned Customers, Customers Active Total

### Average Account Length (months)
type: Clustered Column Chart 2
Y-axis: Avg Churners Account Length, Avg Active Customers Account Length

### Average Monthly Charge
type: Card 6
Data field: Average Monthly Charge

### Average Churner Monthly Charge
type: Card 7
Data field: Avg Churners Charges

## Churn Overview

### Plans
type: 100% Stacked Bar Chart 1
Y-axis: Plans
X-axis: Churned Customers, Customers Active Total

### Payment Method
type: 100% Stacked Bar Chart 2
Y-axis: Payment Method
X-axis: Churned Customers, Customers Active Total

### Contract Type
type: Clustered Column Chart
Y-axis: Contract Type
X-axis: Churned Customers, Customers Active Total

### Customers in Groups
type: 100% Stacked Column Chart
Y-axis: Number of Customers in Group
X-axis: Churned Customers, Customers Active Total

## Customer Behaviour

### Service Calls Average by Churn Status
type: Funnel 1
Category: Churn Label
Values: Service Calls Average

### Churners by Extra Charges
type: Stacked Column Chart
X-axis: Extra Charged
Y-axis: Churned Customers

### Average Account Length
type: Clustered Bar Chart
X-axis: Avg Active Customers Account Length, Avg Churners Account Length

### Average Monthly Charge by Churn Status
type: Funnel 2
Category: Churn Label
Values: Average Monthly Charge

## Geographic Analysis

### Total Churned Customers by States
type: Map
Location: StateLongName
Bubble size: Churned Customers
Tooltips: Average Monthly Charge, Churn Rate

### Top 5 Highest Churned Customers States
type: Stacked Bar Chart
Y-axis: StateLongName
X-axis: Churned Customers
Filters: StateLongName Top 5 Churned Customers

### Top 5 Highest Churn Rate States
type: Funnel
Category: StateLongName
Values: Churn Rate

### Churn Rate by States
type: Filled Map
Location: StateLongName
Tooltips: Churn Rate, Average Monthly Charge, Churned Customers
Filters: StateLongName Top 5 Churn Rate

## Churn Reasons

### Churned Customers by Categories
type: Stacked Bar Chart 1
Y-axis: Churn Category
X-axis: Churned Customers
Tooltips: Churn Rate by Category

### Churned Customers by Churn Reason
type: Treemap
Category: Churn Reason
Values: Churned Customers
Filters: Churn Reason Top 5 Customers

### Churn Category and Reason Breakdown
type: Stacked Bar Chart 2
Y-axis: Churn Category, Churn Reason
X-axis: Churned Customers
Drill-down: active

## Past Speculations

### Churn Rate Percentage Value
type: Card 1
Data field: Churn Rate Percentage Value

### Select Churn Rate
type: Slicer
Field: Churn Rate Percentage

### Revenue Churners Staying
type: Card 2
Data field: Revenue Churners Staying
Tooltip fields: % Total Revenue Growth

### Current Revenue + Revenue Churners Staying
type: Card 3
Data field: Total Revenue Churners Staying plus Active

### Current Revenue
type: Card 4
Data field: Revenue Running Total

### Churned Customers
type: Card 5
Data field: Churned Customers

### Churners No Longer
type: Card 6
Data field: Churners No Longer

### Churners Still
type: Card 7
Data field: Churners Still

### Average Account Length (months)
type: Textbox

### Active Customer 
type: Card 8
Data field: Avg Active Customers Account Length

### Churned Customer
type: Card 9
Data field: Avg Churners Account Length

### No Longer Churner
type: Card 10
Data field: Avg No Longer Churners Account Length

### Revenue From No Longer Churners Staying Extra Months
type: Line and Clustered Column Chart
X-axis: Months
Column y-axis: Churners No Longer, Churned Customers
Line y-axis: Revenue Churners Staying
Tooltips: Average of Account Length (in months)

## Future Speculations

### Select Churn Rate
type: Slicer 1
Field: Churn Rate Percentage

### Select a Month Range
type: Slicer 2
Field: Month Number

### Total Revenue Lost by Months
type: Stacked Column Chart
X-axis: Month Number (bins)
Y-axis: Total Revenue Lost

### Monthly Revenue Decreased by
type: Card 1
Value: Revenue Decrease Label

### Churn Rate %
type: Card 2
Value: Churn Rate Percentage Value

### Monthly Revenue: Future Speculation vs Current
type: Line Chart
X-axis: Month Number
Y-axis: Monthly Revenue, Current Monthly Total Revenue Speculated

### Total Lost Revenue
type: Card 3
Value: Total Revenue Lost
Tooltips: Total Revenue If Churners Stayed

### Total Surviving Revenue
type: Card 4
Value: Total Revenue Remaining

### Total Customers Churners
type: Card 5
Data field: Total Customers Churned

### Customers Remaining (Total)
type: Card 6
Data field: Customers Remaining (Total)



## Tables and Measures/Columns

### _Measures

#### Measures

Average Monthly Charge
```DAX
Average Monthly Charge = AVERAGE('Databel - Data'[Monthly Charge])
```

Avg Active Charges
```DAX
Avg Active Charges = CALCULATE(AVERAGE('Databel - Data'[Monthly Charge]), 'Databel - Data'[Churn Label]="No") 
```

Avg Active Customers Account Length
```DAX
Avg Active Customers Account Length = CALCULATE(AVERAGE('Databel - Data'[Account Length (in months)]), 'Databel - Data'[Churn Label]="No")
```

Avg Churners Account Length
```DAX
Avg Churners Account Length = CALCULATE(AVERAGE('Databel - Data'[Account Length (in months)]), 'Databel - Data'[Churn Label]="Yes")
```

Avg Churners Charges
```DAX
Avg Churners Charges = CALCULATE(AVERAGE('Databel - Data'[Monthly Charge]), 'Databel - Data'[Churn Label]="Yes") 
```

Churn Rate
```DAX
Churn Rate = DIVIDE([Churned Customers], [Total Customers])
```

Churn Rate by Category
```DAX
Churn Rate by Category = 
DIVIDE(
    [Churned Customers],
    CALCULATE(
        [Churned Customers],
        ALL('Databel - Data')   -- ignore any filters like Churn Category
    )
)
```

Churned Customers
```DAX
Churned Customers = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Churn Label] = "Yes")
```

Competitor Churn %
```DAX
Competitor Churn % = 
DIVIDE(
    CALCULATE([Churned Customers], 'Databel - Data'[Churn Category] = "Competitor"),
    [Churned Customers]
)
```

Customers Active Total
```DAX
Customers Active Total = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Churn Label] = "No")
```

Customers Churned Average Per Account Length
```DAX
Customers Churned Average Per Account Length = DIVIDE([Churned Customers], [Total Customers])
```

Customers Total
```DAX
Customers Total = COUNTROWS('Databel - Data')   
```

Monthly Charge Active Total
```DAX
Monthly Charge Active Total = CALCULATE(SUM('Databel - Data'[Monthly Charge]), 'Databel - Data'[Churn Label]="No")
```

Monthly Charge Average
```DAX
Monthly Charge Average = AVERAGE('Databel - Data'[Monthly Charge])
```

Monthly Charge Total
```DAX
Monthly Charge Total = SUM('Databel - Data'[Monthly Charge])
```

Monthly GB Average
```DAX
Monthly GB Average = AVERAGE('Databel - Data'[Avg Monthly GB Download])
```

Number of Unique Customers
```DAX
Number of Unique Customers = DISTINCTCOUNT('Databel - Data'[Customer ID]) 
```

Plan Intl
```DAX
Plan Intl = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Intl Plan] = "Yes") 
```

Plan Unlimited
```DAX
Plan Unlimited = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Unlimited Data Plan] = "Yes")
```

Revenue Churners
```DAX
Revenue Churners = CALCULATE(SUM('Databel - Data'[Monthly Charge]), 'Databel - Data'[Churn Label]="Yes")
```

Revenue Lost Due to Churn
```DAX
Revenue Lost Due to Churn = [Churn Rate] * [Monthly Charge Total]
```

Revenue Running Total
```DAX
Revenue Running Total = SUM('Databel - Data'[Total Charges])
```

Revenue Shrinking Rate
```DAX
Revenue Shrinking Rate = DIVIDE([Revenue Churners], [Monthly Charge Total])
```

Revenue Shrinking Rate Monthly
```DAX
Revenue Shrinking Rate Monthly = DIVIDE([Revenue Churners], [Monthly Charge Total])
```

Revenue Total Monthly
```DAX
Revenue Total Monthly = SUM('Databel - Data'[Monthly Charge]) 
```

Service Calls Average
```DAX
Service Calls Average = AVERAGE('Databel - Data'[Customer Service Calls])
```

Total Customers
```DAX
Total Customers = COUNTROWS('Databel - Data')   
```

### Churn Rate Percentage

This is a parameter generated table

#### Measures

Churn Rate Percentage Value
```DAX
Churn Rate Percentage Value = SELECTEDVALUE('Churn Rate Percentage'[Churn Rate Percentage])
```

#### Calculated Columns

Churn Rate Percentage
```DAX
Churn Rate Percentage = GENERATESERIES(0.0000, 0.2686, 0.0001)
```

### Months

This is a parameter generated table

#### Measures

Months Value
```DAX
Months = GENERATESERIES(1, 24, 1)
```

#### Calculated Columns

Months
```DAX
Months Value = SELECTEDVALUE('Months'[Months], 24)
```

### Percentage

This is a parameter generated table

#### Measure

Percentage Value
```DAX
Percentage Value = SELECTEDVALUE('Percentage'[Percentage Churn Rate], 100)
```

#### Calculated Column

Percentage
```DAX
Percentage = GENERATESERIES(0.01, 1.01, 0.01)
```

Percentage Churn Rate
```DAX
Percentage Churn Rate = ([Churn Rate] * Percentage[Percentage])
```

### Speculations Future

#### Measures

Active Customers Expected to Churn
```DAX
Active Customers Expected to Churn = [Customers Active Total] * [Churn Rate] 
```

ARPU
```DAX
ARPU = [Average Monthly Charge]
```

Cumulative Revenue Loss
```DAX
Cumulative Revenue Loss = 
CALCULATE(
    SUMX(
        FILTER('Speculations Future', 'Speculations Future'[Month Number] <= MAX('Speculations Future'[Month Number])),
        [Monthly Revenue Loss]
    )
)
```

Current Monthly Total Revenue
```DAX
Current Monthly Total Revenue Speculated = [Customers Active Total] * [Average Monthly Charge]
```

Customers Churned
```DAX
Customers Churned = 
VAR MonthNum = MAX('Speculations Future'[Month Number])
VAR CurrentCustomers = [Customers Remaining (Churnable)]
VAR PrevCustomers =
    IF(
        MonthNum = 1,
        [Active Customers Expected to Churn],
        CALCULATE(
            [Customers Remaining (Churnable)],
            'Speculations Future'[Month Number] = MonthNum - 1
        )
    )
RETURN
    PrevCustomers - CurrentCustomers
```

Customers Remaining (Churnable)
```DAX
Customers Remaining (Churnable) = 
VAR MonthNum = MAX('Speculations Future'[Month Number])
VAR BaseCustomers = [Active Customers Expected to Churn]
VAR Rate = [Monthly Churn Rate]
RETURN
    BaseCustomers * POWER(1 - Rate, MonthNum - 1)
```

Customers Remaining (Total)
```DAX
Customers Remaining (Total) = 
[Customers Stable] + [Customers Remaining (Churnable)]
```

Customers Stable
```DAX
Customers Stable = 
[Customers Active Total] - [Active Customers Expected to Churn]
```

Monthly Churn Rate
```DAX
Monthly Churn Rate = 
DIVIDE([Churn Rate Percentage Value], 18)
```

Monthly Revenue
```DAX
Monthly Revenue = 
[Customers Remaining (Total)] * [Average Monthly Charge]
```

Monthly Revenue Loss
```DAX
Monthly Revenue Loss = 
VAR t = SELECTEDVALUE('Speculations Future'[Month Number])
VAR N0 = [Total Customers]
VAR MonthlyChurn = [Monthly Churn Rate]
VAR CustomersThisMonth = N0 * POWER(1 - MonthlyChurn, t-1) * MonthlyChurn
RETURN
CustomersThisMonth * [ARPU]
```

Revenue Decrease Label
```DAX
Revenue Decrease Label = 
VAR InitialRevenue = [Current Monthly Total Revenue Speculated]
VAR FinalRevenue = [Monthly Revenue]
VAR Diff = InitialRevenue - FinalRevenue
VAR Pct = DIVIDE(Diff, InitialRevenue)
RETURN
FORMAT(Diff, "Currency") & " (" & FORMAT(Pct, "0.0%") & ")"
```

Revenue Lost (Monthly Cohort)
```DAX
Revenue Lost (Monthly Cohort) = 
VAR MonthNum = MAX('Speculations Future'[Month Number])
VAR MaxMonth =
    MAXX(ALLSELECTED('Speculations Future'), 'Speculations Future'[Month Number])
VAR RemainingMonths = MaxMonth - MonthNum
VAR Churned = [Customers Churned]
VAR AvgRevenue = [ARPU]
RETURN
    Churned * RemainingMonths * AvgRevenue
```

Revenue Shrink %
```DAX
Revenue Shrink % = 
VAR InitialRevenue =
    [Customers Active Total] * [Average Monthly Charge]
VAR FinalRevenue =
    [Customers Remaining (Total)] * [Average Monthly Charge]
RETURN
    DIVIDE(InitialRevenue - FinalRevenue, InitialRevenue)
```

Total Customers Churned
```DAX
Total Customers Churned = 
[Active Customers Expected to Churn] - [Customers Remaining (Churnable)]
```

Total Revenue If Churners Stayed
```DAX
Total Revenue If Churners Stayed = [Total Revenue Remaining] + [Total Revenue Lost]
```

Total Revenue Lost
```DAX
Total Revenue Lost = 
SUMX(
    VALUES('Speculations Future'[Month Number]),
    [Revenue Lost (Monthly Cohort)]
)
```

Total Revenue Remaining
```DAX
Total Revenue Remaining = 
[Customers Remaining (Total)] * [Average Monthly Charge] * MAX('Speculations Future'[Month Number])
```

#### Calculated Columns

Month Number
```DAX
Speculations Future = GENERATESERIES(1, 48, 1)
```


### Speculations Past

#### Measures

% Total Revenue Growth
```DAX
% Total Revenue Growth = ([Total Revenue Churners Staying plus Active] / [Revenue Running Total]) - 1.0
```

Avg No Longer Churners Account Length

```DAX
Avg No Longer Churners Account Length = [Avg Churners Account Length] + Months[Months Value]
```

Churners No Longer
```DAX
Churners No Longer = [Churned Customers] - [Churners Still]
```

Churners Still
```DAX
Churners Still = [Total Customers] * 'Churn Rate Percentage'[Churn Rate Percentage Value] 
```

Revenue Churners Staying
```DAX
Revenue Churners Staying = IF([Churners No Longer]>0, [Churners No Longer] * [Avg Churners Charges] * Months[Months Value], 0)
```

Total Revenue Churners Staying plus Active
```DAX
Total Revenue Churners Staying plus Active = _Measures[Revenue Running Total] + [Revenue Churners Staying] 
```
### Calculated Columns
Month Number
```DAX
Speculations Past = GENERATESERIES(1, 24, 1)
```