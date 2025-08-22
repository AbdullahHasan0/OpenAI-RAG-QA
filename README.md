# OpenAI-RAG-QA

A general-purpose, AI-powered Retrieval-Augmented Generation (RAG) pipeline for asking natural-language questions about any PDF.
Built with OpenAI (LLM + embeddings), LangChain, and ChromaDB — fully Colab-friendly.

One-liner: Upload a PDF → ask questions → get concise answers with sources.

## 🔧 Models Used (Defaults & Options)

LLM (answers):

Default: gpt-4o-mini (fast, cost-efficient, strong reasoning).

Quality option: gpt-4o (higher quality; higher cost).

Embeddings (search):

Default: text-embedding-3-large (high-recall search; larger vectors).

Budget option: text-embedding-3-small (cheaper; smaller vectors).

You can switch models in one place in the notebook:

`LLM_MODEL = "gpt-4o-mini"          # or "gpt-4o"`
`EMBED_MODEL = "text-embedding-3-large"  # or "text-embedding-3-small"`

## ⚠️ Disclaimer

Add your OpenAI API key first (Colab Secrets or env var OPENAI_API_KEY).

This notebook is for educational/demo purposes.

AI-generated answers can be incomplete or wrong — verify with official documents.

Do not upload sensitive or confidential PDFs.

## ✨ Features

📂 Upload any PDF at runtime using Colab’s file picker (no repo data baked in).

✂️ Smart chunking (configurable size & overlap) to preserve context.

🧭 ChromaDB vector store built from OpenAI embeddings.

🔎 Semantic retrieval to pull the most relevant chunks.

🤖 LLM answers grounded in retrieved context (RAG) to reduce hallucination.

🖥️ Gradio UI for interactive Q&A with source references.

🧱 Clear, modular cells you can reuse in other projects.

## 🚀 How to Use (Google Colab)

Open the notebook in Google Colab.

Add your OpenAI API key in Colab Secrets:

Go to Tools → Settings → Secrets

Add key: OPENAI_API_KEY

Value: <your OpenAI API key>

Upload your PDF when prompted by the file picker.

Run cells step-by-step:

Connect to OpenAI

Load PDF

Split into chunks

Create embeddings & Chroma vector store

Build the RAG QA chain

Launch the Gradio app

Ask questions about your document and view answers + sources.

## 💡 Example Questions

What is the company’s policy on remote work?

How do I request vacation time?

What benefits are available to employees?

Summarize section 3 and list the key exceptions.

## 🧠 How It Works (High-Level Architecture)

Ingest → Load PDF pages (PyPDFLoader).

Chunk → Split text into overlapping segments (e.g., 1,000 chars, 150 overlap).

Embed → Create vector embeddings with OpenAI embeddings.

Index → Store in ChromaDB for fast similarity search.

Retrieve → On each question, fetch top-k relevant chunks.

Generate → LLM answers using only retrieved context (custom prompt discourages hallucination).

Attribute → Return answer + source references.

## 🛠️ Configuration & Tuning

Chunking

CHUNK_SIZE = 1000

CHUNK_OVERLAP = 150

Larger chunks = more context per hit; smaller chunks = tighter precision.

Retrieval

k (top results): start with k=2 or k=3.

Prompting

Use a strict prompt: “Answer only from context; otherwise say you don’t know.”

Models

Swap LLM_MODEL and EMBED_MODEL constants to match your speed/quality budget.

## 📝 Notes & Best Practices

Works with text-based PDFs (not scanned images). Use OCR first if needed.

For multi-PDF support, load multiple files and build a single vector store.

To persist the vector store, set a Chroma persist_directory between runs.

Keep your API key in Colab Secrets — never hard-code secrets in notebooks.

## 🧯 Troubleshooting

Empty answers / “I don’t know” → raise k, increase chunk size, or check the PDF text extraction.

Irrelevant answers → try text-embedding-3-large, increase overlap, or improve the prompt.

Rate limits → add short sleeps between calls; lower batch sizes.

Scanned PDFs → run OCR (e.g., with pytesseract or upload a text-based version).

## 📦 Dependencies

`langchain` 

`openai`

`langchain_community`

`chromadb`

`gradio`

`pypdf / PyPDFLoader `
