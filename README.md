# adf-metadata-driven-ingestion
Repository for Metadata driven Data Ingestion

# Azure Data Factory – Metadata Driven Ingestion Framework

## Overview
This repository demonstrates a metadata-driven ingestion framework built using Azure Data Factory (ADF).  
The solution dynamically ingests Excel files from Azure Blob Storage and lands them into Azure Data Lake Storage (ADLS Gen2) following a Bronze layer design pattern.

The pipeline is designed to be scalable, reusable, and aligned with modern data lake architecture principles.

---

## Architecture
Source (Excel files)  
→ Azure Data Factory (Metadata-driven pipeline)  
→ Azure Data Lake Storage Gen2 (Bronze layer)

---

## Key Features
- Metadata-driven ingestion using control files
- Dynamic source and destination handling
- ForEach loop for processing multiple entities
- Segregation of Master and Transaction data
- Automatic cleanup of source files using Delete activity
- Parameterized datasets and linked services
- GitHub-integrated ADF project

---

## Pipeline Flow Explanation

1. **Lookup – Metadata File**
   - Reads configuration metadata (source file name, target folder, data type).
   - Drives the pipeline dynamically without hardcoding values.

2. **ForEach Activity**
   - Iterates over metadata records.
   - Enables scalable ingestion for multiple files/entities.

3. **Copy Activity**
   - Copies Excel data from Blob Storage to ADLS Gen2.
   - Destination folders are dynamically created based on metadata.
   - Data is classified into Master or Transaction zones.

4. **Delete Activity**
   - Deletes the source file after successful ingestion.
   - Prevents duplicate processing and ensures idempotency.
     
5. **Event Trigger**
   - The Pipeline is triggered once a file is placed in the Blob Storage.

---

## Bronze Layer Justification
This ingestion qualifies as a Bronze layer because:
- Data is stored in raw or lightly structured form
- Minimal transformations are applied
- Source fidelity is preserved
- Acts as the foundation for Silver and Gold layers

---

## Tech Stack
- Azure Data Factory
- Azure Blob Storage
- Azure Data Lake Storage Gen2
- GitHub

---

## How to Deploy
1. Clone this repository
2. Import ARM templates into Azure Data Factory
3. Configure linked services with your Azure credentials
4. Update metadata file paths
5. Trigger the pipeline

---

## Author
Azure Data Engineering | Analytics Architecture

--

## Architecture Diagram
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/7115d78a-d49f-4a0c-a4bd-156c48704073" />

