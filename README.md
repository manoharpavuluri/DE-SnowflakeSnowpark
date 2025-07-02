# Snowflake Snowpark Data Engineering Project

## Overview
This project demonstrates a data engineering workflow using Snowflake's Snowpark for Python. It ingests, transforms, merges, and analyzes sales and sales items data, leveraging Snowflake's scalable cloud data platform and the Snowpark API for advanced data processing.

## Architecture & Technologies
- **Snowflake**: Cloud data warehouse for storage and compute
- **Snowpark for Python**: DataFrame-style API for data engineering in Snowflake
- **Pandas**: Local data manipulation and CSV handling
- **TOML**: Configuration management
- **Custom UDFs**: User-defined functions for data transformation
- **Jupyter Notebook**: Interactive development and documentation

## Functional Flow
1. **Configuration**: Reads Snowflake connection details from a TOML config file (not included in repo for security).
2. **Session Creation**: Establishes a Snowpark session using the config.
3. **Data Ingestion**: Reads sales and sales items tables from Snowflake.
4. **Transformation**:
   - Flattens nested JSON data
   - Extracts and normalizes fields
   - Applies UDFs (e.g., sorts item arrays)
5. **Merge Logic**: Merges new sales items data from CSV into Snowflake tables, handling upserts.
6. **Automation**: Automates extraction, transformation, and loading (ETL) steps.
7. **Output**: Writes processed data back to Snowflake tables for analytics.

## Setup Instructions
1. **Clone the repository**
2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Prepare configuration**:
   - Create a TOML file (e.g., `Snowflake_Snowpark_1sttry_config.toml`) with your Snowflake credentials:
     ```toml
     [snowflake]
     account = "<your_account>"
     user = "<your_user>"
     password = "<your_password>"
     role = "<your_role>"
     warehouse = "<your_warehouse>"
     database = "<your_database>"
     schema = "<your_schema>"
     ```
   - Ensure this file is listed in `.gitignore` and not committed.
4. **Run the notebook**:
   - Open `Snowflake_Snowpark_1sttry.ipynb` in Jupyter or Colab
   - Follow the cells sequentially

## Business Logic & Data Model
- **Tables**: `RAW_CREDITCO_SALES`, `RAW_CREDITCO_SALES_ITEMS`, `sales_items`, `sales_data`
- **Key Operations**:
  - Flattening and extracting nested JSON
  - Hashing IDs for privacy
  - Merging new data with existing tables
  - Applying UDFs for custom transformations
- **Data Sources**: Snowflake tables, local CSVs, and JSON files

## Security & Configuration
- Sensitive credentials are managed via a TOML config file, not included in the repo.
- `.gitignore` is updated to exclude config files.

## Dependencies
See `requirements.txt` for all Python dependencies.

## File Structure
- `Snowflake_Snowpark_1sttry.ipynb`: Main notebook with code and documentation
- `requirements.txt`: Python dependencies
- `README.md`: This documentation
- `Snowflake_Snowpark_1sttry_config.toml`: (User-provided, not in repo) Snowflake credentials
- Data files: CSV/JSON files referenced in the notebook (user-provided)

## Future Improvements
- Modularize code into Python scripts for production use
- Add automated testing and CI/CD integration
- Parameterize data sources and destinations
- Enhance error handling and logging
- Add data quality checks and validation steps
- Integrate with orchestration tools (e.g., Airflow)
- Provide sample/mock config and data files for easier onboarding

## Additional Notes
- Ensure you have access to a Snowflake account and the necessary permissions.
- For large-scale or production use, consider refactoring the notebook into maintainable Python modules and pipelines.