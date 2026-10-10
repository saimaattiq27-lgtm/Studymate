# StudyMate AI

A beginner-friendly Streamlit app that lets you upload study materials and ask questions about them using the Groq API.

## Features

- PDF, DOCX, PPTX, XLSX and TXT text extraction
- PNG, JPG and JPEG image question-answering with a Groq vision model
- Summaries, topic explanations, vocabulary definitions, and study questions
- Simple keyword-based retrieval from document text
- Streamlit Cloud deployment support

## 1. Get a Groq API key

1. Sign in to the Groq Console: https://console.groq.com/
2. Create an API key.
3. Keep it private. Do not put the key directly into `app.py` or commit it to GitHub.

## 2. Run locally

Install Python 3.10 or newer, then open a terminal in this folder.

```bash
python -m venv .venv
```

Activate the environment:

**Windows PowerShell**
```powershell
.venv\Scripts\Activate.ps1
```

**Windows Command Prompt**
```bat
.venv\Scripts\activate.bat
```

Install packages:
```bash
pip install -r requirements.txt
```

Create a folder named `.streamlit`, then inside it create `secrets.toml`:

```toml
GROQ_API_KEY = "paste_your_groq_api_key_here"
GROQ_TEXT_MODEL = "llama-3.3-70b-versatile"
GROQ_VISION_MODEL = "meta-llama/llama-4-scout-17b-16e-instruct"
```

Run the app:
```bash
streamlit run app.py
```

If a model name is unavailable in your Groq account, check the currently available models in the Groq Console and update the model setting in the app sidebar or `secrets.toml`.

## 3. Push to GitHub

1. Create a new empty repository on GitHub, for example `studymate-ai`.
2. Put `app.py`, `requirements.txt`, `README.md`, and `.gitignore` in the project folder.
3. Make sure `.streamlit/secrets.toml` is **not** uploaded.
4. In the VS Code terminal, run:

```bash
git init
git add app.py requirements.txt README.md .gitignore
git commit -m "Create StudyMate AI app"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/studymate-ai.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username. If Git asks you to sign in, follow the sign-in prompt.

## 4. Deploy on Streamlit Community Cloud

1. Open https://share.streamlit.io/ and sign in with GitHub.
2. Choose **Create app** and select your `studymate-ai` repository and `main` branch.
3. Set the main file path to `app.py`.
4. Before or during deployment, open the app's **Settings / Secrets** area.
5. Add your secrets in TOML format:

```toml
GROQ_API_KEY = "paste_your_groq_api_key_here"
GROQ_TEXT_MODEL = "llama-3.3-70b-versatile"
GROQ_VISION_MODEL = "meta-llama/llama-4-scout-17b-16e-instruct"
```

6. Save the secrets and deploy/reboot the app.

## Important limitations in this starter version

- Scanned PDFs that contain only page images may not yield text. Upload screenshots/page images instead, or add OCR in a later version.
- For image questions, the app sends up to four uploaded images to the vision model.
- The first version uses simple keyword matching to choose text sections. Large syllabi may need better retrieval (embeddings/vector search) in a future version.
- The app processes documents during the current session; it does not permanently store a document library.
- Groq model availability and rate limits can change. Check the Groq Console if a model name stops working.
- Do not upload confidential documents unless you understand the data handling policies of the services you use.
