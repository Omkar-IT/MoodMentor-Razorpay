<div align="center">

# 🧠 <b><u>MoodMentor Enterprise Edition</u></b> — <i>Next-Gen AI-Driven Employee Wellness, Sentiment Intelligence & Crisis Prevention Ecosystem</i>
  
<p style="font-size: 1.35rem;">
  <b><i>Engineered specifically for the Razorpay AI Buildathon & Engineering Internship Evaluation — Demonstrating Production-Grade Architecture, Advanced Transformer Pipelines, & Real-World Impact.</i></b>
</p>

<p>
  <img src="https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge&logo=rocket&logoColor=white" alt="Status">
  <img src="https://img.shields.io/badge/Razorpay-AI%20Buildathon-blue?style=for-the-badge&logo=razorpay&logoColor=white" alt="Buildathon">
  <img src="https://img.shields.io/badge/Python-3.10%2B-purple?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-Async%20Core-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Streamlit-Reactive%20UI-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit">
  <img src="https://img.shields.io/badge/PostgreSQL-Neon%20Cloud-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/HuggingFace-Transformers-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" alt="HuggingFace">
</p>

</div>

---

## 🎯 <u><b>Why MoodMentor Stands Out for Razorpay</b></u>
Modern high-growth fintech environments like Razorpay demand engineering excellence that goes beyond basic CRUD applications. **MoodMentor** solves an enterprise-scale organizational challenge: preventing burnout, tracking retention risk, and ensuring psychological safety at scale without compromising data privacy or server performance. 

This repository showcases:
* **<u>Microservices-Inspired Decoupling</u>:** Clean separation of concerns between an asynchronous, high-throughput **FastAPI** backend and a reactive, session-managed **Streamlit** frontend.
* **<u>Optimized Resource Management</u>:** Strategic implementation of singleton lazy-loading patterns for heavy deep learning weights (`torch`, `transformers`, `spaCy`), avoiding memory spikes on modest cloud instances.
* **<u>Safety-First Guardrails</u>:** Hardcoded, deterministic safety filters running *upstream* of generative models to ensure zero-tolerance for safety failures in crisis scenarios.
* **<u>Production-Grade Persistence</u>:** Robust relational schema design using PostgreSQL with connection pooling, transactional context managers, and strict data type enforcement.


┌────────────────────────────────────────────────────────────────────────┐
│                      STREAMLIT REACTIVE FRONTEND                       │
│    (Employee Self-Service Portal • HR Analytics • Face Verification)   │
└───────────────────────────────────┬────────────────────────────────────┘
│ (HTTP/REST • Bearer JWT Auth)
▼
┌────────────────────────────────────────────────────────────────────────┐
│                         FASTAPI ASYNC BACKEND                          │
│  ┌─────────────────────────┐                 ┌──────────────────────┐  │
│  │   Multilingual NLP      │                 │  Qwen2.5 Generative  │  │
│  │    Pipeline (Pipeline)  │                 │    Support Chatbot   │  │
│  └───────────┬─────────────┘                 └──────────┬───────────┘  │
└──────────────┼──────────────────────────────────────────┼──────────────┘
│                                          │
▼                                          ▼
┌─────────────────────────────┐           ┌──────────────────────────────┐
│   BERT (GoEmotions)         │           │   VADER Sentiment Engine     │
│   & spaCy Lemmatization     │           │   (Compound Polarity Scores) │
└──────────────┬──────────────┘           └──────────────┬───────────────┘
│                                         │
└───────────────────┬─────────────────────┘
│
▼
┌────────────────────────────────────────────────────────────────────────┐
│                      POSTGRESQL CLOUD DATABASE                         │
│     (Users • Encrypted Auth • Daily Wellness • Immutable Mood Logs)    │
└────────────────────────────────────────────────────────────────────────┘

## 🧠 <u><b>Deep-Dive: The Multilingual NLP & AI Pipeline</b></u>

MoodMentor does not rely on naive keyword matching. Every piece of employee text goes through a rigorous **7-stage transformation pipeline** inside `nlp_pipeline.py`:

1. **Text Normalization (`ftfy`):** Fixes broken unicode, mojibake, and malformed character encodings automatically.
2. **Language Identification (`langdetect`):** Detects the ISO 639-1 language code across 50+ supported global languages.
3. **Noise Extraction & Preservation:** Isolates emojis for sentiment valence while stripping URLs, HTML tags, and spam tokens.
4. **Dynamic Multilingual Stopword Removal (`stopwordsiso`):** Automatically maps the detected language code to native stopword dictionaries without bloated hardcoded lists.
5. **Neural Translation (`deep-translator`):** Seamlessly bridges regional and international feedback into a unified semantic space in English.
6. **Lemmatization (`spaCy` `xx_sent_ud_sm`):** Reduces words to their base root lemmas for cleaner syntactic analysis.
7. **Dual-Model Scoring:** 
   - **VADER:** Computes fast, deterministic polarity ($pos, neu, neg, compound$).
   - **Fine-Tuned BERT (`bhadresh-savani/bert-base-go-emotion`):** Maps granular psychological states across 28 GoEmotions categories, aggregating them mathematically into **6 core enterprise wellness classes** (`Happy`, `Sad`, `Stress`, `Angry`, `Fear`, `Neutral`) with precise percentage confidence scores.

---

## 📊 <u><b>Comprehensive API Specification</b></u>

| Endpoint | Method | Authentication | Description | Payload / Response Schema |
| :--- | :---: | :---: | :--- | :--- |
| **`/health`** | `GET` | Public | System liveness probe. | Returns `{"status": "ok"}`. |
| **`/analyze-text`** | `POST` | Bearer JWT | Analyzes raw text string from Journal UI. | **In:** `{"text": "string"}` <br>**Out:** Sentiment scores, BERT vector, confidence %. |
| **`/analyze`** | `POST` | Bearer JWT | Bulk batch processing for uploaded CSV/TXT files. | **In:** Multipart file <br>**Out:** Aggregate distribution metrics. |
| **`/chat`** | `POST` | Bearer JWT | Conversational AI support session handler. | **In:** `{"message": "string", "history": [...]}` <br>**Out:** `{"reply": "string", "flagged": bool}` |

---

## 🛡️ <u><b>Safety Engineering & Crisis Interception</b></u>

In mental health and employee wellness applications, hallucinations or inappropriate model behavior are catastrophic failure points. 

* **Upstream Guardrails:** Before any prompt hits the `Qwen/Qwen2.5-0.5B-Instruct` generative weights, the input string passes through `_contains_crisis_language()`.
* **Immediate Fallback:** If self-harm, suicidal ideation, or acute crisis keywords are detected, the LLM execution thread is bypassed entirely.
* **Empathetic Resource Routing:** The system instantly returns a verified, compassionate crisis intervention message containing real-world helpline numbers (such as AASRA in India) alongside standard EAP instructions.

---

## 📈 <u><b>Automated PDF Reporting Engine</b></u>

Using `reportlab`, MoodMentor generates executive-ready, downloadable weekly wellness dossiers (`weekly_report.py`). The engine:
* Computes weighted scoring matrices across daily moods, journal consistency, sleep hours, stress levels, and workload distributions.
* Automatically handles missing data by normalizing active weights rather than penalizing employees with unfair zero-scores.
* Renders matplotlib analytics charts directly into publication-quality vector and raster graphics embedded inside the final PDF document.

---

## 💻 <u><b>Complete Installation & Deployment Guide</b></u>

### **Prerequisites**
* Python 3.10 or higher
* PostgreSQL instance (e.g., Neon, Supabase, or local)
* Git installed on your system

### **Step-by-Step Local Setup**

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/Omkar-IT/MoodMentor-Razorpay.git](https://github.com/Omkar-IT/MoodMentor-Razorpay.git)
   cd MoodMentor-Razorpay
---

## 🏗️ <u><b>Enterprise Architecture & System Design</b></u>
