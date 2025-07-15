# 🚀 API Performance Testing Tool 

## 🛠️ Installation

### Prerequisites

- Python 3.7+
- pip package manager
- ### Install Dependencies

```bash
# Using Make (recommended)
make install-ui

# Or manually
pip install -r requirements.txt
pip install -r streamlit_requirements.txt
```

## 📖 Usage

### Streamlit Dashboard (Recommended)

```bash
# Launch the web dashboard
make streamlit

# Configure endpoints through the web UI
# Run tests and view results in real-time
``
## 📦 Features

- ✅ Send `GET`, `POST`, `PUT`, `DELETE` requests to any API
- ✅ View real-time responses (JSON/text)
- ✅ Catch and display request errors (400/500/etc.)
- ✅ Save request history
- ✅ Run one-off test request as a **Locust simulation**
- ✅ Beautiful download button for response output
- ✅ Organized, modular folder structure

---

## 🗂 Folder Structure

```plaintext
.
├── main.py                      # Streamlit entry point
├── components/
│   ├── api_request.py          # Handles Send Request logic
│   └── locust_runner.py        # Handles Run Locust Test logic
├── utils/
│   ├── env_writer.py           # Writes .env for Locust
│   └── history.py              # Save/load/delete request history
├── locustfile.py               # Locust load testing logic
├── ui.css                      # Custom UI styling
├── history.json                # Saved request history
├── .env                        # Generated env for Locust
└── README.md                   # You're here!

How to Run
1. ✅ Start Streamlit App
      streamlit run main.py

⚙️ How It Works
🧪 1. Send API Request
Fill in the URL, method, headers, and body

Click Send Request

See the formatted response in the UI

You can also download the response JSON

🐜 2. Run Locust Test
Click Run Locust Test

Sends one request (like Locust) and shows response/error in Streamlit

You can later expand this to launch full load tests

🖼️ UI Example
(Include screenshots here if needed — like api_request, response, locust output)

🛠️ Technologies Used
Streamlit – UI

Requests – HTTP calls

Locust – Performance testing

Python 3.7+






