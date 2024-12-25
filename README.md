# Azure-End-To-End-Data-Engineering-Project

## Adventure Works

Worked on End-to-End Azure Data Engineering project from scratch where I leverage powerful technologies like Azure Data Factory, Azure Data Lake, Databricks, Azure Synapse Analytics, and Apache Spark, along with managed identities, API connections, and many more.

**What I learnt:**

•	How to design and implement a robust data pipeline using Azure Data Factory.

•	The process of data integration and transformation with Databricks.

•	Utilizing Azure Synapse Analytics for efficient data warehousing and analytics.

•	Best practices for handling big data solutions and real-time data processing with Apache Spark.

We used Medallion Architecture (Layers), it’s a kind of approach we followed in data engineering solutions.  We make our data to travel into three different zones bronze (raw Data), silver (Transformed), and gold (Serving layer).

**About Dataset (Why I pick this Dataset?)**

This data is available on Kaggle, it was full of tables, and this gives you an advantage when you showcase your project that involved so many tables, because they know that this person has applied so many Joins, Lookups while completing this project. This dataset was past three years of sales data 2015, 2016, 2017. Adventure Works is an ideal data set if you want to work with end-to-end solution because we can perform so many joins, transformations, and we can do a lot more with these tables. That’s why I picked this dataset. In this dataset we have (2 Fact tables (Sales, returns), and 6-dimension tables)

### Microsoft Azure Account Home Page

![azure](https://github.com/user-attachments/assets/137c7b40-b1f3-469b-b5d9-622c0bd781de)

### Phase 1:

We will be pulling our data from data source (GitHub), and we will be pushing this data to our Data Lake storage account (bronze zone) this process known as (Ingesting of the Data dynamically).

•	Create Resource Group where we keep all our resources.

•	Create data lake Storage account (by default it creates Blob storage account you need to tick Hierarchical namespace).

•	 Create containers (bronze, silver, and gold) in storage account.

•	Create Azure Data Factory (Dynamic Data Pipeline), use of Copy data Activity load the data from GitHub account and pushed it into Azure Data Lake storage account (Destination) (made connection with GitHub and Data Lake).

•	Our data source was GitHub account within the folder we have all our data set.

•	Dynamic Data Pipeline: There are three parameters changing for copying data activity:

   Relative URL (base URL) changing
   
   Sink (destination) Folder name is changing
   
   Sink (destination) Filename itself changing
   
   Created git.Json file where the links of these (parameters) were stored in the form of dictionary.
   Copy Activity, Foreach Loop, lookup Activity (if we want to look an output of our file)

![pipeline](https://github.com/user-attachments/assets/4a68411a-808f-486e-96d1-181fdf9fc01a)

![pipeline2](https://github.com/user-attachments/assets/87d603bf-5e2c-4f48-9669-2808eeb1e9cb)

![bronze](https://github.com/user-attachments/assets/c13f502a-7d89-43ff-9151-31dcac57eaa8)

### Phase 2:

**Azure Databricks:** In phase2 of the project we will pick data from bronze layer and Ingest data into silver layer with some transformations on to the data tables.

•	Created compute because we are applying transformation on the data, processing the data using compute (It is a cluster). Need to create cluster for our workflows.

•	Give permission to access the data from Data lake storage account by the Databricks Application.

•	Create Notebook and read the data tables, transformed it pushed into silver layer into the parquet format.

•	Example in Sales Table: 1) transforming stock date into timestamp, 2) Replace Order Number S with T, 3) Multiplication of orderLineItem * OrderQuantity as Total Sales.

•	Produce charts on Notebook by applying aggregate functions on sales dataset like Group By.

### Databricks Notebook video

https://github.com/user-attachments/assets/72aa3811-00b5-405a-8933-1f73ea53e47d

![silver](https://github.com/user-attachments/assets/fe4b02a1-fd42-44d4-8f28-4170d91a08a7)

### Phase 3:

**Azure Synapse Analytics:**

•	Usen of OPENROWSET Function to access the data from data lake silver layer.

•	Created views of all the data tables in the gold layer.

•	Create external tables and pushed views data into it.

•	Deploy azure synapse analytics with Power BI desktop, build the connectivity, copy the SQL endpoint, pull the data tables into Power BI, and then generate the report.

### Azure Synapse Analytics Video

https://github.com/user-attachments/assets/da7f8f2f-ce13-4851-90d1-44a66939a793




