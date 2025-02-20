# Azure Data Factory ETL Pipeline

## Overview

This project demonstrates an **ETL (Extract, Transform, Load) pipeline** built using **Azure Data Factory (ADF)**. The pipeline automates the process of ingesting CSV logs from **Azure Data Lake** and loading them into an **Azure Synapse Analytics (SQL Data Warehouse)** table for structured analysis.

## Architecture

![Image](https://github.com/user-attachments/assets/8b5785ee-3ad9-4cb7-b68b-06313e15ee64)

### Data Flow:

1. **Source:** CSV files stored in **Azure Data Lake Storage Gen2**.
2. **Processing:** A **Copy Activity** in ADF extracts data from CSV, applies necessary transformations, and maps it to the Synapse schema.
3. **Destination:** Data is loaded into an **Azure Synapse Analytics table** for further analysis.
4. **Automation:** A **scheduled trigger** runs every **5 minutes** to automate the data movement.

### Technologies Used:

- **Azure Data Factory (ADF)** - Orchestration & ETL
- **Azure Data Lake Storage (ADLS Gen2)** - Storing raw CSV files
- **Azure Synapse Analytics (SQL DW)** - Storing structured data
- **Azure Blob File System (ABFS)** - Data access in ADLS
- **GitHub Integration** - Version control & CI/CD

## Pipeline Components

- **Dataset:**
  - Source dataset pointing to CSV files in Azure Data Lake.
  - Defined schema and delimiter settings.
  - Target dataset mapping to the Synapse table `PoolActivityLog`.
  - Schema definition ensuring proper data typing.
- **Linked Services:**
  - `hiimjacekdatalake1`: Connects to Azure Data Lake Storage.
  - `hiimjacekdedicatedpool`: Connects to Azure Synapse Analytics.
- **Pipeline:**
  - **Copy Activity** moves data from ADLS to Synapse.
  - **Tabular Translator** ensures correct type conversion.
  - **Write Behavior:** `Insert` mode used to append data.
- **Trigger:**
  - Runs every 5 minutes to automate the data pipeline.

## Future Enhancements

- Add **data validation** before loading into Synapse.
- Implement **incremental data loading** to optimize storage and performance.
- Monitor pipeline using **Azure Monitor & Log Analytics**.
