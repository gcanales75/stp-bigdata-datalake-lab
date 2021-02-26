+++ 
title = "Task 1: Create a Glue Data Crawler" 
chapter = false 
weight = 1 
+++

The IT team at UnicornNation has exported Merchandise Sales data from their finance system and transferred this data to a folder in a single S3 bucket. There are multiple .CSV files in the bucket, each representing a month’s worth of data.
In this lab, we are going to create a Glue Data Crawler to crawl across this bucket. Once we have created the crawler, we are going to run it to determine the tables that are located in the bucket and add their definitions to the Glue Data Catalog.

To create your Glue data crawler, follow these steps: 

1. Login to the AWS Console using the login URL and credentials provided. Once you are logged in, check in the upper right-hand corner that you are using **Oregon** region. If not, use the drop-down list to change to the **Oregon** region.

	<img src="../images/region-1.png" alt="drawing" width="500"/>
	
1. Before start working with AWS Glue, we need to configure a default result bucket, please navigate to the S3 service. Services *search box* > S3

	<img src="../images/service-s3.png" alt="drawing" width="700"/>

1. Locate the S3 bucket with this name pattern `query-results-bucket-xxxxxxxxx`

1. Copy and paste the full bucket name in a notepad, you will need it in the following step

1. Now navigate to the Athena service. Services *search box* > Athena

1. Click on **Get Started**

	<img src="../images/athena-get-started.png" alt="drawing" width="600"/>

1. Click on the link to set up a query result location

	<img src="../images/query-result-location.png" alt="drawing" width="600"/>

1. Enter the S3 bucket name you recorded in step 4. Follow this pattern: `s3://[my-query-result-bucket]/` (include the slash '/' at the end).

	<img src="../images/set-result-location.png" alt="drawing" width="600"/>

1. Click **Save**

1. From the console, navigate to the AWS Glue service. Services *search box* > AWS Glue

1. From the AWS Glue Data Catalog, navigate to **Databases** and click **Add Database**

	<img src="../images/skitch.28.png" alt="drawing" width="500"/>

1. Enter a database name, type `teamawesome-merch-sales` and click **Create**

	<img src="../images/skitch.27.png" alt="drawing" width="500"/>

1. Now that your database has been created, click on the **Tables** menu in the left-hand menu

1. Select the drop down to **Add Tables** > **Add tables using a crawler**

	<img src="../images/skitch.26.png" alt="drawing" width="600"/>

1. Enter a name for your crawler, type `teamawesome-merch-sales-crawler` and click **Next**

1.  For Crawler source type select **Data stores**, then click **Next**

1. For your data store, select **S3** and below **Include path**, click on the little folder icon

	<img src="../images/skitch.25.png" alt="drawing" width="600"/>

1. This will open a new window, look for the Merchandise Sales bucket, it's name will follow this pattern: `merchandise-sales-xxxxxxx`, click **Select** and then click **Next**.

1. For **Add another data store**, take the default of *No* and click **Next**

1. Next, when setting up an IAM role, click on **Choose an existing IAM Role**, then under IAM role select role name **GlueServiceRole**. Then click **Next**.

	<img src="../images/glue-iam-role.png" alt="drawing" width="600"/>

1. For the Frequency, leave the default of **Run on demand** and click **Next**

1. In **Configure the crawler's output**, select the Database **teamawesome-merch-sales** and click **Next**

1. Finally, review the settings for your crawler and click **Finish**. This should take you to a list of crawlers that have been created

1. Select the crawler you just created and click on **Run crawler**

	<img src="../images/skitch.22.png" alt="drawing" width="600"/>

	Watch the Crawler console for your job to finish successfully (it should take ~2 minutes). *Status* must change from **Starting** to **Ready**

1. Using the navigation menu on the left, navigate to **Tables**

1. You should see a new table has been created, copy and paste the table name on a notepad. 

1. Now click to select the table, then select **Action** > **View Data**. A dialogue window will be open, select **Preview data**

	<img src="../images/merch-sales-new-table.png" alt="drawing" width="600"/>
	
1. This will open the Athena console, click Get started

	<img src="../images/athena-get-started.png" alt="drawing" width="600"/>

1. You will see the Athena console, you will run the below query, but first you need to update it with the table name you recorded in step 26- Click **Run query**

	```
	SELECT * FROM "teamawesome-merch-sales"."[GLUE_TABLE_NAME]" limit 10;
	```

	<img src="../images/athena-run-query.png" alt="drawing" width="600"/>

1. You must see a similar query output

	<img src="../images/athena-output.png" alt="drawing" width="800"/>