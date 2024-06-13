# Credit_Card_Financial_Dashboard
Credit Card Transaction  and Credit Card Customer Dashboard Using Power Bi

Objective: To develop a comprehensive credit card weekly dashboard that provides real-time insights in key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations efficiently and effectively.

Import Data to SQL Database
Steps:
1) Prepare csv file
2) Create tables in SQL
3) Import csv file into SQL

Dax Queries Used:

AgeGroup = 

          SWITCH(
          TRUE(),
          'public cust_detail'[Customer_Age] < 30,"20-30",
          'public cust_detail'[Customer_Age] >= 30 && 'public cust_detail'[Customer_Age] < 40,"30-40",
          'public cust_detail'[Customer_Age] >= 40 && 'public cust_detail'[Customer_Age] < 50,"40-50",
          'public cust_detail'[Customer_Age] >= 50 && 'public cust_detail'[Customer_Age] < 60,"50-60",
          'public cust_detail'[Customer_Age] >= 60,"60+",
          "unknown"
        )

Income Group = 

      SWITCH(
      TRUE(),
     'public cust_detail'[Income] < 35000,"Low",
     'public cust_detail'[Income] >= 35000 && 'public cust_detail'[Income] <70000,"Med",
     'public cust_detail'[Income] >= 70000 && 'public cust_detail'[Income] <70000,"Med",
     'public cust_detail'[Income] > 70000,"High",
     "unknown"
     )


week_num2 = 

         WEEKNUM('public cc_detail'[Week_Start_Date])

Revenue =

       'public cc_detail'[Annual_Fees] + 'public cc_detail'[Total_Trans_Amt] + 'public cc_detail'[Interest_Earned]


Current_Week_Revenue =

     CALCULATE(
     SUM('public cc_detail'[Revenue]),
     FILTER(
     ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))



Previous_Week_Revenue =

     CALCULATE(
     SUM('public cc_detail'[Revenue]),
     FILTER(
     ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))


Project Insights:
Overview YTD:
- Overall revenue is 55M
- Total Interest is 7.8M
- Total Transaction amount is 45M
- Blue & Silver credit card are contributing to 93% of overall transactions.
- TX, NY & CA is Contributing to 68%
- Male Customers are contributing more in revenue 30M, female 25M
- Overall Activation Rate is 57.47%
- Overall Delinquent rate is 6.07% 







