I am excited to share the recent dashboard I developed as part of my virtual internship on Power BI, provided by PwC through Forage.

Problem Statement:
The objective was to provide the client with insights into customer churn.

Customers in the telecom industry can easily switch between operators and have access to a wide range of service providers. In this highly competitive environment, the telecommunications industry frequently experiences high annual customer churn rates. As a result, it has become crucial for organizations to analyze customer turnover and identify the underlying causes.

To address this challenge, it was necessary to analyze and identify potential risk factors related to customer turnover. The goal was to build a dashboard for the retention manager that reflects the key performance indicators (KPIs) related to client retention.

Learning:
How to define key performance indicators (KPIs) related to customer retention.
How to create a dashboard that visualizes customer demographics and insights.

Project Work:
Develop a dashboard using the defined KPIs to reflect customer demographics and insights.
Write a concise email to the engagement partner explaining your findings and providing suggestions for necessary changes based on the dashboard you've created.

Key Points from Customer Retention Analysis:
83% of the customers are senior citizens.
The percentage of male and female customers is equal (50% each).
1,869 customers have churned from a total of 7,043 customers.
The total revenue loss due to churn is $2.86 million.
Most customers without online backup services are among those who have churned.
Among internet services, fiber optics provides the highest revenue.

Additional Insights on Churn Customers:
A total of 1,869 customers have churned, representing 26.5% of the customer base.
380 customers churned in the last month alone (immediate churn).
The revenue loss due to churn is approximately $2.9 million.
Gender is not a decisive factor in customer churn, as the churn rate is equal among male and female customers.

DAX Used -

1. Percentage of Senior Citizens Who Have Churned
To calculate the percentage of senior citizens who have churned, the formula is:

DAX
Copy code
% of Senior Citizen = 
DIVIDE(
    CALCULATE(
        COUNT(Churn[SeniorCitizen]), 
        Churn[SeniorCitizen] = 1, 
        Churn[Churn] = "Yes"
    ),
    CALCULATE(
        COUNT(Churn[SeniorCitizen]), 
        Churn[Churn] = "Yes"
    ),
    0
)
2. Percentage of Customers with Partners Who Have Churned
To find out the percentage of customers with partners who have churned, the formula is:

DAX
Copy code
% of Partner = 
DIVIDE(
    CALCULATE(
        COUNT(Churn[Partner]), 
        Churn[Partner] = "Yes", 
        Churn[Churn] = "Yes"
    ),
    CALCULATE(
        COUNT(Churn[Partner]), 
        Churn[Churn] = "Yes"
    ),
    0
)
3. Percentage of Customers with Dependents Who Have Churned
To determine the percentage of customers with dependents who have churned, use the following formula:

DAX
Copy code
% of Dependents = 
DIVIDE(
    CALCULATE(
        COUNT(Churn[Dependents]), 
        Churn[Dependents] = "Yes", 
        Churn[Churn] = "Yes"
    ),
    CALCULATE(
        COUNT(Churn[Dependents]), 
        Churn[Churn] = "Yes"
    ),
    0
)
4. Percentage of Customers with Online Backup Who Have Churned
To calculate the percentage of customers with online backup services who have churned:

DAX
Copy code
% of Online Backup = 
DIVIDE(
    CALCULATE(
        COUNT(Churn[OnlineBackup]), 
        Churn[OnlineBackup] = "Yes", 
        Churn[Churn] = "Yes"
    ),
    CALCULATE(
        COUNT(Churn[OnlineBackup]), 
        Churn[Churn] = "Yes"
    ),
    0
)
5. Churn Rate Percentage
To calculate the overall churn rate percentage among all customers, the formula is:

DAX
Copy code
Churn rate % = 
DIVIDE(
    CALCULATE(
        COUNT(Churn[Churn]), 
        Churn[Churn] = "Yes"
    ),
    CALCULATE(
        COUNT(Churn[Churn]), 
        ALLSELECTED(Churn)
    ),
    0
)
