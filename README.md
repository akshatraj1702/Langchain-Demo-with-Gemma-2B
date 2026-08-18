# Langchain-Demo-with-Gemma-2B

Minimal Streamlit app: a prompt template piped into a local Gemma 2B model via Ollama.
Built while learning LangChain fundamentals.

## What's inside
- `ChatPromptTemplate` — system + user message with a `{question}` placeholder
- `OllamaLLM` — local model, no API keys or cost
- `StrOutputParser` — response object to plain string
- LCEL chaining with `|` — prompt | model | parser
- Optional LangSmith tracing for run visibility

## Setup
```bash
ollama pull gemma:2b
pip install -r requirements.txt
cp .env.example .env   # optional, only for LangSmith
streamlit run app.py
```
