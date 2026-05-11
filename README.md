# Build a Location Intelligence ADK Agent with MCP Servers


https://github.com/user-attachments/assets/bc95977d-7756-42eb-a7e8-1cc5653b4c16


> Build an AI-powered bakery intelligence agent using Google ADK, BigQuery, Google Maps, MCP, and Gemini 3.1 Pro.

---

## Introduction

This project demonstrates how to create a Location Intelligence Agent capable of combining:

- BigQuery analytics
- Google Maps intelligence
- MCP server integrations
- Gemini reasoning

The agent helps analyze bakery business opportunities using:

- demographic data
- foot traffic analysis
- competitor pricing
- sales forecasting
- real-world location intelligence

## Architecture Diagram

<img width="3620" height="1802" alt="Agent - Architecture Diagram" src="https://github.com/user-attachments/assets/4741bb73-4246-44c3-a1ed-2895042f7064" />


---

## Prerequisites

### Requirements

- Google Cloud Project
- Billing Enabled
- Web Browser
- Basic terminal knowledge

---

## 1. Setup Google Cloud

### Create or Select a Project

1. Open Google Cloud Console
2. Create or select a project
3. Enable billing

### Screenshot

![Create Google Cloud Project](https://codelabs.developers.google.com/static/adk-mcp-bigquery-maps/img/a3dd2e6dddc8f691_1920.png)

---

## 2. Start Cloud Shell

Activate Cloud Shell from the top-right corner.

### Screenshot

![Activate Cloud Shell](https://codelabs.developers.google.com/static/adk-mcp-bigquery-maps/img/404e4cce0f23e5c5_1920.png)


### Verify Authentication

```bash
gcloud auth list
```


### Verify Active Project

```bash
gcloud config get project
```


### Export Project ID

```bash
export PROJECT_ID=$(gcloud config get project)
```

---


## 3. Clone Repository

Clone repository:

```bash
git clone https://github.com/google/mcp.git
```

Navigate to project:

```bash
cd mcp/examples/launchmybakery
```

---

## 4. Authenticate

Authenticate with Google Cloud:

```bash
gcloud auth application-default login
```

> Re-authenticate if the session exceeds 60 minutes.

---

## 5. Configure Environment & BigQuery

### Run Environment Setup

```bash
chmod +x setup/setup_env.sh
./setup/setup_env.sh
```

This script:

- Enables APIs
- Creates `.env`
- Configures Maps API Key


### Setup BigQuery

```bash
chmod +x ./setup/setup_bigquery.sh
./setup/setup_bigquery.sh
```

This script creates:

- Cloud Storage bucket
- BigQuery dataset
- Required tables

---

## 6. Verify Dataset in BigQuery

Open BigQuery Console:

```text
https://console.cloud.google.com/bigquery
```

Verify dataset:

```text
mcp_bakery
```

Tables created:

- demographics
- bakery_prices
- sales_history_weekly
- foot_traffic

### Screenshot

![Verify Dataset](https://codelabs.developers.google.com/static/adk-mcp-bigquery-maps/img/6bd0a0cd7522dd11_1920.jpeg)

---

## 7. Install ADK

Create virtual environment:

```bash
python3 -m venv .venv
```

Activate environment:

```bash
source .venv/bin/activate
```

Install ADK:

```bash
pip install google-adk==1.28.0
```

Navigate to agent directory:

```bash
cd adk_agent/
```

---

## 8. Project Structure

```text
launchmybakery/
├── data/
├── adk_agent/
│   └── mcp_bakery_app/
│       ├── agent.py
│       ├── tools.py
│       └── .env
├── setup/
└── cleanup/
```

---

## 9. MCP Tool Configuration

### Maps MCP Toolset

Used for:

- Place search
- Competition analysis
- Route calculations
- Location intelligence

### Example

```python
def get_maps_mcp_toolset():
```

Uses:

- Maps API Key
- Streamable HTTP MCP connection


### BigQuery MCP Toolset

Used for:

- SQL execution
- Sales analytics
- Demographic analysis
- Forecasting

### Example

```python
def get_bigquery_mcp_toolset():
```

Uses:

- OAuth authentication
- BigQuery MCP server

---

## 10. Agent Definition

The agent uses Gemini 3.1 Pro.

### Example

```python
root_agent = LlmAgent(
    model='gemini-3.1-pro-preview'
)
```

Capabilities:

- BigQuery reasoning
- Maps reasoning
- Unified business intelligence

---

## 11. Run the Agent

Navigate to:

```bash
cd adk_agent/
```

Start ADK web server:

```bash
adk web --allow_origins 'regex:https://.*\.cloudshell\.dev'
```

Expected output:

```text
ADK Web Server started
http://127.0.0.1:8000
```

---

## 12. Open ADK UI

### Option 1

Open:

```text
http://127.0.0.1:8000
```

### Option 2

Use Cloud Shell Web Preview:

1. Click Web Preview
2. Change port
3. Enter `8000`

### Screenshot

![Change Port](https://codelabs.developers.google.com/static/adk-mcp-bigquery-maps/img/open_adk_ui_1920.png)

---

## 13. Interact with the Agent

Example prompt:

```text
Find the zip code with the highest morning foot traffic score in Los Angeles.
```

### Screenshot

![Interact with Agent](https://codelabs.developers.google.com/static/adk-mcp-bigquery-maps/img/5f2a48bebfc49709_1920.png)

---

## 14. More Example Prompts

### Competition Analysis

```text
Search for bakeries in that zip code to see if the market is saturated.
```

### Premium Pricing

```text
Find the maximum price for a Sourdough Loaf in the LA Metro area.
```

### Revenue Forecast

```text
Forecast December 2025 revenue using historical sales data.
```

### Logistics Validation

```text
Find the nearest Restaurant Depot and ensure drive time is under 30 minutes.
```

---

## 15. Cleanup

Run cleanup script:

```bash
chmod +x ../cleanup/cleanup_env.sh
./../cleanup/cleanup_env.sh
```

Removes:

- BigQuery datasets
- Cloud Storage buckets
- API keys

---

## 16. Key Learnings

- Infrastructure automation
- MCP integrations
- Multi-tool AI orchestration
- Location intelligence workflows
- Business reasoning with Gemini

---

## Technologies Used

- Google ADK
- Gemini 3.1 Pro
- MCP
- BigQuery
- Google Maps
- Python
- Cloud Shell

---

## Conclusion

I successfully built a Location Intelligence AI Agent capable of combining:

- Enterprise data analysis
- Real-world mapping intelligence
- Sales forecasting
- Competitive research

Powered by:

- MCP
- Gemini
- BigQuery
- Google Maps

<img width="1365" height="644" alt="SS-08" src="https://github.com/user-attachments/assets/ddbed36a-a0ae-4a48-a2bc-db3fe6ae8547" />
<img width="1365" height="642" alt="SS-10" src="https://github.com/user-attachments/assets/f42feda4-a023-44f2-8013-17aeaeefb5c7" />

---

## 1. Interaction with Relevant Question

Ask the agent a relevant bakery/business intelligence question.

### Example

```text
Find the zip code with the highest morning foot traffic score in Los Angeles.
```

Capture:

- Your prompt
- Agent response
- Tool execution (if visible)

<img width="1365" height="641" alt="SS-02" src="https://github.com/user-attachments/assets/c9645d55-649e-4a6d-8694-19e69628ef86" />
<img width="1366" height="637" alt="SS-03" src="https://github.com/user-attachments/assets/ba62cb41-f62e-498f-b551-9a9dd803a362" />

---

## 2. Interaction with Irrelevant Question

Ask the agent an unrelated or irrelevant question.

### Example

```text
What if I want to open it at the moon?
```

or

```text
Who won the football match yesterday?
```

<img width="1366" height="638" alt="SS-07" src="https://github.com/user-attachments/assets/400b4b7a-2081-4278-9670-950338da26f0" />


---

Capture:

- Your prompt
- Agent response


<img width="1366" height="635" alt="SS-09" src="https://github.com/user-attachments/assets/c2939250-4d32-4bab-9650-d9f64f2c8aa4" />
<img width="1361" height="640" alt="SS-11" src="https://github.com/user-attachments/assets/8ef11860-7740-492a-97b4-c42945f5f57c" />
<img width="1366" height="768" alt="SS-14" src="https://github.com/user-attachments/assets/c6626204-48d8-4879-9fc1-77e74c7a0255" />


This helps evaluate:

- Agent behavior
- Instruction following
- Response handling for irrelevant queries

---

## Resources & Attribution

### Official Repository:
[![Google MCP](https://img.shields.io/badge/Google-MCP-green?style=for-the-badge&logo=google&logoColor=white)](https://github.com/google/mcp)


### Workshop Organizers:
Conducted by GeeksforGeeks in collaboration with Google.

<img width="507" height="238" alt="WorkShop" src="https://github.com/user-attachments/assets/2b118237-2b60-4d3e-9b53-7edab26b969e" />
