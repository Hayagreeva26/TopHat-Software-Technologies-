TopHat — SaaS Usage Analytics

📌 Overview
This project analyzes **user interaction logs** from a SaaS platform.  
It provides:
- **Session funnels**
- **User engagement heatmaps**
- **Anomaly detection** in KPIs
- Integration with MongoDB and PostgreSQL

🏗 Architecture
```
   MongoDB / Postgres
          |
   +------v------+
   | Data Loader |
   +------+------+
          |
   +------v------+
   | Analytics   | -- Funnels, Heatmaps, Anomaly Detection
   +-------------+
```

🔧 Tech Stack
- **Python 3.10+**
- **MongoDB**, **PostgreSQL**
- **Pandas**, **Statsmodels**
- **pytest**, **GitHub Actions**

📂 Project Structure
```
tophat-usage-analytics/
├── src/
│   ├── data/load_mongo.py
│   ├── analytics/funnels.py
│   └── analytics/anomaly_detector.py
├── tests/
├── .env.example
├── requirements.txt
└── README.md
```

⚙️ Setup
```bash
git clone https://github.com/<your-username>/tophat-usage-analytics.git
cd tophat-usage-analytics
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

🚀 Usage
- **Load sessions from MongoDB**:
  ```python
  from src.data.load_mongo import load_sessions
  df = load_sessions(limit=500)
  ```
- **Compute funnel**:
  ```python
  from src.analytics.funnels import compute_funnel
  steps = ['landing', 'signup', 'purchase']
  print(compute_funnel(df, steps))
  ```
- **Detect anomalies**:
  ```bash
  python src/analytics/anomaly_detector.py
  ```

🧪 Testing
```bash
pytest -q
```

⚡ CI/CD
- Runs on push via `.github/workflows/ci.yml`
- Executes unit tests automatically

📈 Future Improvements
- Real-time anomaly alerts
- Interactive dashboard with Plotly/Dash
- A/B test analytics

