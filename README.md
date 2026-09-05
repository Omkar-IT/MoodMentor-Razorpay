# <div align="center">🧠 MoodMentor — AI-Powered Employee Wellness & Sentiment Platform</div>
<p align="center">
  <img src="https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Razorpay-AI%20Buildathon-blue?style=for-the-badge" alt="Buildathon">
  <img src="https://img.shields.io/badge/Python-3.10%2B-purple?style=for-the-badge" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge" alt="FastAPI">
  <img src="https://img.shields.io/badge/Streamlit-Frontend-FF4B4B?style=for-the-badge" alt="Streamlit">
</p>

<p align="center">
  <b>Transforming organizational well-being through real-time multilingual NLP, precision sentiment tracking, and compassionate AI support.</b>
</p>

---

## 🌟 Executive Summary & Working Mechanism
Traditional annual engagement surveys are broken: they arrive months too late, suffer from low response rates, and miss acute emotional friction. **MoodMentor** bridges this gap by capturing real-time employee journals, check-ins, and multilingual text inputs, processing them instantly through a powerful dual-layer intelligence pipeline.

### **The Architecture Lifecycle ⚙️**
1. **📥 Data Ingestion:** Employees log check-ins via interactive emoji grids, free-form journals, or bulk dataset uploads (`.csv` / `.txt`).
2. **🧹 Multilingual NLP Engine:** Raw input passes through text normalization, language detection, emoji preservation, translation, stopword filtering, and lemmatization.
3. **🤖 Dual-Model Intelligence:** 
   - **VADER:** Computes fast, deterministic polarity and compound sentiment scores.
   - **BERT (`bert-base-go-emotion`)** Classifies deep emotional drivers down to core workplace sentiment categories.
4. **💾 Persistence & Reporting:** Structured scores, confidence metrics, and compound logs are committed to **PostgreSQL**, driving automated weekly PDF summaries and managerial visibility panels.

---

## 🛠️ Technology Stack & AI Models

| Layer | Technology / Model | Core Purpose |
| :--- | :--- | :--- |
| **Frontend UI** | 📊 **Streamlit** | Responsive, dynamic user experience for self-service & analytics. |
| **Backend API** | ⚡ **FastAPI** | Asynchronous REST routing, middleware orchestration, and secure auth. |
| **Database** | 🐘 **PostgreSQL (Neon)** | Scalable relational storage for user profiles, roles, and mood history. |
| **Emotion AI** | 🤖 `bhadresh-savani/bert-base-go-emotion` | Transformer model mapping granular emotions to core classes. |
| **Sentiment AI** | 📈 **VADER Sentiment** | Lexicon-rule engine calculating polarity and compound intensity. |
| **Conversational AI** | 💬 `Qwen/Qwen2.5-0.5B-Instruct` | Empathetic workplace chatbot with strict safety guardrails. |
| **Text Processing** | 🔤 `spaCy`, `stopwordsiso`, `deep-translator` | Multilingual tokenization, cleanup, and translation frameworks. |

---

## 🔌 Core API Architecture & Endpoints

* **`POST /analyze-text`**
  * *Payload:* Raw text input from the journaling module.
  * *Response:* JSON containing language codes, text stats, VADER polarity breakdowns, and BERT emotion vectors.
* **`POST /analyze`**
  * *Payload:* Multi-row `.csv` or `.txt` batch upload.
  * *Response:* Aggregated organization wellness scores and bulk distribution statistics.
* **`POST /chat`**
  * *Payload:* User query string and recent chat context window.
  * *Response:* Context-aware, supportive wellness response generated via Qwen2.5.

---

## 📊 Live Sample Inputs & Outputs

### **Scenario A: Positive Engagement Entry**
* **📥 Input Text:** 
  > *"I had an incredible planning session today and successfully deployed our new feature stack!"*
* **📤 Model Output:**
  * **Final Sentiment:** Positive 😊 *(Compound Score: `+0.85`)*
  * **Dominant Emotion:** Happy 😃 *(Confidence Level: `98%`)*
  * **Distribution Vector:** Happy (`0.98`), Neutral (`0.02`)

### **Scenario B: High-Stress Workload Entry**
* **📥 Input Text:** 
  > *"The deadlines are piling up simultaneously and I am completely overwhelmed trying to balance everything."*
* **📤 Model Output:**
  * **Final Sentiment:** Negative 📉 *(Compound Score: `-0.62`)*
  * **Dominant Emotion:** Stress 🤯 *(Confidence Level: `91%`)*
  * **Distribution Vector:** Stress (`0.91`), Sad (`0.07`), Neutral (`0.02`)

---

## 🚀 Local Installation & Quickstart

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/Omkar-IT/MoodMentor-Razorpay.git](https://github.com/Omkar-IT/MoodMentor-Razorpay.git)
   cd MoodMentor-Razorpay
