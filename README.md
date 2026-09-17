# AI Resume Parser 📄✨

An AI-powered resume parser that extracts structured information — name, contact details, skills, experience, education, certifications, and projects — from PDF and DOCX resumes, and returns it as clean, structured JSON.

Built with **Streamlit** for the UI and **Groq's LLaMA/GPT-OSS models** for fast, free-tier-friendly parsing.

---

## Features

- 📤 Upload resumes in **PDF** or **DOCX** format
- 🤖 AI-powered structured extraction — name, email, phone, skills, experience, education, certifications, projects, languages
- ⚡ Powered by **Groq's `openai/gpt-oss-20b`** model for fast, low-cost inference
- 📥 Export parsed results as **JSON** or **CSV**
- 🛡️ Fallback regex-based extraction for skills, name, and email if the AI response is incomplete
- 🧹 Automatic cleanup of malformed JSON responses
- 🎯 Clean, simple Streamlit interface — no setup beyond an API key

---

## Project Structure

```
ai-resume-parser/
├── resume_parser/
│   ├── __init__.py
│   ├── file_reader.py      # Extracts raw text from PDF/DOCX
│   ├── chatgpt_parser.py   # AI-based structured extraction
│   ├── utils.py            # Text cleaning helpers
│   └── config.py           # API key & model configuration
│
├── app.py                  # Streamlit UI
├── requirements.txt        # Python dependencies
├── .env                    # API key (not committed — see below)
└── README.md
```

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/hc94172-crypto/ai-resume-parser.git
cd ai-resume-parser
```

### 2. Create a virtual environment & install dependencies

```bash
python -m venv venv
source venv/Scripts/activate      # Windows Git Bash
# or: venv\Scripts\activate.bat   # Windows CMD
# or: source venv/bin/activate    # macOS/Linux

pip install -r requirements.txt
```

### 3. Set up your API key

This project uses [Groq](https://console.groq.com/keys), which offers a **free tier** and is fully compatible with the OpenAI Python SDK.

Create a `.env` file in the project root:

```
OPENAI_API_KEY=your_groq_api_key_here
```

> The variable is named `OPENAI_API_KEY` for compatibility with the OpenAI SDK that Groq's API works through. Grab a free key at https://console.groq.com/keys.

### 4. Run the app

```bash
streamlit run app.py
```

Open the local URL Streamlit prints (usually `http://localhost:8501`) and upload a resume.

---

## How It Works

1. User uploads a PDF or DOCX resume
2. `file_reader.py` extracts raw text from the file
3. `chatgpt_parser.py` sends the text to an LLM with a structured extraction prompt
4. The model returns JSON matching a defined resume schema
5. Results are validated, cleaned, and displayed in the UI — with options to download as JSON or CSV

---

## Example Output

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+1 (123) 456-7890",
  "skills": ["Python", "Machine Learning", "SQL"],
  "experience": [
    {
      "company": "Tech Corp",
      "position": "Senior Developer",
      "duration": "2020-Present"
    }
  ],
  "education": [
    {
      "institution": "State University",
      "degree": "B.S. Computer Science",
      "year": "2020"
    }
  ]
}
```

---

## Customization

To change what fields are extracted, edit the prompt template in `resume_parser/chatgpt_parser.py` inside `_create_prompt()`.

To switch models, update `MODEL_NAME` in `resume_parser/config.py`. See [Groq's model list](https://console.groq.com/docs/models) for current available options.

---

## Tech Stack

- [Streamlit](https://streamlit.io) — web UI
- [Groq API](https://groq.com) — LLM inference
- PyPDF2 / Mammoth — file text extraction

---

## Live Demo

*(Add your Streamlit Cloud URL here once deployed, e.g. `https://your-app-name.streamlit.app`)*

---

## Author

Built by **Himanshu**

---

## License

Licensed under the MIT License — see [LICENSE](LICENSE) for details.