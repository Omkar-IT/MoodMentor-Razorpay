# MoodMentor 🧠 — AI-Powered Employee Wellness Platform
**Razorpay AI Buildathon Submission**

## Project Objective
The objective of this project is to integrate emotion detection, sentiment scoring, and journal management with database persistence into the Employee Wellness Management platform. This allows the system to analyze daily journal entries, predict dominant emotions, and compute VADER sentiment scores to track employee well-being.

## Model Used
* **Emotion Detection:** `bhadresh-savani/bert-base-go-emotion` (Transformer-based BERT model)
* **Sentiment Analysis:** VADER (Valence Aware Dictionary and sEntiment Reasoner)
* **Text Preprocessing:** `spaCy`, `ftfy`, `langdetect`, `stopwordsiso`, and `deep-translator`.
* **Conversational AI:** `Qwen/Qwen2.5-0.5B-Instruct` for empathetic workplace wellness support.

## Architecture & Pipeline
1. **Frontend & Backend Separation:** Streamlit handles the user interface for employee self-service, management reports, and face recognition, while FastAPI handles secure routing and NLP execution.
2. **Emotion Detection Pipeline:** User journal entries or uploaded files pass through text normalization, language detection, emoji removal, translation to English, stopword removal, and lemmatization before being classified by the BERT Emotion pipeline into 6 core app labels.
3. **Sentiment Analysis:** VADER computes polarity scores, generating positive, negative, neutral, and compound scores stored in PostgreSQL.

## Confidence Score Calculation
The confidence score is derived directly from the Hugging Face `pipeline` output, returning probability scores for all mapped labels where the score corresponding to the dominant predicted emotion is extracted and stored as a percentage.

## Database Schema (PostgreSQL)
The persistence layer utilizes structured tables including `users`, `otp_codes`, `daily_wellness`, and `mood_logs`:
* `id` (SERIAL PRIMARY KEY)
* `user_id` (INTEGER FK to users table)
* `mood_date` (DATE)
* `sentiment` (VARCHAR) - Derived from VADER
* `emotion` (VARCHAR) - Derived from BERT
* `compound_score` (REAL)
* `confidence` (REAL)
* `journal_text` (TEXT)
* `source` (VARCHAR) - e.g., 'nlp' or 'manual'

## API Endpoints (FastAPI)
* `POST /analyze-text`: Accepts raw text from the Journal, runs the full NLP pipeline, and returns emotion and sentiment JSON data.
* `POST /analyze`: Accepts `.csv` or `.txt` file uploads, extracts text, runs the NLP pipeline, and returns analysis.
* `POST /chat`: Support chatbot endpoint utilizing Qwen2.5 to provide wellness responses with safety guardrails.

## Sample Input & Output
**Input:** "I had a highly productive day today and felt great!"
**Output:** 
- Final Sentiment: Positive 😊 (Compound: 0.82)
- Final Emotion: Happy 😊 (Confidence: 96%)
- Emotion Distribution: Happy (0.96), Neutral (0.02), etc.

## Running Locally
1. Install the requirements:
   ```bash
   pip install -r requirements.txt
   python -m spacy download xx_sent_ud_sm
   
