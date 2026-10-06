# DAX Measures

The following measures are documented in the analysis report.

## Churn Rate

```DAX
Churn Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS('Customers'),
        'Customers'[Churn] = 1
    ),
    COUNTROWS('Customers')
)
```

## Total Revenue

```DAX
Total Revenue =
SUM('Customers'[Total Spend])
```

## Revenue at Risk

```DAX
Revenue at Risk =
CALCULATE(
    SUM('Customers'[Total Spend]),
    'Customers'[Churn] = 1
)
```

## % Revenue at Risk

```DAX
% Revenue at Risk =
DIVIDE(
    [Revenue at Risk],
    [Total Revenue]
)
```

## Average Support Calls — Churned

```DAX
Avg Support Calls (Churned) =
CALCULATE(
    AVERAGE('Customers'[Support Calls]),
    'Customers'[Churn] = 1
)
```

## High-Risk Customers

```DAX
High-Risk Customers =
CALCULATE(
    COUNTROWS('Customers'),
    'Customers'[Support Calls] >= 7,
    'Customers'[Payment Delay] >= 20
)
```

## Notes

The measures above reproduce the KPI definitions documented in the supplied analysis report.
