# 📄 ATS Resume Checker

A Streamlit app that scores a resume for ATS (Applicant Tracking System) compatibility
and suggests concrete improvements, powered by Google's Gemini Flash model.

## Features
- Upload a resume as **PDF, DOCX or TXT**
- Optional **job description** for keyword matching
- Overall ATS score (0-100) plus breakdown: formatting, keywords, content, structure, readability
- Strengths, issues found, prioritized improvements, missing keywords, example bullet rewrites
- Download the report as JSON

## Run locally
1. Install Python 3.9+ and get a free Gemini API key from https://aistudio.google.com
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Provide your key (pick one):
   - Environment variable: `export GEMINI_API_KEY="your_key"` (Windows: `set GEMINI_API_KEY=your_key`)
   - Or create `.streamlit/secrets.toml` containing `GEMINI_API_KEY = "your_key"`
   - Or paste it into the app sidebar
4. Start the app:
   ```bash
   streamlit run app.py
   ```

## Deploy on Streamlit Community Cloud
1. Push this repo to GitHub (never commit your API key).
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app**, choose this repo, branch `main`, main file `app.py`.
4. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your_key"
   ```
5. Click **Deploy**.

## Configuration
The model name is editable in the sidebar (default `gemini-2.5-flash`). If Google retires
that name, enter a current Gemini Flash model name from https://ai.google.dev/gemini-api/docs/models

## Notes
- Resumes are sent to the Gemini API for analysis and are not stored by this app.
- The score is an AI estimate, not the output of a real ATS. Use it as guidance.
- Scanned/image-only PDFs can't be read; use a text-based PDF or DOCX.

## Project structure
```
app.py             # Streamlit app
requirements.txt   # Dependencies
README.md          # This file
```
