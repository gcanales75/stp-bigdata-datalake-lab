+++ 
title = "Task 1: Querying data with Amazon Athena" 
chapter = false 
weight = 1 
+++

1. Login to the AWS Console using the login URL and credentials provided. Once you are logged in, check in the upper right-hand corner that you are using **Oregon** region. If not, use the drop-down list to change to the **Oregon** region.

1. From the console, navigate to the Athena service. Services *search box* > Athena

1. Using the **Database** drop-down list, change the database to point to your Tickit database **teamawesome-tickit-history**

	<img src="../images/skitch.5.png" alt="drawing" width="450"/>

1. Open a new query text box

	<img src="../images/open-new-query-window.png" alt="drawing" width="600"/>

1. To run a query, paste your below sql script into the new text box and click the **Run Query** button

1. Use the query text below, run each query to answer these questions:

	Question 1: Using the following query, what were the Top 5 ticket sellers for events in San Diego in 2008?
	
	```
	select sellerid, username, city, firstname ||' '|| lastname as fullname, sum(qtysold) as qtysold
	from sales, date, users
	where sales.sellerid = users.userid
	and sales.dateid = date.dateid
	and year = 2008
	and city = 'San Diego'
	group by sellerid, username, city, firstname ||' '|| lastname
	order by 5 desc
	limit 5;
	```
	
	Question 2: Using the following query, who were the buyers AND sellers for ticket transactions that cost $10,000 or more?
	
	```
	select listid, lastname, firstname, username,
	pricepaid as price, 'S' as buyorsell
	from sales, users
	where sales.sellerid=users.userid
	and pricepaid >=10000
	union
	select listid, lastname, firstname, username, pricepaid,
	'B' as buyorsell
	from sales, users
	where sales.buyerid=users.userid
	and pricepaid >=10000
	order by 1, 2, 3, 4, 5;
	```