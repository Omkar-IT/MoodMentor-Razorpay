# MoodMentor 🧠 — AI-Powered Employee Wellness Platform
**Razorpay AI Buildathon Submission — Track 05 (Open Track)**

## 🌟 Overview
MoodMentor is a full-stack, multilingual employee wellness platform designed to bridge the gap between employee sentiment and HR analytics. Traditional surveys are slow and low-response; MoodMentor captures real-time emotional insights securely while respecting privacy and infrastructure constraints.

## 🛠️ Architecture & Tech Stack
* **Frontend:** Streamlit (Employee portal, interactive mood grids, analytics dashboards, and face recognition)
* **Backend:** FastAPI REST service handling secure routing and JWT authentication
* **Database:** PostgreSQL (Neon) managing users, encrypted passwords, roles, daily wellness logs, and mood history
* **Intelligence Layer:** 
  * **spaCy (`xx_sent_ud_sm`)** for multilingual text preprocessing and normalization
  * **VADER** for deterministic sentiment polarity scores
  * **Fine-tuned BERT (`bert-base-go-emotion`)** for precise 6-class emotion classification
  * **Qwen2.5 (0.5B-Instruct)** for empathetic conversational wellness support with safety guardrails

## 🚀 Key Features
* **Multilingual NLP Pipeline:** Normalizes text, cleans noise/emojis, translates dynamically, and extracts sentiment and emotions.
* **Face Recognition & Emotion Analysis:** Optional deep learning-based facial expression scanning via DeepFace.
* **Automated Weekly PDF Reports:** Aggregates sleep, stress, workload, and sentiment data into downloadable PDF wellness summaries using ReportLab.
* **Safety Guardrails:** Includes built-in crisis keyword detection that intercepts self-harm queries and immediately redirects users to real-world support resources.

## ⚙️ Running Locally
1. Clone the repository and install dependencies:
   ```bash
   pip install -r requirements.txt
   python -m spacy download xx_sent_ud_sm
