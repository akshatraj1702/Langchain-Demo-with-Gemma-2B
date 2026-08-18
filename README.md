# LangChain Demo with Gemma 2B

A simple Generative AI application built while learning the fundamentals of **LangChain**, **LCEL**, **Ollama**, **Gemma 2B**, and **LangSmith**.

The project uses the **Gemma 2B** language model locally through Ollama and connects it to a LangChain pipeline for generating responses to user questions.

---

## 🚀 Overview

The application follows a simple LLM workflow:

```text
User Question
      ↓
ChatPromptTemplate
      ↓
Gemma 2B via Ollama
      ↓
StrOutputParser
      ↓
Final Response
```

The LangChain pipeline is connected using **LCEL (LangChain Expression Language)**:

```python
chain = prompt | llm | output_parser
```

Each component passes its output to the next component.

---

## 🧠 Technologies Used

- **Python**
- **LangChain**
- **Ollama**
- **Gemma 2B**
- **Streamlit**
- **LangSmith**
- **Jupyter Notebook**

---

## 🔑 Key Components

### 1. ChatPromptTemplate

Creates a structured prompt for the LLM.

```python
prompt = ChatPromptTemplate.from_messages(
    [
        ("system", "You are a helpful assistant. Please respond to the question asked"),
        ("user", "Question: {question}"),
    ]
)
```

The `{question}` placeholder is replaced with the user's actual input.

---

### 2. Ollama + Gemma 2B

The project runs Gemma 2B locally using Ollama:

```python
llm = OllamaLLM(model="gemma:2b")
```

This allows the model to run locally rather than relying on a hosted LLM API.

---

### 3. StrOutputParser

The output parser converts the model's response into a simple text string:

```python
output_parser = StrOutputParser()
```

---

### 4. LCEL Chain

The components are connected together using LangChain Expression Language:

```python
chain = prompt | llm | output_parser
```

This means:

```text
Prompt → LLM → Output Parser
```

The output from one component becomes the input to the next.

---

## 📁 Project Structure

```text
.
├── 1-module/
│   ├── 1.ipynb
│   ├── simpleapp.ipynb
│   └── simpleapp1.ipynb
│
├── langchain_gemma_notebook.ipynb
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup

### 1. Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_REPOSITORY_NAME>
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it:

**macOS / Linux**

```bash
source venv/bin/activate
```

**Windows**

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🦙 Setup Ollama

Install Ollama and make sure it is running.

Pull the Gemma 2B model:

```bash
ollama pull gemma:2b
```

Verify that the model is available:

```bash
ollama list
```

You should see `gemma:2b` in the list.

---

## ▶️ Running the Notebook

Open:

```text
langchain_gemma_notebook.ipynb
```

in VS Code or Jupyter Notebook and execute the cells sequentially.

The notebook demonstrates the complete LangChain workflow:

```text
Input
  ↓
Prompt Template
  ↓
Gemma 2B
  ↓
Output Parser
  ↓
Response
```

---

## 🌐 Streamlit Application

The project also demonstrates how the LangChain chain can be connected to a Streamlit interface.

A typical Streamlit workflow is:

```python
input_text = st.text_input("What question do you have in mind?")

if input_text:
    st.write(chain.invoke({"question": input_text}))
```

To run a Streamlit Python application:

```bash
streamlit run app.py
```

> Make sure `app.py` exists in the repository before running this command.

---

## 📊 LangSmith Tracking

LangSmith can optionally be used to monitor and trace LangChain executions.

If a LangSmith API key is available:

```python
if os.getenv("LANGCHAIN_API_KEY"):
    os.environ["LANGCHAIN_TRACING_V2"] = "true"
    os.environ["LANGCHAIN_PROJECT"] = "langchain-notes"
```

LangSmith helps visualize and debug the execution of the LangChain pipeline.

It is **optional** and is not required for Gemma 2B to generate responses.

---

## 💡 Example

### Input

```text
What is LangChain?
```

### Workflow

```text
"What is LangChain?"
        ↓
ChatPromptTemplate
        ↓
Gemma 2B
        ↓
StrOutputParser
        ↓
Generated Answer
```

---

## 📚 Key Concepts Learned

This project covers the basic building blocks of an LLM application:

- **Prompt Templates** — structure the input given to the LLM.
- **LLMs** — generate responses based on the provided input.
- **Output Parsers** — convert model outputs into usable formats.
- **Chains** — connect multiple LangChain components together.
- **LCEL** — provides a simple way to compose LangChain components using `|`.
- **Ollama** — enables local execution of language models.
- **Gemma 2B** — the local language model used in this project.
- **LangSmith** — provides optional tracing and observability.

---

## 🎯 Purpose

This project was created as a hands-on learning project to understand how the individual components of a Generative AI application fit together.

The project focuses on the fundamentals of:

```text
Prompting
   ↓
LLM
   ↓
Parsing
   ↓
Chaining
   ↓
Application
```

More advanced concepts such as **RAG, vector databases, retrievers, agents, and fine-tuning** are outside the scope of this project.

---

## 👨‍💻 Author

**Akshat Raj**

Built as part of my hands-on learning journey in **Generative AI and LangChain**.
