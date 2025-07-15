# 🚀 API Performance Testing Tool 

## 🛠️ Installation

### Prerequisites

- Python 3.7+
- pip package manager
Dependency  manually install

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

🔷 OVERVIEW
This is a web-based API tester (like Postman) with the ability to trigger Locust-based performance testing. It lets you:

Send GET/POST/PUT/DELETE API requests.

View responses (JSON or plain text).

Save request history in a sidebar, grouped by date.

Replay past requests.

Launch Locust for load testing.


🔍 CODE BREAKDOWN
✅ Imports

import streamlit as st       # UI framework
import subprocess            # For launching Locust via CLI
import requests              # To send API requests
import json                  # For parsing headers/body
import os                    # File operations (history, .env)
from urllib.parse import urlparse  # To split URL into host/path
from datetime import datetime       # Timestamps
import webbrowser            # Opens Locust dashboard in browser
import streamlit.components.v1 as components
⚙️ st.set_page_config(...)
Sets the layout to wide and names the browser tab "TIBCO API Tester".

📜 History File
python

HISTORY_FILE = "history_tibcoresponse.json"
Used to store the request/response history (manually logged).

🔁 load_history() & save_history_data()
These functions:

Load existing request history from HISTORY_FILE

Save a new request at the top of the history list

🎨 CSS Styling Loader:
if os.path.exists("ui.css"):
    with open("ui.css") as f:
        st.markdown(f"<style>{f.read()}</style>", unsafe_allow_html=True)
Loads custom CSS (like button colors, rounded corners, etc.)

🧾 Form Inputs for API Testing:
api_url = st.text_input(...)
method = st.selectbox(...)
headers_input = st.text_area(...)
json_body = st.text_area(...)
num_users = st.number_input(...)
spawn_rate = st.number_input(...)
run_time = st.text_input(...)
User enters:

API endpoint

Method

Headers (JSON)

Body (JSON)

Locust-specific configs (user count, spawn rate, run time)

💾 save_history(...)
This saves test configuration and Locust responses to history.json.

📆 group_history_by_exact_date(...)
Groups history items by formatted date (Jul 15, Jul 14, 2024).
Returns:
{
  'Jul 14': [(entry1, idx1), (entry2, idx2)],
  'Jul 13, 2024': [...]
}
This lets the sidebar show expandable sections grouped by date.

❌ delete_history_entry(...)
Deletes a request from history by index. Reruns the Streamlit app after deletion.

📚 Sidebar History Rendering:
st.sidebar.header("🕘 Request History")
For each grouped history date:

Shows an expander (e.g., 📅 Jul 14)

Inside each expander:

Replay button: Loads the previous request

Delete button: Removes it from history

🔘 Two Main Buttons
✅ Send Request Button (Main Testing Function)
Parses headers/body

Sends request using requests

Displays JSON/text response

Saves to history_tibcoresponse.json

🐜 Run Locust Test Button
Parses the URL to extract host/path

Writes variables like LOCUST_HOST, REQ_URL, REQ_METHOD etc. to .env

Runs:
locust --config locust.conf
Opens http://localhost:8089 in browser

Saves test config (including user count, spawn rate, etc.) to history.json





