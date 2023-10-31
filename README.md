# Azure Databricks Data Processing and Reporting
This project outlines the steps to set up an Azure Databricks environment for data processing and reporting. Follow these instructions to create 
necessary resources, process data, and generate insightful reports.

## Project Overview
### Step 1: Resource Group and Azure Resources Setup
- Create an Azure resource group.
- Create the following Azure resources:
  - Databricks workspace.
  - Storage account with three empty containers: Landing, Staging, and Reporting.
- Upload 'orders.csv' and 'customers.csv' to the Landing container of the storage account.
### Step 2: Databricks Workspace and Cluster Configuration
- Launch the Azure Databricks workspace.
- Create a single-node cluster inside the workspace that terminates after 30 minutes of inactivity. Choose 'Standard_DS3_v2' with a configuration of 14GB RAM and 4 cores.
### Step 3: Data Processing and Transformation
- Create a notebook in the Databricks workspace.
- Execute the following tasks in the notebook:
  -Mount the Azure Storage to DBFS and mount all three containers.
  -Create Spark DataFrames for 'orders' and 'customers' data and enforce the schema 
  -Write a Spark transformation on the 'orders' DataFrame to add new columns 'order_year' and 'order_month' by extracting them from 'orders_date.'
  -Store the transformed 'orders' and 'customers' data in a suitable format to optimize storage and query performance, considering partitioning based on 'order_year,' 'order_status,' and 'state' from the customers' data.
### Step 4: Data Analysis and Reporting
- Create Spark DataFrames for 'customers' and 'orders' using data from the Staging container.
- Write optimized queries to retrieve details of customers, combining data from both tables, and perform an optimized join.
- Store the query results in the Reporting container, partitioned by 'city,' 'state,' 'status,' and 'order_year.'
### Step 5: SQL View Creation and Querying
- Create a temporary SQL view containing concatenated customer names, city, order date, status, state, order year, and order month for all customers.
- Cache the view for improved performance in subsequent operations.
- Write a SQL query on the cached view to find names of all customers in the state 'TX,' with 'COMPLETE' status, and in the year 2014.
- Parameterize the query to take inputs dynamically from widgets in the notebook.
- Add widgets for 'State' (dropdown), 'Status' (dropdown), 'order_year' (textbox), and 'order_month.'
- Write a query to calculate the total number of customers based on the values selected in the above widgets.
## Conclusion
This project demonstrates the setup and utilization of Azure Databricks for data processing and reporting. By following these steps, you can efficiently manage and analyze data, generate reports, and leverage dynamic querying for enhanced insights.
