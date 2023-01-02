# Tableau

This repository consists of all of my learning experiences and practices related to Tableau.

# My Tableau Public Repository  : - 
https://public.tableau.com/app/profile/ritesh.sil#!/?newProfile=&activeTab=0


# Use Case 3 : Dynamic change of sales based on the filter selection : 
https://public.tableau.com/app/profile/ritesh.sil/viz/Test-Report_16445217571370/ExecutiveSummary


# Use Case 2 : Comaprative Analysis for Sales vs Target : Bullet chart : 
   Bullet charts are often used for a compartive analysis between Actual Measure vs Target Measure or a Forecast measure by different dimensions.
   In the given link below a simple bullet chart has been showcased to compare actual sales vs the target, where the wider bands represent the 60%
   80% of the target sales.
   
   
# Use Case 1 : Distribution of Sales accross regions : Histogram /Bins :
   To check the distribution across the region will help us to understand the market size for each region. It will help us to do a comparative study of different markets across the region along with the profit%, so that business understands in which region we should focus to promote the products and spend for more branding and advertising to increase the revenue. 
   1. Identify the Top customers, who are actually driving the sales KPI. We need to monitor them highly.
   2. Identfy the root cause , why so many customers are having that very low sales. Find the characteristics of those customers. Which city they belong to
   3. Find the strategy promote the sales for them.

URL :  https://public.tableau.com/app/profile/ritesh.sil/viz/SalesvsProfit-Distribution/WestRegion?publish=yes
 
         Key learning : 
            1. How to plot histogram in Tableau.
            2. How to create bins in Tableau


**Rolling 12 month logic**

- *Step1* - Create the **Concatenate** Field as below : 

`DATEPARSE("MM.YYYY",STR([Month-Quarter])+"."+str([Year]))`


- *Step2* - Create the **Rolling 12 month** Field as below : 

`IF DATETRUNC('month',DATEADD("month",12,[Period]))>=[Concatenate] 
and DATETRUNC("month", [Period])<=[Concatenate]
then [Period]
END`

This calculation will help to change the rolling 12 month range dynamically.


**Dynamic QTD based on month selection**

- *Step1* - Create the **Month to Qtr** Field as below :

`IF [Month-Quarter] in (1,2,3) THEN 1
ELSEIF [Month-Quarter] in (4,5,6) THEN 2
ELSEIF [Month-Quarter] in (7,8,9) THEN 3
ELSEIF [Month-Quarter] in (10,11,12) THEN 4
END`

- *Step2* - Create the **Sales to Date QTD** Field as below :

`IF int([qtr])=[Month to Qtr] AND  [year] = [Year] AND int([Month])<=[Month-Quarter] THEN [<Measure field>] END`



=========================Tableau interview questions ==========================================
1. Could you please tell me what are key differences b/w continuous and discrete fields

2. Dual Axis chart : - 
	How do you create a donut chart in Tableau.
	
3. Grouping  - 
   Lets Say, you are dealing with restaurant foods data.
   Several exhaustive list of food items and corresponding price list.
   Now you want to categorize the sales as per cuisines, 
   
   You want to categorize the sales as per cuisine.  
   

   
4. When do we use bullet chart in Tableau?

5. I want to create a calculation which will give me the number of months between
 starting of the year and today

6. Lets say you have a time series data for last 3 years of sales.
	- How will you calculate Year to Date sales.
	- Rolling 6 months of sales.
	- Create a drop down to select a chart based on rolling 3 months,
		rolling 6 months, rolling 12 months 
	- What do you mean by year over year growth


7. Suppose you have 3 markets , 
in each of the market you have multiple products and 
then you have sales corresponding to each product.
Now a market share is given 
=  sales for a particular product / the entire sales of the corresponding market	
		
8. Suppose you have a KPI placed inside a dashboard. 
You want add simple navigation as "Show Customer level details".
When you click on it it expands and when you hide 


9. Suppose you have created 3 dashboards in a report, 
you need to add filter drop downs which will apply all rest of the dashboards

10. 
