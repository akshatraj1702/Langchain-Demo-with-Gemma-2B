LangChain Demo with Gemma 2B

A minimal GenAI application built while learning the fundamentals of LangChain, LCEL, Ollama, and LangSmith.

The project uses the locally hosted Gemma 2B model through Ollama. A user's question is inserted into a structured chat prompt, passed to the model, and converted into a plain-text response.

How It Works

User Question
      ↓
ChatPromptTemplate
      ↓
Gemma 2B via Ollama
      ↓
StrOutputParser
      ↓
Final Response

The LangChain workflow is built using LCEL (LangChain Expression Language):

chain = prompt | llm | output_parser

Each step passes its output to the next step.

What's Inside

ChatPromptTemplate — creates a structured prompt containing a system message and the user's question.

OllamaLLM — connects LangChain to the locally running Gemma 2B model.

StrOutputParser — converts the model output into a plain Python string.

LCEL — connects the prompt, model, and parser into a single chain.

LangSmith tracing — optionally tracks LangChain runs for debugging and visibility.

Streamlit — provides a simple web interface for interacting with the model.

Project Structure

.
├── app.py
├── langchain_gemma_notebook.ipynb
├── requirements.txt
├── .env.example
└── README.md

Requirements

Before running the project, make sure you have:

Python 3.10+

Ollama

Gemma 2B model

Python dependencies listed in requirements.txt

Setup

1. Install the Python dependencies

pip install -r requirements.txt

2. Install and pull Gemma 2B with Ollama

Make sure Ollama is installed and running, then:

ollama pull gemma:2b

You can verify that the model is available with:

ollama list

3. Optional: Configure LangSmith

LangSmith is optional. It is used to trace and monitor LangChain runs.

Create a .env file based on .env.example:

LANGCHAIN_API_KEY=your_api_key
LANGCHAIN_PROJECT=langchain-notes

If you do not want LangSmith tracing, you can run the application without these variables.

Running the Application

If using the Streamlit application:

streamlit run app.py

Streamlit will provide a local URL, usually:

http://localhost:8501

Open that URL in your browser to interact with the application.

Running the Notebook

The project also includes:

langchain_gemma_notebook.ipynb

Open it in VS Code or Jupyter and run the cells sequentially.

The notebook demonstrates the same core workflow without the Streamlit interface.

Example

Input

What is LangChain?

Workflow

"What is LangChain?"
        ↓
Prompt Template
        ↓
Gemma 2B
        ↓
String Output Parser
        ↓
Answer

LangSmith Tracking

When a LANGCHAIN_API_KEY is available, LangSmith tracing can be enabled.

The application sets:

os.environ["LANGCHAIN_TRACING_V2"] = "true"

and specifies a project using:

os.environ["LANGCHAIN_PROJECT"] = "langchain-notes"

This allows the LangChain execution to be inspected and debugged through LangSmith.

LangSmith is not required for the model itself to generate responses.

Key Concepts Learned

This project demonstrates the basic LangChain workflow:

Prompt Template — defines how the model should receive the user's input.

LLM — Gemma 2B generates the response.

Output Parser — converts the model response into usable text.

Chain — connects these components together using LCEL.

Ollama — allows the language model to run locally instead of calling a hosted model API.

LangSmith — provides optional tracing and observability.

Notes
