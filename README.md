# 🩺 Health Care Chatbot

A lightweight, health-focused AI chatbot built with **Streamlit** and the **Groq API**. It answers general health, symptom, and wellness questions in simple language, stays strictly on topic, and always encourages users to seek professional medical care when needed.

> ⚠️ **Disclaimer:** This chatbot provides general health information for educational purposes only. It is **not** a substitute for professional medical advice, diagnosis, or treatment. In an emergency, contact your local emergency services immediately.

---

## 📖 Context & Purpose

Access to quick, understandable health information can be difficult, and general-purpose chatbots often drift off-topic or give overconfident medical claims. This project demonstrates a **domain-restricted health assistant** that:

- Provides easy-to-understand information on health, symptoms, and wellness
- Refuses unrelated topics (sports, politics, movies, coding, general knowledge)
- Avoids acting like a doctor: it does not diagnose conditions or prescribe medicines or dosages
- Flags possible emergencies and advises urgent medical care
- Includes a short disclaimer alongside medical guidance

It is a good starting point for learning how to build **guardrailed, single-domain LLM applications** using system prompts.

---

## ✨ Features

- **Health-only scope:** off-topic questions receive a polite refusal
- **Safety-first responses:** no diagnoses, no prescriptions or dosages, emergency escalation advice
- **Prompt-injection resistance:** the system prompt instructs the model not to follow requests to ignore its rules
- **Conversation memory:** chat history is kept for the duration of the session
- **Clear Chat button:** reset the conversation at any time
- **Friendly error handling:** missing API key and API errors are surfaced clearly in the UI
- **Fast inference:** powered by Groq's low-latency API

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3 |
| UI Framework | [Streamlit](https://streamlit.io/) |
| LLM Provider | [Groq](https://groq.com/) |
| Model | `openai/gpt-oss-120b` |
| Config | `python-dotenv` |

---

## 📁 Project Structure

```
Health-care-chatbot/
├── app.py            # Main Streamlit application
├── .env              # API key (not committed to Git)
├── requirements.txt  # Python dependencies
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9 or higher
- A free [Groq API key](https://console.groq.com/keys)

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Create and activate a virtual environment

```bash
python -m venv myenv

# Windows
myenv\Scripts\activate

# macOS / Linux
source myenv/bin/activate
```

### 3. Install dependencies

```bash
pip install streamlit groq python-dotenv
```

Or, if you have a `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 4. Configure your API key

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

> 🔒 Never commit your `.env` file or share your API key publicly.

### 5. Run the app

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`.

---

## 💬 Usage

1. Type a health-related question in the chat box, for example:
   - *"What are common causes of headaches?"*
   - *"How can I improve my sleep?"*
   - *"What should I do for a mild sore throat?"*
2. Read the response, which includes general guidance and a short disclaimer.
3. Click **Clear Chat** to start a new conversation.

**Off-topic example:**

> **User:** Who won the cricket match yesterday?
> **Bot:** Sorry, I can only answer health-related questions. Please ask me something related to health, symptoms, wellness, or medical information.

---

## ⚙️ How It Works

1. `app.py` loads the `GROQ_API_KEY` from `.env` and initializes the Groq client.
2. A **system prompt** defines the assistant's role, scope, and safety rules.
3. User messages are stored in `st.session_state` and sent, together with the system prompt, to the Groq chat completions API (`temperature=0.3`, `max_tokens=700`).
4. The model's reply is displayed in the chat and appended to the session history.

---

## 🔧 Configuration

You can tweak these values in `app.py`:

| Setting | Default | Description |
|---------|---------|-------------|
| `model` | `openai/gpt-oss-120b` | Groq-hosted model used for responses |
| `temperature` | `0.3` | Lower values give more consistent, factual answers |
| `max_tokens` | `700` | Maximum length of each response |
| `SYSTEM_PROMPT` | Health-only rules | Controls scope and safety behavior |

---

## ⚠️ Limitations

- Responses are AI-generated and may contain errors or omissions
- No medical records, personalization, or clinical validation
- Chat history is temporary and is lost when the session ends or the page is refreshed
- Topic restriction relies on prompt instructions, which can't guarantee perfect enforcement

---

## 🗺️ Possible Improvements

- Add streaming responses for a smoother chat experience
- Persist chat history (database or file storage)
- Add multilingual support
- Integrate trusted medical sources (retrieval-augmented generation)
- Add an emergency-keyword detector with local helpline information
- Deploy on Streamlit Community Cloud

---

## 🤝 Contributing

Contributions are welcome! Feel free to fork the repo, create a feature branch, and open a pull request.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE). *(Add a LICENSE file if you haven't already.)*

---

## 🙏 Acknowledgements

- [Streamlit](https://streamlit.io/) for the UI framework
- [Groq](https://groq.com/) for fast LLM inference



