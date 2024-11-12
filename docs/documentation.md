# Project Documentation: Data Science Job Trends Analysis with AWS

This document provides a detailed guide for setting up each AWS service used in this project to analyze data science job trends, ensuring a seamless setup and configuration.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Amazon S3 Setup](#amazon-s3-setup)
3. [IAM Role Configuration](#iam-role-configuration)
4. [AWS Glue Crawler and ETL Setup](#aws-glue-crawler-and-etl-setup)
5. [Amazon QuickSight Visualization](#amazon-quicksight-visualization)
6. [Data Source](#data-source)
7. [Troubleshooting](#troubleshooting)

### Project Overview

This project utilizes AWS services to automate the data processing pipeline for analyzing data science job trends. The pipeline involves data storage, cataloging, transformation, and visualization to generate insights into top job locations, hiring companies, roles, and required skills.

### Amazon S3 Setup

1. **Create S3 Buckets**:
   - Log in to the AWS Console and navigate to the **S3** service.
   - Create two buckets:
     - `job-trends-raw-data`: Stores raw job data files.
     - `job-trends-processed-data`: Stores cleaned and processed data ready for analysis.

2. **Upload Data**:
   - Download the dataset from [Kaggle's Data Science Jobs CSV](https://storage.googleapis.com/kagglesdsdata/datasets/1207291/2017105/Data_Science_Jobs.csv).
   - Upload this CSV file to the `job-trends-raw-data` S3 bucket.

### IAM Role Configuration

1. **Create IAM Role for AWS Glue**:
   - In the AWS Console, go to **IAM** and create a new role.
   - Select **Glue** as the trusted service and attach the following permissions:
     - `AmazonS3FullAccess`: Grants access to read and write in S3.
     - `AWSGlueServiceRole`: Grants Glue the permissions to access Data Catalog and perform ETL jobs.
     - `AmazonQuickSightAccess`: Allows QuickSight to access S3 and Glue data.

2. **Assign the Role to AWS Glue and QuickSight**:
   - Attach this role to AWS Glue for performing crawler and ETL jobs, and ensure QuickSight can access the Glue Data Catalog.

### AWS Glue Crawler and ETL Setup

1. **Configure Glue Crawler**:
   - Navigate to **AWS Glue** > **Crawlers** > **Add Crawler**.
   - Provide a name for the crawler, such as `job-trends-crawler`.
   - Set the data source as the `job-trends-raw-data` bucket.
   - Choose the IAM role you created earlier.
   - Run the crawler to automatically catalog the data, creating tables based on the CSV structure.

2. **Create a Glue Database**:
   - Go to **Databases** under AWS Glue and create a new database, e.g., `job_trends_db`.
   - This database will store the schema and metadata for your job data.

3. **Set Up Glue ETL Job**:
   - In AWS Glue, go to **Jobs** and create a new ETL job.
   - Select the **Source** as the Glue table created by the Crawler.
   - Choose **Transform** options to clean or filter data, if needed.
   - Set the **Target** as the `job-trends-processed-data` bucket.
   - Run the ETL job to clean and process the raw data, saving it in S3 for analysis.

### Amazon QuickSight Visualization

1. **Connect QuickSight to Glue Data Catalog**:
   - Go to **Amazon QuickSight** and select **Manage Data** > **New Dataset**.
   - Choose **Glue Data Catalog** as the data source and select the `job_trends_db` database.
   - Choose the table created from the processed data.

2. **Build the Dashboard**:
   - Create visualizations for key insights:
     - **Top Locations for Data Science Jobs**: Use a bar chart to show popular cities.
     - **Top 15 Companies Hiring in Data Science**: Create a list or table for top hiring companies.
     - **Top Roles in Data Science Jobs**: Visualize frequent job titles in a chart.
     - **Top Skills in Data Science Jobs**: Show in-demand skills in a word cloud or bar chart.

3. **Publish the Dashboard**:
   - Customize and publish the dashboard, enabling access to key insights for stakeholders.

### Data Source

The dataset used in this project is available from Kaggle at the following URL: [Data Science Jobs Dataset](https://www.kaggle.com/code/nickyeapen/data-science-job-trend-analysis/).

### Troubleshooting

- **Crawler or ETL Job Fails**:
  - Ensure the IAM role has the necessary permissions to read and write in the designated S3 buckets.
  - Verify that the Glue database and table configurations are correct.

- **Data Not Updating in QuickSight**:
  - If the data is updated, ensure you re-run the Glue ETL job to process the latest data.
  - Refresh the dataset in QuickSight or schedule regular updates to see the latest insights.

- **Permission Issues in QuickSight**:
  - Confirm the IAM role includes `AmazonQuickSightAccess` and permissions for Glue and S3.

This documentation provides the necessary details to replicate the setup, run the pipeline, and troubleshoot common issues. For further questions, please refer to the official AWS documentation.
