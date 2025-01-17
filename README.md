# Data Catalogues from Crawling Data using AWS Glue Studio 

<img width="640" alt="Screenshot 2025-01-17 at 12 35 52" src="https://github.com/user-attachments/assets/ee672d2a-5785-4490-a0ef-79252476d18e" />


# Activity Guide: Creating and Managing AWS Glue Crawlers for Data Cataloging

1. Scenario

- Context:
Valtara Analytics, a data analytics company, uses AWS S3 to store vast volumes of raw data. With growing data complexity, tracking structure and location becomes a challenge, hindering efficient data processing and analytics.
- Objective:
Use AWS Glue Crawlers to catalog and organize data in S3, streamlining ETL (Extract, Transform, Load) processes and ensuring quick data access.

2. Set Up AWS Environment

- Create IAM Role (IAM):
Go to the IAM Console and create a role with the following permissions:
AWSGlueServiceRole
AmazonS3FullAccess
Attach the role to AWS Glue to enable access to S3 and Glue resources.
- Prepare an S3 Bucket (Amazon S3):
Create an S3 bucket (e.g., data-insights-raw-data).
Organize the bucket into folders based on data categories (e.g., /sales/, /marketing/) and upload raw data files.

3. Create a Glue Database

- Open Glue Console:
Navigate to the AWS Glue Console and go to the Databases section.
- Add Database:
Click Add Database, provide a name (e.g., data_insights_catalog), and save.
This database will store metadata for the S3 data catalog.

4. Configure and Run a Glue Crawler

- Access Crawlers in Glue Console:
Go to the Crawlers section and click Add Crawler.
- Configure Data Source:
Choose S3 as the data source and provide the path to your S3 bucket (e.g., s3://data-insights-raw-data/).
- Assign IAM Role:
Attach the role created earlier to the crawler.
- Define Output:
Select the Glue database (data_insights_catalog) as the target for storing cataloged metadata.
- Schedule Crawler:
Schedule the crawler to run periodically (e.g., daily) to keep the catalog updated.
- Run the Crawler:
Execute the crawler and wait for it to scan and catalog the S3 data.

5. Verify the Data Catalog

- Check Metadata:
Navigate to the Tables section in the Glue Console to view the created metadata tables.
- Inspect Details:
Verify that the tables include schema information, such as column names, data types, and file locations.

6. Use the Catalog for ETL Processes

- Create Glue Jobs:
Use AWS Glue jobs to transform and load data using the cataloged metadata.
- Query with Athena:
Connect AWS Athena to the Glue catalog to run SQL queries directly on the S3 data.

7. Clean Up Resources

- Delete Glue Crawler and Database:
Go to the Glue Console, delete the crawler, and remove the database if no longer needed.
- Empty and Delete S3 Bucket:
Remove all objects from the bucket and delete it to avoid additional costs.
- Detach IAM Role:
Detach the policies from the IAM role and delete it.

8. Troubleshooting

- Issue: Crawler Fails to Access S3 Data:
Ensure the IAM role has the required AmazonS3FullAccess permission.
- Issue: Incorrect Schema Detection:
Adjust the crawler's configuration or validate the data format in S3.

9. Summary

Successfully created and managed AWS Glue Crawlers to catalog data in S3 buckets.
Simplified data discovery and enabled efficient ETL processes for Valtara.
