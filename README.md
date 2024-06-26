<h1>CREDIT CARD WEEKLY STATUS REPORT</h1>


<h2> Project Objective </h2>

To develop a comprehensive credit card weekly dashboard that provides real time insights into performances metrics and trends, enabling stakeholders to monitor.


<h2>DAX(Data Analysis Expressions ) Queries</h2>

AgeGroup = 
          
           SWITCH(TRUE(),

                         'customer'(customer_age] < 30, "20-30",

                         'customer' [customer_age] >= 30 && 'customer' [customer_age] <40, "30-40",

                         'customer' [customer_age] >= 40 && 'customer' [customer_age] < 50, "40-50",

                         'customer' (customer_age] >= 50 && 'customer' [customer_age] <60, "50-60",

                         'customer' (customer_age] >= 60 && 'customer' [customer_age] <70, "50-70", 
                         
                         'customer' [customer_age] >= 70 && 'customer' [customer_age] <80, "70-80",

                         'customer' (customer_age] >= 80 && 'customer' [customer_age] <90, "80-90",

                         'customer' (customer_age] >= 90 ,"90+",

                         'unknown'
                          )

IncomeGroup = 

           SWITCH(TRUE(),

                         'customer' [income) < 35000, "Low",

                         'customer' [income) >= 35000 && 'customer' [income] <70000, "Med",

                         'customer' [income) >= 70000, "High",

                         'unknown'
                          )


week_num2 = 
            
           WEEKNUM('credit_card (1)' [week_start_date])

Revenue = 

          'credit_card (1)' [annual_fees] + 'credit_card (1)' [total_trans_amt] + 'credit_card (1)' [interest_earned]

Current_week_Reveneue =

          CALCULATE(SUM('credit_card (1)' [Revenue]), 
                     
                    (ALL('credit_card (1)'),'credit_card (1)'[week_num2] = MAX('credit_card (1)' [week_num2])))

Previous_week_Reveneue = 

          CALCULATE(

                  SUM('credit_card (1)' [Revenue]),

                  FILTER(ALL('credit_card (1)'),'credit_card (1)' [week_num2] = MAX('credit_card (1)' [week_num2])-1))

<h2>Project Insights </h2>

Revenue increased by 28.8% in Week 53(31st Dec)

Overall revenue is 57M

Total interest is 8M

Total transaction amount is 46M

Male customers are contributing more in revenue 31M, female 26M

Blue & Silver credit card are contributing to 93% of overall transactions

TX, NY & CA is contributing to 68%

Overall Activation rate is 57.5%

Overall Delinquent rate is 6.06%
