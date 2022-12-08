# Sql-challenges
Solution of most challenging question 

**********************************************************************************************************************************************************************
Assume that you are given the table below containing information on viewership by device type (where the three types are laptop, tablet, and phone). Define “mobile” as the sum of tablet and phone viewership numbers. Write a query to compare the viewership on laptops versus mobile devices.

Output the total viewership for laptop and mobile devices in the format of "laptop_views" and "mobile_views".
**********************************************************************************************************************************************************************
viewership TABLE:-
user_id	   device_type	  view_time
123	       tablet	       01/02/2022 00:00:00
125	       laptop	       01/07/2022 00:00:00
128	       laptop	       02/09/2022 00:00:00
129	       phone	       02/09/2022 00:00:00
145	       tablet	       02/24/2022 00:00:00
**********************************************************************************************************************************************************************
select 
count (case when device_type in ('phone' , 'tablet') then 1 else null end ) 
mobile_views
, count(case when  device_type ='laptop' then 1 else null end ) laptop_views
from viewership 
**********************************************************************************************************************************************************************
Result:-
mobile_views	laptop_views
3	             2
**********************************************************************************************************************************************************************
q2
**********************************************************************************************************************************************************************
CVS Health is trying to better understand its pharmacy sales, and how well different products are selling. Each drug can only be produced by one manufacturer.

Write a query to find the total sales of drugs for each manufacturer. Round your answer to the closest million, and report your results in descending order of total sales.

Because this data is being directly fed into a dashboard which is being seen by business stakeholders, format your result like this: "$36 million".
**********************************************************************************************************************************************************************
product_id	units_sold	  total_sales	    cogs	        manufacturer	   drug
94	        132362	      2041758.41	    1373721.70	  Biogen	         UP and UP
9	          37410	        293452.54	      208876.01	    Eli Lilly	       Zyprexa
50	        90484	        2521023.73	    2742445.9	    Eli Lilly	       Dermasorb
61	        77023	        500101.61	      419174.97	    Biogen	         Varicose Relief
136	        144814	      1084258.00	    1006447.73	  Biogen	         Burkhart
**********************************************************************************************************************************************************************
Example Output:
manufacturer    	sale
Biogen	        $4 million
Eli Lilly	      $3 million
**********************************************************************************************************************************************************************
SELECT 
manufacturer, 
concat ('$',round(SUM(total_sales)/1000000 ), ' million') as sale 
from pharmacy_sales
group by manufacturer
order by sum(total_sales) DESC;
