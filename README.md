<div align="center">

# 🧠 <b><u>MoodMentor</u></b> — <i>AI-Powered Employee Wellness & Sentiment Platform</i>
  
<p style="font-size: 1.25rem;">
  <b><i>Transforming organizational well-being through real-time multilingual NLP, precision sentiment tracking, and compassionate AI support.</i></b>
</p>

<p>
  <img src="https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge&logo=rocket&logoColor=white" alt="Status">
  <img src="https://img.shields.io/badge/Razorpay-AI%20Buildathon-blue?style=for-the-badge&logo=razorpay&logoColor=white" alt="Buildathon">
  <img src="https://img.shields.io/badge/Python-3.10%2B-purple?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Streamlit-Frontend-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit">
  <img src="https://img.shields.io/badge/PostgreSQL-Database-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL">
</p>

</div>

---

## 🌟 <u><b>Executive Summary & Core Mission</b></u>
Traditional annual engagement surveys are completely broken: they arrive months too late, suffer from abysmal response rates, and completely miss acute emotional friction in the workplace. **MoodMentor** bridges this critical gap by capturing real-time employee journals, check-ins, and multilingual text inputs, processing them instantly through a state-of-the-art dual-layer intelligence pipeline.

### **The Architecture Lifecycle ⚙️**
1. **📥 <u>Data Ingestion</u>:** Employees log check-ins via interactive emoji grids, free-form journals, or bulk dataset uploads (`.csv` / `.txt`).
2. **🧹 <u>Multilingual NLP Engine</u>:** Raw input flows through text normalization, language detection, emoji preservation, translation, stopword filtering, and lemmatization.
3. **🤖 <u>Dual-Model Intelligence</u>:** 
   - **VADER:** Computes fast, deterministic polarity and compound sentiment scores.
   - **BERT (`bert-base-go-emotion`)**: Classifies deep emotional drivers down to core workplace sentiment categories.
4. **💾 <u>Persistence & Reporting</u>:** Structured scores, confidence metrics, and compound logs are committed to **PostgreSQL**, driving automated weekly PDF summaries and managerial visibility panels.

---

## 🛠️ <u><b>Technology Stack & AI Models</b></u>

| Layer | Technology / Model | Core Purpose |
| :--- | :--- | :--- |
| **Frontend UI** | 📊 <b><u>Streamlit</u></b> | Responsive, dynamic user experience for self-service & analytics. |
| **Backend API** | ⚡ <b><u>FastAPI</u></b> | Asynchronous REST routing, middleware orchestration, and secure auth. |
| **Database** | 🐘 <b><u>PostgreSQL (Neon)</u></b> | Scalable relational storage for user profiles, roles, and mood history. |
| **Emotion AI** | 🤖 `bhadresh-savani/bert-base-go-emotion` | Transformer model mapping granular emotions to core classes. |
| **Sentiment AI** | 📈 <b><u>VADER Sentiment</u></b> | Lexicon-rule engine calculating polarity and compound intensity. |
| **Conversational AI** | 💬 `Qwen/Qwen2.5-0.5B-Instruct` | Empathetic workplace chatbot with strict safety guardrails. |
| **Text Processing** | 🔤 `spaCy`, `stopwordsiso`, `deep-translator` | Multilingual tokenization, cleanup, and translation frameworks. |

---

## 🔌 <u><b>Core API Architecture & Endpoints</b></u>

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

## 📊 <u><b>Live Sample Inputs & Outputs</b></u>

### **Scenario A: Positive Engagement Entry**
* **📥 <u>Input Text</u>:** 
  > _"I had an incredible planning session today and successfully deployed our new feature stack!"_
* **📤 <u>Model Output</u>:**
  * **Final Sentiment:** Positive 😊 _(Compound Score: `+0.85`)_
  * **Dominant Emotion:** Happy 😃 _(Confidence Level: `98%`)_
  * **Distribution Vector:** Happy (`0.98`), Neutral (`0.02`)

### **Scenario B: High-Stress Workload Entry**
* **📥 <u>Input Text</u>:** 
  > _"The deadlines are piling up simultaneously and I am completely overwhelmed trying to balance everything."_
* **📤 <u>Model Output</u>:**
  * **Final Sentiment:** Negative 📉 _(Compound Score: `-0.62`)_
  * **Dominant Emotion:** Stress 🤯 _(Confidence Level: `91%`)_
  * **Distribution Vector:** Stress (`0.91`), Sad (`0.07`), Neutral (`0.02`)

---

## 🚀 <u><b>Local Installation & Quickstart</b></u>

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/Omkar-IT/MoodMentor-Razorpay.git](https://github.com/Omkar-IT/MoodMentor-Razorpay.git)
   cd MoodMentor-Razorpay
