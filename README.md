This repository is a reference implementation of a **financial data ETL pipeline** based on my R – Financial project experience. It ingests transactional data from APIs and files, transforms it into a standardized schema, and loads it into **Azure Synapse** (or AWS Redshift).  
The goal is to enable **scalable, repeatable, and testable** financial data workflows.

🏗 Architecture
```
          +-------------+
          | API / Files |
          +------+------+ 
                 |
          [src/etl/ingest_api.py]
                 |
          +------v------+
          | Transform   |  <- [src/etl/transform.py]
          +------+------+ 
                 |
          +------v------+
          | Synapse DW  |  <- [src/etl/load_to_synapse.py]
          +-------------+
```

🔧 Tech Stack
- **Python 3.10+**
- **Azure Synapse** / AWS Redshift
- **Azure Data Factory** (for orchestration)
- **Pandas**, **SQLAlchemy**, **pyodbc**
- **GitHub Actions** (CI/CD)
- **pytest** (unit testing)

📂 Project Structure
```
r-financial-etl/
├── src/
│   ├── etl/
│   │   ├── ingest_api.py
│   │   ├── transform.py
│   │   └── load_to_synapse.py
│   ├── config.py
│   └── main.py
├── tests/
├── infra/azure_data_factory_template.json
├── .env.example
├── requirements.txt
└── README.md
```

⚙️ Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/r-financial-etl.git
   cd r-financial-etl
   ```
2. Create virtual environment & install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```
3. Configure environment variables:
   ```bash
   cp .env.example .env
   # Fill in API_BASE_URL, API_KEY, Azure Synapse connection string
   ```

🚀 Usage
- **Dry run** (preview transformations without loading to DW):
  ```bash
  python src/main.py --mode dryrun
  ```
- **Production run** (ETL into Synapse):
  ```bash
  python src/main.py --mode run
  ```

🧪 Testing
```bash
pytest -q
```

⚡ CI/CD
- On every push, GitHub Actions:
  - Runs unit tests
  - Lints Python code
  - (Optional) Deploys to Azure via service principal

📈 Future Improvements
- Support for multiple currency conversions
- Automatic schema evolution detection
- Integration with Power BI dashboards
