+++ 
title = "Task 1: Working with Glue transformation" 
chapter = false 
weight = 1 
+++

1. Login to the AWS Console using the login URL and credentials provided. Once you are logged in, check in the upper right-hand corner that you are using **Oregon** region. If not, use the drop-down list to change to the **Oregon** region.

1. From the console, navigate to the **AWS Glue** service. Service *search box* > Glue

1. Under the ETL menu, select **Jobs** and then click the button for **Add Job**

1. For the **Name** of the Job, use type `teamawesome-convert-to-parquet`

1. Under IAM role, using the drop-down list, select **GlueServiceRole** IAM role

	Leave the rest of the parameters as *Default*

1. Click **Next**

1. For your data source, select the database you created for the Merchandise Sales data, look for a data source named similar to`merchandise_sales_xxxxxxx` and then click the **Next** button

1. In the **Choose a transformation type** page, select **Change schema**, click the **Next** button

1. In the **Choose a data target** page, select **Create tables in your data target**

	1. For the Data store, select **Amazon S3**

	1. For the Format, select **Parquet**

	1. For the Target path, click on the small folder icon and select the S3 bucket `teamawesome-merch-sales-parquet-xxxxxxx`, click **Select**, then click **Next**

1. In the **Map the source columns to target columns** page, leave *defaults* and click **Save job and edit script**

1. Close **Script editor tips** window

1. From the toolbar, click the **Save** button, and then click the **X** icon (far right) to return to the list of jobs

1. Locate the job you created and click to select the job

	<img src="../images/click-on-job.png" alt="drawing" width="600"/>

1. Click the **Action** button and select **Run Job**, this will start your Glue ETL job

1. Click again on the checkbox next to your ETL job to see the status panel. 

1. You will notice the job status as *Running*, wait a couple of minutes until it changes to *Succeeded*

1. Navigate to the S3 console (Services *search box* > S3) and search for the bucket `teamawesome-merch-sales-parquet-xxxxxxxx`. Verify that the parquet files were successfully created in the bucket

With the Parquet files created, you could then crawl those files and start using the data with Athena. Because Parquet is a columnar, compressed format, there will be less data scanned, reducing the cost of your Athena queries.

**LAB END**