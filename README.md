Goals
Create an insightful and easy to use report so the Managers could track their teams’ performance to the individual, level without too much effort. 
Business Needs
After the implementation of the new CRM system for the whole year of 2017 (the first complete year we have data for), the need to summarize and present the findings on a higher level was imminent. 
The findings of this report will help Managers and VP’s to draw conclusions on current sales performance, spot weaknesses, set new goals, and make the necessary adjustments and corrections.
Report Analysis

In this report five main KPI’s are used to track Sales performance:
1.	Deals Won
Shows the number of opportunities that were won for the Manager/ Agent.  
DAX Formula used:

Total Won = 
CALCULATE (
    COUNT ( sales_pipeline[deal_stage] ),
    sales_pipeline[engage_date] <> BLANK ()
        && sales_pipeline[deal_stage] = "Won"
        && sales_pipeline[close_date] <> BLANK ()
)

2.	Won Deals Ratio
Displays the percentage of the won Opportunities compared to the total number of Opportunities the Manager/ Agent was engaged.
DAX Formula used:
Won Deals Ratio = 
DIVIDE ( [Total Won], [Total Closed] )

3.	Average Days Engage-Close:

Depicts the average number of the days it took to the Manager/ Agent to win the opportunity.

DAX Formula used:
Avg days engage-close = 
AVERAGE ( sales_pipeline[engage_vs_close_date] )

The DAX Formula Calculated Column was:

engage_vs_close_date = 
SWITCH (
    TRUE,
    sales_pipeline[engage_date] <> BLANK ()
        && sales_pipeline[close_date] <> BLANK (), DATEDIFF ( sales_pipeline[engage_date], sales_pipeline[close_date], DAY )
)


4.	Average Revenue

The Average Revenue of the Manager/ Agent for the selected Quarter

DAX Formula used:

Avg Revenue = 
AVERAGE (  'sales_pipeline'[close_value]  )


5.	Average Dif Close Price-SRP

This KPI shows the Average Difference between the closure Price and the Suggested Retail Price. Managers are able to investigate sales that went way under the SRP, thus producing less revenue for the company.

DAX Formula used:

Avg Dif Close Price-SRP = 
AVERAGE ( sales_pipeline[close_vs_SRP_difference] )

The DAX Formula Calculated Column was:

close_vs_SRP_difference = 
SWITCH (
    TRUE,
    sales_pipeline[close_value] <> BLANK ()
        || sales_pipeline[close_value] <> 0, sales_pipeline[close_value] - RELATED ( dim_products[sales_price] )
)



Apart from the main KPI’s values, users are able to see each KPI’s previous quarter value, as well as the percentage of Quarter over Quarter Growth (&QoQ Growth), so they can track the trending.


Each Manager can also see information on the top Customer regarding sales revenue for his team for each Quarter, namely:

1.	Name of Top Customer
2.	Revenue from the Customer
3.	Total Deals made
4.	Size of Customer’s company (Revenue)
5.	Size of Customer’s company (Nr of Employees)
6.	Name of Mother Company (if there is one)



On the bottom of the report, the user can check the individual performance of his/her team via 3 clustered bar charts:

1.	The first shows the values for the currently selected KPI above (a green tick sign indicates that) for the selected Manager in the selected Quarter. The greenish bar indicates the best performance for the selected KPI and the reddish the worst.
2.	The second bar chart allows the Manager to track High-Tier Sales performance among the team
3.	Hier three (at max) smaller bars for each Agent, show the breakdown of the sales accomplished, based on whether they sold at a higher/the same/a lower price compared to the SRP.

Finally, on the right a Legend explains how the 3 Price Tiers are currently levelled.



Finding Insights in the Report

Manager Summer Sewald would be able to see, that for Q3 of 2017, Agent Kary Hendrixson converted the higher number of opportunities into actual deals (54) (see screenshot below)

 

At the same time, Kary was the slowest on closing the deals, as it took her on average 51.3 days:

 

At least Kary closed most of the deals very close to the SRP (only -$10.56 on average), so the revenue for the company was very close to the minimum expected amount:

 
