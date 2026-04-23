# agentic-rag-llamaindex
This code builds a **practical Agentic RAG system (“Alfred”)** that:  * integrates multiple tools (RAG over custom data, web search, weather, etc.), * retrieves structured + real-time information, * and answers user queries by **choosing the right tool/workflow at runtime**.


**Agentic RAG (short technical view)**
Agentic RAG extends classic Retrieval-Augmented Generation by adding an **agent layer (LLM with tool-use + planning)** on top of retrieval. Instead of a fixed pipeline (retrieve → stuff context → generate), the model can **decide dynamically**:

* what to retrieve,
* when to retrieve again (iterative loops),
* which tools to call (search, APIs, DBs),
* and how to combine intermediate results.

This turns RAG into a **closed-loop reasoning system** where the LLM orchestrates retrieval and reasoning steps, improving adaptability and multi-step problem solving ([Hugging Face][1]).

---

**What this project is about**

The concrete use case is a **”gala assistant agent”** that:

* manages guest knowledge, schedules, and context,
* retrieves relevant info on demand using BM25 search over a guest dataset,
* and handles dynamic queries during the event ([Hugging Face][2]).

[1]: https://huggingface.co/learn/agents-course/en/unit3/agentic-rag/agentic-rag?utm_source=chatgpt.com “Agentic Retrieval Augmented Generation (RAG) · Hugging Face”
[2]: https://huggingface.co/learn/agents-course/en/unit3/agentic-rag/introduction?utm_source=chatgpt.com “Introduction to Use Case for Agentic RAG · Hugging Face”

---

## Stack

| Component | Version | Purpose |
|---|---|---|
| Python | 3.14.3 | Runtime |
| Ollama | 0.17.2 | Local LLM server |
| qwen2:7b | — | LLM model (run via Ollama, free & local) |
| datasets | 4.8.4 | Load the HuggingFace guest dataset |
| llama-index | 0.14.21 | Agent and RAG orchestration framework |
| llama-index-retrievers-bm25 | 0.7.1 | BM25 keyword retrieval over guest docs |
| llama-index-llms-ollama | 0.10.1 | Ollama LLM integration for llama-index |

---

## Setup & Execution

**1. Install Ollama and pull the model**

Download Ollama from [ollama.com](https://ollama.com) and then pull the model:

```bash
ollama pull qwen2:7b
```

**2. Start the Ollama server**

```bash
ollama serve
```

**3. Create and activate a virtual environment**

```bash
python3 -m venv .venv
source .venv/bin/activate        # macOS/Linux
# .venv\Scripts\activate         # Windows
```

**4. Install Python dependencies**

```bash
pip install datasets llama-index llama-index-retrievers-bm25 llama-index-llms-ollama
```

**5. Run the script**

```bash
python3 main.py
```
