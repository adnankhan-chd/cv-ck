CV ATS Checker
A small Streamlit app that uses Google's Gemini Flash model to review pasted CV text and estimate ATS readiness. It can compare a CV against a target job description and suggest practical improvements.
Important: This is an AI-generated estimate, not an official ATS score, a guarantee of parsing behavior, or a hiring prediction. The app sees pasted text, not the original PDF/DOCX layout. Do not use the score as the sole basis for hiring decisions.

Features
- Paste CV text and optionally a target job description
- Estimated overall readiness, keyword-match, and visible-text formatting scores
- Strengths, potential keyword gaps, prioritized improvements, and section feedback
- Download analysis results as JSON
- API key read from environment variables or Streamlit secrets
Requirements
- Python 3.10 or newer
- A Google AI Studio API key with access to Gemini
Run locally
1. Clone/download this project and open a terminal in the project folder.
2. Create and activate a virtual environment (recommended):
   macOS/Linux
   python -m venv .venv
   source .venv/bin/activate
   Windows PowerShell
   python -m venv .venv
   .venv\Scripts\Activate.ps1
3. Install dependencies:
   pip install -r requirements.txt
4. Set your API key. For a quick local run:
   macOS/Linux
   export GEMINI_API_KEY="your_api_key_here"
   Windows PowerShell
   $env:GEMINI_API_KEY="your_api_key_here"
   Or create .streamlit/secrets.toml with:
   GEMINI_API_KEY = "your_api_key_here"
   Do not commit .streamlit/secrets.toml or publish your API key.
5. Start the app:
   streamlit run app.py
Push to GitHub
Create an empty repository on GitHub, then run these commands from the project folder (replace the URL with your repository URL):
git init
git add app.py README.md requirements.txt
git commit -m "Build CV ATS Checker with Streamlit and Gemini"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
If Git asks you to authenticate, use GitHub's supported sign-in or token flow; do not put credentials in the remote URL. If you already initialized a repository, skip git init and check git remote -v before adding a remote.
Deploy on Streamlit Community Cloud
1. Push the three project files to GitHub.
2. Sign in to Streamlit Community Cloud at https://share.streamlit.io/ and connect your GitHub account if prompted.
3. Choose Create app, select your repository, branch (main), and main file path (app.py).
4. Before or after launch, open the app's Settings → Secrets and add:GEMINI_API_KEY = "your_api_key_here"
5. Deploy the app. Streamlit installs packages from requirements.txt. If deployment fails, inspect the app logs and confirm the secret name and API key permissions/quota.
How the score should be interpreted
The model evaluates the content provided and returns a directional estimate. Real ATS products differ, and the original document's columns, tables, fonts, headers/footers, images, and file conversion can affect parsing in ways that pasted text cannot reveal. Tailor the CV honestly to the job; do not add skills or keywords you do not have.
Privacy and production notes
- CVs can contain personal information. Tell users what is sent to the AI provider and obtain appropriate consent before processing.
- This prototype does not save CV text to a database, but application hosting, provider processing, and logs may have their own data handling rules. Review the relevant policies before public launch.
- Add rate limiting, abuse protection, and clear retention/deletion practices before offering this publicly.
- Avoid using the tool to rank candidates automatically or infer protected traits.
Files
- app.py — Streamlit interface and Gemini analysis
- requirements.txt — Python dependencies
- README.md — setup, GitHub, and deployment i
