# Customer-Churn-Analysis
This project uses a fictional churn dataset from a Telecom provider called Databel, to analyze customer churn using business intelligence tools like Tableau and PowerBI. The dataset consists of 29 different columns and has one row per customer.

The Churn Rate, or the rate of attrition or customer churn, is the rate at which customers stop doing business with an entity. Since it is considered easier to keep customers than to get new ones, reducing churn is a priority for many companies. The simplified churn formula is dividing customers lost by the total number of customers. There are multiple ways to calculate churn. It varies by industry and revenue model. For example, an e-commerce platform could define a churner as customers who have not purchased in the last 12 months.


DATA CHECK

The first step in the analysis is doing a data check. In this step, we created two measures to check if the count of customer ids equals the count of unique customer ids. This check is essential because we might double-count costs later if there are duplicate rows. In this case, we made use of calculated fields to create:
1. Number of Customers as COUNT of the ‘Customer ID’
2. Number of Unique Customers as COUNTD of the ‘Customer ID’

Comparing those two measures, the count of unique customers matches the count of customers (6687)

CALCULATING CHURN

The next step is creating another measure that calculates churn. A column in the dataset called 'Churn Label' indicates "Yes" or "No" to indicate whether or not a customer churn. We converted this column to a binomial column containing a 1 or 0 and used that to calculate the churn rate. We used an IF statement to convert the Churn Label column into a new column called 'Churned':

IF Churn Label == “Yes” THEN 1 ELSE 0 END.

Afterward, we created a calculated field called 'Number of Churned Customers' by summing the 1s contained in the 'Churned' column. Then we can calculate the churn rate by dividing the 'Number of Churned Customers' by 'Number of Customers.'

INVESTIGATING CHURN REASONS

The next step is to investigate the different reasons why customers churn. In this case, we created a column chart listing why customers churn in descending order. The chart shows that the top 3 churn reasons include Competitors made a better offer, Competitors had a better device and the Attitude of service provider. 


DIGGING DEPPER IN CHURN CATEGORIES

Churn Reasons are actually grouped together in the 'Churn Category' column. The 'Extra data charges', 'Price too high', and other price-related reasons, for example, are grouped together in the 'Price category'. After visualization, it is displayed that the most prevalent churn reason is competitor related reasons by 44.82%.

USING MAPS FOR FURTHER EXPLORATION

About the customers, it is known that Competitors launched aggressive promos in certain states. Databel is wondering if it had an impact on them. We, therefore, created a map in Tableau (and PowerBI) to investigate the churn rate by state. The result shows that the state of California (CA) has the highest churn rate (63.24%, 43 out of 68).

ANALYZING DEMOGRAPHICS

Investigating the Senior metrics, we discovered that the churn rate for senior citizens is around 10% higher than the average(38.22%). This suggests it might be a good idea to analyze age in general. Therefore, we created different age bins and combo charts visualizing the numbers of customers per bracket and their respective churn rates. The result shows that the age groups of 70 and above have the highest churn rates, but they also contain the least amount of people. 

INSPECTING GROUPS

Databel offers group contracts to customers from the same household. The advantage for the customer is a discounted rate, which is an excellent way for Databel to grow its customer base. We analyzed if customers that are part of a group indeed have a lower phone bill and if it impacts the churn rate. From the graph, the ‘Monthly Charge’ is significantly lower for people in a group of 2 or more. Particularly, the contract consisting of 6 customers has the lowest churn rate. 

PARAMETERS

We created a dynamic parameter to allow stakeholders to interact with the sheet and investigate metrics such as the number of customers per group, the number of churned customers per group, etc. One of the new parameters would be ‘Pick Metric’ consisting of several metrics such as “Avg Monthly Charge”, “Number of Customers”, “Number of churned Customers”, and “Avg Customer Service Calls”. After exploring, it is shown that the churn rate for people in groups is significantly lower(<10%), but most people (5166 or over 75%) are not part of a group.  

CHURN RATE BY PLAN

Databel hypothesizes that people not on an unlimited data plan are more likely to churn. To investigate the matter, we created a text table displaying the churn rate for customers with unlimited plans and those without them. The table shows that customers on an unlimited plan are more likely to churn.  

Since it would be good to know how much mobile data in a gigabyte (GB) they are using monthly. We created a new calculated field to classify customers based on the data they use called the ‘Grouped Monthly GB Download’ from the ‘Avg Monthly GB Download’ Column. The analysis shows that customers on an unlimited data plan who do not consume more than 5 GB per month tend to churn more. 

CHURN RATE BY INTERNATIONAL CALLS

Databel is also curious about the behavior of customers who call internationally and/or if paying for an international plan influences their loyalty. The analysis results in a high churn rate for customers who have an international plan but do not call internationally. Although the rate is ridiculously high, there are luckily only a few customers in this group. As for the monthly charge, this group has the highest average monthly charge of all four groups. 

CHURN RATE BY CONTRACT TYPE

Adding Contract Type into account, customers on a Month-to-Month contract are way more likely to churn. In this case, they mostly pay with Direct Debit (1141 out of 1796). 


OVERVIEW DASHBOARD

After doing all the necessary analysis, we built four dashboards. The first dashboard should be an overview of the analysis and contain key performance indicators (KPIs) such as the number of customers and the churn rate. We also added churn reason to the graph because it explains why customers left Databel. 

AGE BRACKETS & GROUP DASHBOARD

The second dashboard portrays insights about the age buckets and groups. We use dynamic parameters created in combination with filters to make the dashboard interactive. The graph shows that the churn rate for customers outside a group who have an account length of 12 months or less is 53%. Moving these customers to a one or two-year contract to reduce churn sounds like a great way to reduce churn.

PAYMENT METHOD & CONTRACT DASHBOARD

The third dashboard investigated customer service calls. In this case, we use a scatterplot about the contract and payment type and combine it with two KPI cards about customer service calls. From the dashboard, the average number of customer service calls for customers on a month-to-month contract and by direct debit is pretty high (1.47 calls per customer). Databel should investigate what is going on here. It is possible that there is a problem with the payment method that needs to be looked into. 

INTERNATIONAL AND DATA PLAN DASHBOARD

The final dashboard covers insights about the Data and International plan. The graph shows that customers without an unlimited data plan and consuming less than 5 gigabytes pay 4.34 extra data charges. These customers pay extra for the data charges because they are not on an unlimited data plan. 

STORY

The last step would be to combine the four dashboards in a story. 
