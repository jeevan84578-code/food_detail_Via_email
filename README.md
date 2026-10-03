# MacroSnap

MacroSnap is a Streamlit app that helps users estimate calories and macros from meal photos or text descriptions. It lets people chat about food, track meals in a short conversation history, and email a daily nutrition summary.

## Features

- Upload a meal photo or describe a meal in chat
- Estimate calories and macro breakdowns using Google Gemini
- Keep a short conversation history for meal tracking
- Send a summarized nutrition update by email
- Simple onboarding flow for name and email

## Tech Stack

- Python
- Streamlit
- Google GenAI (Gemini)
- Gmail SMTP

## Project Structure

- `app.py` — main Streamlit app
- `prompts.py` — system and summary prompts
- `requirements.txt` — project dependencies

## Prerequisites

Before running the app, make sure you have:

- Python 3.10+
- A Google Gemini API key
- A Gmail account with an app password for SMTP

## Setup

1. Clone the repository and open the project folder.
2. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.streamlit/secrets.toml` file in the project root with your credentials:

   ```toml
   GEMINI_API_KEY = "your_gemini_api_key"
   GMAIL_ADDRESS = "your_email@gmail.com"
   GMAIL_APP_PASSWORD = "your_gmail_app_password"
   ```

   For Gmail, generate an app password in your Google account settings and use that value in `GMAIL_APP_PASSWORD`.

## Run the app

```bash
streamlit run app.py
```

Then open the local URL shown in the terminal, typically:

```text
http://localhost:8501
```

## How it works

- On first launch, the user enters their name and email.
- The app creates a Gemini chat session using a nutrition-focused system prompt.
- The user can either send text or upload a meal image.
- Gemini estimates the meal's calories and macros.
- The user can send the current chat summary to their email using Gmail SMTP.

## Notes

- This project expects secrets to be stored in `.streamlit/secrets.toml` and will not run without them.
- The app uses a prompt-based estimation workflow, so results are approximate and intended for casual tracking.
- The app currently uses Gmail email sending rather than SMS or WhatsApp messaging.
