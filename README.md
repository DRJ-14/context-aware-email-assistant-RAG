# Context-Aware Email Assistant (RAG over Gmail .mbox + Fine-tuned Gemma)

A local-first Retrieval-Augmented Generation (RAG) system that answers questions over Gmail archives exported via Google Takeout (.mbox). It parses/cleans emails, builds a vector index, retrieves relevant context, and generates grounded answers using local LLM inference. Includes an optional Gemma fine-tuning notebook (QLoRA).

## Problem
Keyword search isn’t enough for large mailboxes. This project enables semantic search + QA over historical emails while keeping data local.

## Architecture
Takeout (.mbox) → Parse/Clean → Chunk → Embed → ChromaDB → Retrieve (top-k) → LLM → Answer

## Tech Stack
- Python, Jupyter
- LangChain (RAG)
- ChromaDB (vector store)
- GPT4All embeddings (embeddings)
- Local inference (GPT4All / llama.cpp)
- BeautifulSoup (HTML cleaning)
- Optional fine-tuning: Transformers + TRL + PEFT (LoRA) + bitsandbytes (4-bit)

## Setup
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Results
- Enables semantic search + question answering over Gmail Takeout exports while keeping data local.
- Retrieves top-k relevant email chunks and generates grounded answers with citations to source messages.
- Designed to avoid committing sensitive data (Takeout/.mbox ignored via .gitignore).
