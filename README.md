his project demonstrates an end-to-end ETL (Extract, Transform, Load) pipeline. It fetches live football competition data (including leagues like Premier League, Champions League, and World Cup) via an API, processes it into a structured format using Pandas, and automates the data injection into a MySQL relational database.

🛠️ Tech Stack
Language: Python 3.14+
Libraries: Pandas, SQLAlchemy, PyMySQL, Requests
Database: MySQL Workbench
API Source: Football-Data.org

⚙️ ETL Workflow
1. Extraction (E)
Used the requests library to connect to the Football-Data API.
Authenticating requests using a secure X-Auth-Token.
Retrieved real-time JSON data for 13 global competitions (Brazil, England, Germany, etc.).

2. Transformation (T)
JSON Parsing: Extracted nested area information from the JSON response.
Data Wrangling: Flattened the nested dictionary structure into a clean tabular format.
DataFrame Construction: Built a structured Pandas DataFrame with columns: id, name, code, and flag.

3. Loading (L)
Established a connection to the local MySQL server using create_engine from SQLAlchemy.
Automation: Automated the data transfer to a table named standings within the football_database.
Overwrite Logic: Used if_exists="replace" to ensure the database always contains the most up-to-date competition list.

📊 Database Schema Preview
After execution, the data is stored in MySQL with the following structure:
id: Unique identifier for the geographical area.
name: Name of the country/region (e.g., Brazil, England).
code: Country ISO code (e.g., BRA, ENG).
flag: URL to the country's official crest/flag.


<img width="546" height="431" alt="loaded_data" src="https://github.com/user-attachments/assets/bfa4502a-39a3-4351-a1f2-4c9b557f2a5e" />

