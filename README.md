# OpenAI-RAG-QA

A **general-purpose, AI-powered Retrieval-Augmented Generation (RAG)** pipeline for asking questions about documents (any PDF). Built with **OpenAI**, **LangChain**, and **ChromaDB**, and fully **Colab-friendly**.

---

## ⚠️ Disclaimer

1. **Add your OpenAI API key first** in Colab Secrets or as an environment variable (`OPENAI_API_KEY`).  
2. This notebook is for **educational/demo purposes only**.  
3. AI-generated answers may **not be fully accurate**—always verify with official HR documents.  
4. **Do not upload sensitive or confidential PDFs**.  

---

## Features

- Upload **any PDF** at runtime using Colab file picker.  
- Split documents into **smaller chunks** for better embeddings.  
- Generate **OpenAI embeddings** and store them in **Chroma vector store**.  
- Perform **semantic search** to retrieve relevant chunks.  
- Ask questions via a **Gradio web interface**.  
- Returns answers with **source references**.  

---

## How to Use (Colab)

1. Open the notebook in **Google Colab**.  
2. **Add your OpenAI API key** in Colab Secrets:  
   - Go to **Tools → Settings → Secrets**.  
   - Add key: `OPENAI_API_KEY`  
   - Value: `<Your OpenAI API key>`  
3. **Upload your PDF** when prompted by the file picker.  
4. Run the notebook cells step by step:  
   - Connect to OpenAI  
   - Load PDF  
   - Split text into chunks  
   - Create embeddings & vector store  
   - Build the RAG QA chain  
   - Launch the Gradio interface  
5. **Ask questions** about your uploaded PDF using the interface.  

---

## Example Questions

- What is the company's policy on remote work?  
- How do I request vacation time?  
- What benefits are available to employees?  

---

## Notes

- Works for **any PDF document**, not tied to a specific file.  
- Make sure your document is **text-based PDF** (not scanned images).  
- The pipeline can be adapted for **other document types** (finance, legal, technical manuals, etc.).  

---

## Dependencies

- `langchain`  
- `openai`  
- `langchain_community`  
- `gradio`  
- `chromadb`  
- `PyPDFLoader`  

```bash
!pip install langchain openai langchain_community gradio chromadb
