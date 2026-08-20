# 🔬 ResearchMind — Multi-Agent AI Research System

> An AI-powered multi-agent research system that searches the web, reads relevant sources, generates structured research reports, and critically evaluates the final output.

## 🌐 Live Demo

👉 **[Launch ResearchMind](https://multiagentairesearchsystem-42rzanwk5mytq2tryyxisy.streamlit.app/)**

Experience the multi-agent research pipeline directly in your browser.

---

## 🚀 Overview

**ResearchMind** is a multi-agent AI research application built with **LangChain, Mistral, Tavily, Python, and Streamlit**.

Instead of relying on a single LLM call, the system divides the research workflow into specialized stages:

```text
User Topic
    ↓
🔎 Search Agent
    ↓
🌐 Tavily Web Search
    ↓
📄 Reader Agent
    ↓
🔗 Web Scraping
    ↓
✍️ Writer Chain
    ↓
🧐 Critic Chain
    ↓
📑 Final Research Report
```

The application provides a polished Streamlit interface for interacting with the research pipeline.

---

## ✨ Key Features

- 🔎 AI-powered web research
- 🤖 Multi-agent architecture
- 🌐 Tavily web search
- 📄 Deep source reading through web scraping
- ✍️ Structured AI-generated research reports
- 🧐 AI-based report evaluation
- 📊 Research quality score and feedback
- 🖥️ Premium Streamlit interface
- 📥 Download generated reports as Markdown
- ⚡ Pipeline progress visualization
- 🌙 Modern dark-themed UI

---

## 🧠 Multi-Agent Architecture

The system consists of four major stages.

### 1. 🔎 Search Agent

The Search Agent receives the user's research topic and uses the Tavily search tool to find recent and relevant information.

```text
Research Topic
      ↓
Search Agent
      ↓
Tavily
      ↓
Search Results
```

The search tool returns titles, URLs, and snippets from the retrieved sources.

---

### 2. 📄 Reader Agent

The Reader Agent receives the search results and identifies a relevant URL for deeper investigation.

It then uses the scraping tool to retrieve additional content from that source.

```text
Search Results
      ↓
Reader Agent
      ↓
Relevant URL
      ↓
Web Scraper
      ↓
Detailed Content
```

The scraper uses **Requests** and **BeautifulSoup** to extract readable webpage content.

---

### 3. ✍️ Writer Chain

The Writer Chain combines:

- Search results
- Scraped source content
- Research topic

It generates a structured research report containing:

- Introduction
- Key Findings
- Conclusion
- Sources

The writer is instructed to produce detailed, factual, and professional content.

---

### 4. 🧐 Critic Chain

The generated report is passed to a separate critic chain.

The critic evaluates the report and returns:

```text
Score: X/10

Strengths:
- ...
- ...

Areas to Improve:
- ...
- ...

One line verdict:
...
```

This creates an additional evaluation stage rather than stopping immediately after report generation.

---

# 🏗️ Project Architecture

```text
                         ┌──────────────────┐
                         │      User        │
                         │  Research Topic  │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │   Streamlit UI   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │   Search Agent   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │  Tavily Search   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │   Reader Agent   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │ Requests +       │
                         │ BeautifulSoup    │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │   Writer Chain   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │   Critic Chain   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │ Research Report  │
                         │ + Evaluation     │
                         └──────────────────┘
```

---

# 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **Python 3.13** | Core programming language |
| **LangChain** | Agent and LLM orchestration |
| **Mistral** | Large language model |
| **Tavily** | Web search |
| **Requests** | HTTP requests for webpage scraping |
| **BeautifulSoup** | HTML parsing and content extraction |
| **Streamlit** | Web interface |
| **python-dotenv** | Environment variable management |
| **Pydantic** | Data validation |
| **Tenacity** | Retry handling |

---

# 📁 Project Structure

```text
MultiAgent_AI_Research_System/
│
├── app.py
├── agents.py
├── pipeline.py
├── tools.py
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

### `app.py`

Contains the Streamlit frontend and presentation layer.

### `agents.py`

Contains:

- Search Agent
- Reader Agent
- Writer Chain
- Critic Chain
- Mistral LLM configuration

### `pipeline.py`

Coordinates the complete research workflow:

```text
Search
  ↓
Read
  ↓
Write
  ↓
Critique
```

### `tools.py`

Contains the external tools used by the agents:

- Tavily web search
- URL scraping

### `requirements.txt`

Contains the Python dependencies required to run the project.

---

# ⚙️ Installation

## 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/MultiAgent_AI_Research_System.git
cd MultiAgent_AI_Research_System
```

---

## 2. Create a virtual environment with `uv`

If you don't have `uv` installed:

```bash
pip install uv
```

Create the environment:

```bash
uv venv
```

Activate it on macOS/Linux:

```bash
source .venv/bin/activate
```

---

## 3. Install dependencies

```bash
uv pip install -r requirements.txt
```

---

# 🔑 API Configuration

Create a `.env` file in the project root:

```env
MISTRAL_API_KEY=your_mistral_api_key
TAVILY_API_KEY=your_tavily_api_key
```

### Mistral

Mistral is used as the LLM provider for the agents and chains.

### Tavily

Tavily is used by the search tool to retrieve recent web information.

**Never commit your `.env` file to GitHub.**

Add this to `.gitignore`:

```text
.env
.venv/
__pycache__/
```

---

# ▶️ Running the Application

Start the Streamlit application with:

```bash
uv run streamlit run app.py
```

The application will be available locally at:

```text
http://localhost:8501
```

---

# 🖥️ Application Workflow

### Step 1 — Enter a research topic

Enter the topic you want the system to investigate.

Example:

```text
Impact of Generative AI on Software Development
```

### Step 2 — Start the pipeline

The system executes the four research stages:

```text
01  Search Agent
02  Reader Agent
03  Writer Chain
04  Critic Chain
```

### Step 3 — Review the results

The application displays:

- Search results
- Scraped content
- Final research report
- Critic feedback

### Step 4 — Download the report

The generated report can be downloaded as a Markdown file.

---

# 🔄 Data Flow

```text
Topic
  │
  ▼
Search Agent
  │
  ├── Tavily
  │
  ▼
Search Results
  │
  ▼
Reader Agent
  │
  ├── Requests
  ├── BeautifulSoup
  │
  ▼
Scraped Content
  │
  ▼
Writer Chain
  │
  ▼
Research Report
  │
  ▼
Critic Chain
  │
  ▼
Score + Strengths + Improvements + Verdict
```

---

# 🎯 Why Multi-Agent?

A traditional approach could send the user's question directly to an LLM:

```text
Question → LLM → Answer
```

ResearchMind instead separates the workflow:

```text
Question
   ↓
Search
   ↓
Read
   ↓
Write
   ↓
Critique
```

Each stage has a specific responsibility.

This makes the research process more structured and allows the generated report to be evaluated by a separate critic stage.

---

# 🧩 Core Components

### Agents

The project uses LangChain agents for:

- Web research
- Source reading

### Chains

LangChain chains are used for:

- Report generation
- Report criticism

### Tools

The system currently exposes two tools:

```text
web_search()
scrape_url()
```

The web search tool uses Tavily, while the scraping tool uses Requests and BeautifulSoup.

---

# 📌 Example Use Cases

ResearchMind can be used for topics such as:

- Artificial Intelligence
- Machine Learning
- Generative AI
- Emerging technologies
- Software engineering
- Scientific developments
- Technology trends
- Academic research topics

The quality and availability of information depend on the external sources retrieved during the research process.

---

# 🔐 Security Notes

API keys should be stored in environment variables rather than directly inside Python files.

Never commit:

```text
.env
```

to a public GitHub repository.

If an API key is accidentally exposed, revoke it and generate a new one.

---

# 🚧 Current Limitations

The current implementation has several intentional limitations:

- The Reader Agent focuses on a selected relevant URL rather than crawling many sources.
- Web scraping depends on the target website allowing successful HTTP retrieval.
- Research quality depends on the information returned by external search sources.
- API usage is subject to the limits of the selected LLM and Tavily plans.
- The system does not use persistent conversation memory.
- The system does not use a database or RAG pipeline.

These limitations reflect the current implementation rather than missing UI features.

---

# 🔮 Future Improvements

Potential future extensions include:

- Multi-source parallel reading
- Source credibility ranking
- Citation verification
- Research history
- Persistent projects
- RAG-based knowledge storage
- PDF/document research
- Improved source extraction
- Parallel agent execution
- More advanced report evaluation

These are future possibilities and are not part of the current implementation.

---

# 📊 Project Highlights

```text
Multi-Agent AI
      +
Web Search
      +
Web Scraping
      +
LLM Report Generation
      +
AI Criticism
      +
Streamlit UI
```

### Main Engineering Concepts Demonstrated

- Agent orchestration
- LLM integration
- Tool calling
- Web search
- Web scraping
- Prompt engineering
- Sequential AI workflows
- Chain-based processing
- Streamlit application development
- Environment-based API configuration

---

# 👨‍💻 Author

**Priyanshu Choubey**

B.Tech — Artificial Intelligence & Machine Learning

---

# ⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub and exploring the implementation.