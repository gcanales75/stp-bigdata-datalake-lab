+++ 
title = "Task 1: Create your Glue crawler" 
chapter = false 
weight = 1 
+++

1. Login to the AWS Console using the login URL and credentials provided. Once you are logged in, check in the upper right-hand corner that you are using **Oregon** region. If not, use the drop-down list to change to the **Oregon** region.

	<img src="../images/region-1.png" alt="drawing" width="500"/>

1. From the console, navigate to the AWS Glue service. Services *search box* > AWS Glue

1. From the AWS Glue Data Catalog, navigate to **Databases** and click **Add Database**

	<img src="../images/skitch.28.png" alt="drawing" width="500"/>

1. Enter a database name, type `teamawesome-tickit-history` and click **Create**

	<img src="../images/skitch.27.png" alt="drawing" width="500"/>

1. Now that your database has been created, click **Tables** in the left-hand menu

1. Select the drop down to **Add Tables** > **Add tables using a crawler**

	<img src="../images/skitch.26.png" alt="drawing" width="600"/>

1. Enter a name for your crawler, type `teamawesome-tickit-crawler` and click **Next**

1.  For Crawler source type select **Data stores**. Click **Next**

1. For your data store, select **S3** and below **Include path** click on the little folder icon

	<img src="../images/skitch.25.png" alt="drawing" width="600"/>

1. This will open a new window, look for the Tickit History bucket, it's name will follow this pattern: `tickit-history-xxxxxxx`, click **Select** and then click **Next**.

1. For **Add another data store**, take the default of *No* and click **Next**

1. Next, when setting up an IAM role, click on **Choose an existing IAM Role**, then under IAM role select role name **GlueServiceRoleTickitHistory**. Then click **Next**.

	<img src="../images/glue-iam-role.png" alt="drawing" width="600"/>

1. For the Frequency, select the default of **Run on Demand** and click **Next**

1. In **Configure the crawler's output**, select the Database **teamawesome-tickit-history** and click **Next**

1. Finally, review the settings for your crawler and click **Finish**. This should take you to a list of crawlers that have been created

1. Select the crawler you just created, **teamawesome-tickit-crawler**, and click on **Run crawler**

	<img src="../images/skitch.22.png" alt="drawing" width="600"/>

	Watch the Crawler console for your job to finish successfully (it should take ~2 minutes). *Status* must change from **Starting** to **Ready**

1. Using the navigation menu on the left, navigate to **Tables**

1. You should see several tables has been created.