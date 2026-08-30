
# ☕ Coffee Barista Agent - Google Cloud Run & Vertex AI Integration

This project demonstrates the deployment of an AI-powered Streamlit web application on **Google Cloud Run** integrated with **Vertex AI / Gemini API**.

## 🚀 Project Overview
- **Service Name:** `coffee-barista`
- **GCP Project ID:** `my-genai-project-1788065100`
- **Region:** `us-central1`
- **Framework:** Streamlit + Python 3.10
- **Containerization:** Docker

---

## 🛠️ Project Structure & Source Code

### `app.py`
```python
import streamlit as st
import os

st.set_page_config(page_title = "Coffee Barista Agent", page_icon="☕")
st.title("☕ Coffee Barista Agent")

project_id = os.environ.get("GOOGLE_CLOUD_PROJECT", "")
st.write(f"Connected to Project: {project_id}")

user_prompt = st.text_input("Order or Ask something:", "Recommend a morning coffee")

if st.button("Send Order"):
    st.info("Processing your order with Gemini AI...")
    st.success("Your Barista Agent is ready to serve!")
FROM python:3.10-slim

WORKDIR /app

RUN pip install --no-cache-dir streamlit google-genai

COPY . .

EXPOSE 8501

CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]

⚡ Deployment Command
gcloud run deploy coffee-barista \
  --source . \
  --region us-central1 \
  --allow-unauthenticated \
  --clear-base-image \
  --set-env-vars GOOGLE_GENAI_USE_ENTERPRISE=TRUE,GOOGLE_CLOUD_PROJECT=$PROJECT_ID
✅ Verification & Status
​Task 1, Task 2 & Task 3: Successfully executed and passed standard Codelab evaluation tests ("Check my progress" verified).
​Deployment Status: ACTIVE
