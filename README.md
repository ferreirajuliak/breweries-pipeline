# Breweries Data Pipeline 🍺

## Overview
This project implements a **data pipeline on Databricks** to ingest, transform, and aggregate data from the [OpenBreweryDB API](https://www.openbrewerydb.org/).  
The pipeline is structured into **bronze, silver, and gold layers**, following the **medallion architecture** for simplicity, modularity, and scalability.  

The pipeline is orchestrated via a **Databricks Job** that runs daily, ensuring up-to-date data and automated monitoring.  

---

## Architecture & Design Choices

### Medallion Architecture
- **Bronze** → Raw ingestion of data from external API, stored with minimal transformations.  
- **Silver** → Cleaned and standardized data with enforced schema, deduplication, and basic quality rules.  
- **Gold** → Aggregated and validated tables optimized for analytics and reporting.

---

## Running the Pipeline in Databricks

## 0. Create a Databricks Free Edition Account  
- If you don’t already have one, sign up for a free Databricks Free Edition account:  
   https://www.databricks.com/learn/free-edition
- Follow the sign-up instructions and log in to access your workspace.  

1. **Import notebooks**  
   - Upload the notebooks (`bronze_ingest.ipynb`, `silver_transform.ipynb`, `gold_aggregate.ipynb`) into your Databricks workspace.  

2. **Set up the orchestration**  
   - In the Databricks UI, go to **Jobs & Pipelines**.  
   - In Create New select **Job**.  
   - In the job creation screen, select **Edit as YAML**.  
   - Copy the content of `brewerie-data-pipeline-job.yaml` into the editor.  
   - Update the `<your-email>` placeholders with your own email for job notifications.  
   - Save the job configuration.  

3. **Run the job manually**  
   - Trigger the job in the Databricks Jobs UI.  
   - The job will execute tasks in order:  
     - Bronze → Silver → Gold  

4. **Schedule**  
   - The pipeline is scheduled to run **daily** (interval = 1 day).  
   - You can modify the schedule in the job configuration file or in the Databricks Jobs UI.  
