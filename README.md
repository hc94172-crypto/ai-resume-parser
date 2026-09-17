# AI-Powered Resume Parser 📄✨

An intelligent resume parser that automatically extracts structured information from resumes (PDF, DOCX, DOC) using AI. Perfect for recruiters, HR teams, and job seekers!

---

## Video Demonstration

[Demo # AI Resume Parser 📄✨

An AI-powered resume parser that extracts structured information — name, contact details, skills, experience, education, certifications, and projects — from PDF and DOCX resumes, and returns it as clean JSON.

Built with **Streamlit** for the UI and **Groq's LLaMA/GPT-OSS models** for fast, free-tier-friendly parsing.

---

## Features

- 📤 Upload resumes in **PDF** or **DOCX** format
- 🤖 AI-powered structured extraction (name, email, phone, skills, experience, education, certifications, projects, languages)
- ⚡ Powered by **Groq's `openai/gpt-oss-20b`** — fast inference, free tier available
- 📥 Export parsed results as **JSON** or **CSV**
- 🛡️ Fallback regex-based extraction for skills, name, and email if the AI response is incomplete
- 🧹 Automatic cleanup of malformed JSON responses

---

## Project Structure

```
resume-parser/
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
git clone https://github.com/YOUR_USERNAME/resume-parser-ai.git
cd resume-parser-ai
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

This project uses [Groq](https://console.groq.com/keys), which offers a **free tier** and is OpenAI-API-compatible.

Create a `.env` file in the project root:

```
OPENAI_API_KEY=your_groq_api_key_here
```

> Note: the variable is still named `OPENAI_API_KEY` for compatibility with the OpenAI Python SDK, which Groq's API is built to work with. Get a free key at https://console.groq.com/keys.

### 4. Run the app

```bash
streamlit run app.py
```

Then open the local URL Streamlit prints (usually `http://localhost:8501`) and upload a resume.

---

## How It Works

1. User uploads a PDF or DOCX resume
2. `file_reader.py` extracts raw text from the file
3. `chatgpt_parser.py` sends the text to Groq's LLM with a structured prompt
4. The model returns JSON matching a defined resume schema
5. Results are validated, cleaned, and displayed in the UI — with an option to download as JSON or CSV

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

To switch models (e.g. to a larger Groq model for better accuracy), update `MODEL_NAME` in `resume_parser/config.py`. See [Groq's model list](https://console.groq.com/docs/models) for current options.

---

## Tech Stack

- [Streamlit](https://streamlit.io) — web UI
- [Groq API](https://groq.com) — LLM inference (OpenAI-compatible)
- PyPDF2 / Mammoth — file text extraction

---

## License

MIT — feel free to use, modify, and build on this project.

---

## Acknowledgements

Initially inspired by [DipankarDandapat/ResumeParser](https://github.com/DipankarDandapat/ResumeParser), rebuilt with a different LLM backend, export features, and cleanup. File]



https://github.com/user-attachments/assets/c651d2a5-d08e-4fe5-b727-0a9728d3ca02


[Demo DOCX File]

https://github.com/user-attachments/assets/e5dc5827-565d-4daa-803d-06dffae42ee0




---


## Features 🚀

* Extracts **name, email, phone, skills, experience, education** and more
* Supports **PDF, DOCX, and DOC** formats
* Clean **Streamlit web interface**
* Powered by **OpenAI GPT-4/3.5** for accurate parsing
* Handles complex resume layouts with **Mammoth & PyPDF2**

## Project Structure 🗂️

```
resume-parser/
├── resume_parser/
│   ├── __init__.py
│   ├── file_reader.py      # Handles file parsing
│   ├── chatgpt_parser.py   # AI text extraction
│   ├── utils.py            # Text cleaning
│   └── config.py           # API configuration
│ 
├── app.py                  # Streamlit UI
├── requirements.txt        # Dependencies
├── .env                    # Environment template
└── README.md
```

## Installation ⚙️

1. Clone the repository:
```bash
git clone https://github.com/DipankarDandapat/ResumeParser.git
cd resume-parser
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up your OpenAI API key:
```bash
echo "OPENAI_API_KEY=your_api_key_here" > .env
```

## Usage 🖥️

Run the Streamlit app:
```bash
streamlit run app.py
```

Then upload your resume file (PDF/DOCX/DOC) through the web interface.

## How It Works 🔍

1. Upload a resume file
2. The system extracts raw text using:
   * **Mammoth** for DOCX
   * **PyPDF2** for PDF
   * **Textract** for DOC
3. OpenAI GPT processes the text and returns structured JSON
4. Results are displayed in a clean UI

## Example Output 📋

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

## Customization 🛠️

To modify what fields are extracted, edit the prompt in `chatgpt_parser.py`:

```python
prompt = f"""
Extract resume details in JSON format:
{{
    "name": "Full Name",
    "email": "email@example.com",
    "skills": ["Python", "SQL"],
    "experience": [{{"company": "ABC Corp", "position": "SWE"}}]
}}
Resume Text: {text}
"""
```



