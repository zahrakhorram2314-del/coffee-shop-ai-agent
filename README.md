# coffee-shop-ai-agent
# ☕ Coffee Shop Manager AI Agent (Google Cloud Run & ADK)

An intelligent agentic AI solution built with Python, FastAPI, and Google ADK, designed to automate coffee shop inventory and shift scheduling based on POS data and university event calendars.

## 🌟 Key Features
- **Data Integration:** Processes raw sales CSVs from Google Sheets.
- **Contextual Reasoning:** Correlates sales spikes with campus events (e.g., graduation ceremonies).
- **Human-in-the-Loop Safety:** Prompts the user (`YES/NO`) before applying changes to Google Sheets to mitigate automation bias.
- **Cloud Ready:** Containerized with Docker and designed for deployment on Google Cloud Run.

## 🏗️ Architecture & Deployment

### 1. Requirements (`requirements.txt`)
`fastapi`, `uvicorn`, `google-adk`, `google-auth`, `google-api-python-client`

### 2. Cloud Run Deployment Command
```bash
gcloud beta run deploy coffee-mgr-agent \
    --source=. \
    --region=$REGION \
    --set-env-vars GOOGLE_GENAI_USE_VERTEXAI=1 \
    --service-account coffee-shop-agent-sa@$GOOGLE_CLOUD_PROJECT.iam.gserviceaccount.com
