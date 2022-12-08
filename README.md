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
