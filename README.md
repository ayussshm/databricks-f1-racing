# 🏎️ databricks-f1-racing
This repository contains Databricks workspace for a personal project: Formula1 Racing Databricks Project. This project focuses on building end-to-end analytics pipeline on F1 racing data using Databricks and Azure Cloud. Data is ingested from Ergast API, and processed through Medallion Architecture (Bronze -> Silver -> Gold) to build curated models for visualization and insights in Power BI.

For a detailed overview of the project, please visit [this](https://wwww.ayush-m.com/projects/f1-racing-databricks-project.html) link.

---
## 📐 Architecture Overview
![Architecture Diagram](databricks_f1_architecture.jpg)
This project follows a classic Medallion Architecture:

- **Bronze**: Raw JSON/CSV data from Ergast API stored as External Tables
- **Silver**: Cleaned, standardized tables (snake_case, deduped, metadata added) stored as Managed Tables
- **Gold**: Curated analytical models for reporting stored as Managed Tables

Services Used

- **Databricks** for data processing
- **Azure Data Lake Storage Gen2** for storage
- **Delta Lake** for ACID, MERGE, and time travel
- **Unity Catalog** for governance and lineage
- **Azure Data Factory** for orchestration
- **Power BI** for visualizations

## 📁 Repository Structure

```text
├── set-up/                                    # Mounting ADLS container (deprecated)
│   ├── 9. mount_adls_containers_for_project
│  
├── raw/                                       # Bronze layer table creation
│   ├── 1. create_raw_tables                
│
├── ingestion/                                 # Silver layer table creation
│   ├── 01. create processed Database       
│   ├── 1. ingestion_circuits_file
│   ├── 2. ingestion_races_file
│   ├── 3. ingestion_constructors_file
│   ├── 4. ingestion_drivers_file
│   ├── 5. ingestion_results_file
│   ├── 6. ingestion_pitstops_file
│   ├── 7. ingestion_lap_times_file
│   ├── 8. ingestion_qualifying_file
|
├── trans/                                     # Gold layer table creation
│   ├── 0. Create Presentation Database
│   ├── 1. race_results    
│   ├── 2. driver_standings
│   ├── 3. constructor_standings
│   ├── 4. calculated_race_results
|
├── analysis/                                  # Notebooks for analytics
│   ├── 1. find_dominant_driver  
│   ├── 2. find_dominant_teams
│   ├── 3. viz_dominant_drivers
│   ├── 4. viz_dominant_teams
|
├── includes/                                  # Commaon functions and configuration
│   ├── common_functions 
│   ├── configuration
|
├── adf/                                      # ADF pipeline definitions
│   └── dataset/
│   └── linkedService/
│   └── pipeline/
│   └── trigger/
│
├── utils/
│   └── 1. prepare_for_incremental_load       
│
├── databricks-f1-racing.dbc                  # DBC File for Project
├── databricks_f1_architecture.jpg            # Architecture digram for project
├── .gitignore
└── README.md
```
## ▶️ How to Run

1. Clone this repository
2. Create git folder in Databricks workspace and provide cloned repository url
3. Create metastore with extenal location for Catalog
4. Configure your ADLS Gen2 paths
5. Run the Bronze ingestion notebooks
6. Run Silver transformations
7. Run Gold model notebooks

## 📬 Contact
For any questions or feedback, reach out to me on:
- 📧 Email: ayushmanandhar10@gmail.com
- 🐙 GithHub: ayussshm
