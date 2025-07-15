# API-Performance_Testing_Tool
api_tester/
├── main.py                     # 🔷 Main Streamlit entry point
├── locustfile.py              # 🔥 Locust load testing logic
├── .env                       # 🌍 Auto-generated env file
├── locust.conf                # ⚙️ Locust config file
├── ui.css                     # 🎨 Optional custom styles
├── requirements.txt           # 📦 Python dependencies
│
├── utils/
│   ├── __init__.py
│   ├── history.py             # 🕘 Save/load/delete history
│   ├── env_writer.py          # ✍️ Write .env file for Locust
│
├── components/
│   ├── __init__.py
│   ├── sidebar.py             # 📚 Sidebar history logic
│   ├── api_request.py         # 📡 Send requests logic
│   ├── locust_runner.py       # 🚀 Locust command trigger
