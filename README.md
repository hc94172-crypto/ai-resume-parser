
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

Initially inspired by [DipankarDandapat/ResumeParser](https://github.com/DipankarDandapat/ResumeParser), rebuilt with a different LLM backend, export features, and cleanup.