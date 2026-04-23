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

**What this Hugging Face project is about**
The course unit builds a **practical Agentic RAG system (“Alfred”)** that:

* integrates multiple tools (RAG over custom data, web search, weather, etc.),
* retrieves structured + real-time information,
* and answers user queries by **choosing the right tool/workflow at runtime**. ([Hugging Face][1])

The concrete use case is a **“gala assistant agent”** that:

* manages guest knowledge, schedules, and context,
* retrieves relevant info on demand,
* and handles dynamic queries during the event (including unexpected situations) ([Hugging Face][2]).

👉 In essence: it’s an **end-to-end, tool-augmented agent system** where RAG is just one capability inside a broader **agentic decision loop**.

[1]: https://huggingface.co/learn/agents-course/en/unit3/agentic-rag/agentic-rag?utm_source=chatgpt.com "Agentic Retrieval Augmented Generation (RAG) · Hugging Face"
[2]: https://huggingface.co/learn/agents-course/en/unit3/agentic-rag/introduction?utm_source=chatgpt.com "Introduction to Use Case for Agentic RAG · Hugging Face"
