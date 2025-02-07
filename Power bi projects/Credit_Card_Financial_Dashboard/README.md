# Credit_Card_Financial_Dashboard-

## Project Objective

To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

## DAX QUERIES USED :-

AgeGroup = SWITCH( <br/>
 TRUE(), <br/>
 'public cust_detail'[customer_age] < 30, "20-30",<br/>
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",<br/>
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",<br/>
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",<br/>
 'public cust_detail'[customer_age] >= 60, "60+",<br/>
 "unknown"<br/>
 )<br/>
IncomeGroup = SWITCH(<br/>
 TRUE(),<br/>
 'public cust_detail'[income] < 35000, "Low",<br/>
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",<br/>
 'public cust_detail'[income] >= 70000, "High",<br/>
 "unknown"<br/>
)<br/>
week_num2 = WEEKNUM('public cc_detail'[week_start_date])<br/>
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]<br/>
Current_week_Reveneue = CALCULATE(<br/>
 SUM('public cc_detail'[Revenue]),<br/>
 FILTER(<br/>
 ALL('public cc_detail'),<br/>
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))<br/>
Previous_week_Reveneue = CALCULATE(<br/>
 SUM('public cc_detail'[Revenue]),<br/>
 FILTER(<br/>
 ALL('public cc_detail'),<br/>
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))<br/>

## Project Insights- Week 53 (31st Dec)
### WoW change:
  • Revenue increased by 28.8%,<br/>
  • Total Transaction Amt & Count increased by 3.2% & 16.3%<br/>
  • Customer count increased by 23.1%<br/>
### Overview YTD:<br/>
  • Overall revenue is 57M<br/>
  • Total interest is 8M<br/>
  • Total transaction amount is 46M<br/>
  • Male customers are contributing more in revenue 31M, female 26M<br/>
  • Blue & Silver credit card are contributing to 93% of overall<br/>
### transactions<br/>
  • TX, NY & CA is contributing to 68%<br/>
  • Overall Activation rate is 57.5%<br/>
  • Overall Delinquent rate is 6.06%<br/>
