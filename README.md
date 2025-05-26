# Credit_Card_Financial_Dashboard

*** DAX Queries***
1. Week_Num1 = WEEKNUM(cc_details[Week_Start_Date].[Date])
2. wow_revenue = ((cc_details[Current_Week_Revenue]-cc_details[Previous_week_Revenue])/cc_details[Previous_week_Revenue])
3. wow_trans_count_change = DIVIDE([Current_wow_trans_count]-[Previous_wow_trans_count],[Previous_wow_trans_count])
4. wow_transaction_amount = DIVIDE([current_week_transaction_amount]-[previous_week_transaction_amount],[previous_week_transaction_amount])
5. Total_Revenue = cc_details[Annual_Fees]+cc_details[Interest_Earned]+cc_details[Total_Trans_Amt]
6. Previous_wow_trans_count = CALCULATE(sum(cc_details[Total_Trans_Vol]),
                              FILTER(ALL(cc_details),
                              cc_details[Week_Num1]=MAX(cc_details[Week_Num1])-1))
7. previous_week_transaction_amount = CALCULATE(SUM(cc_details[Total_Trans_Amt]),
                                      FILTER(ALL(cc_details),
                                      cc_details[Week_Num1]=MAX(cc_details[Week_Num1])-1))
8. Previous_week_Revenue = CALCULATE( SUM(cc_details[Total_Revenue]),
                             FILTER(all(cc_details),
                             cc_details[Week_Num1]= MAX(cc_details[Week_Num1])-1))
9. current_week_transaction_amount = CALCULATE(SUM(cc_details[Total_Trans_Amt]),
                                  FILTER(ALL(cc_details),
                                  cc_details[Week_Num1]= MAX(cc_details[Week_Num1])))
10. Current_Week_Revenue = CALCULATE(SUM(cc_details[Total_Revenue]),
                            cc_details[Week_Num1])
11. AGE_GROUP = SWITCH(TRUE(),
                customer_details[Customer_Age]>=20 && customer_details[Customer_Age]<30,"20-30",
                customer_details[Customer_Age]>=30 && customer_details[Customer_Age]<40,"30-40",
                customer_details[Customer_Age]>=40 && customer_details[Customer_Age]<50,"40-50",
                customer_details[Customer_Age]>=50 && customer_details[Customer_Age]<60,"50-60",
                customer_details[Customer_Age]>=60,"60+",
                "unknown"
                )
12. IncomeGroup = SWITCH(TRUE(),
                     customer_details[Income] < 35000, "Low",
                     customer_details[Income] >= 35000 && customer_details[Income] <70000, "Med",
                     customer_details[Income] >= 70000, "High",
                     "unknown"
                     )

13. Summarize_Table = SUMMARIZE(cc_details,cc_details[Client_Num],"ClientCount", COUNTROWS(cc_details))


*** Project Insights- Week 53 (31st Dec)***
WoW(week on week) change:
• Revenue increased by 28.8%,
• Total Transaction Amt & Count increased by 35.04% & 3.39%
• Customer count increased by xx%
Overview YTD:
• Overall revenue is 57M
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M
• Blue & Silver credit card are contributing to 93% of overall
transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%
