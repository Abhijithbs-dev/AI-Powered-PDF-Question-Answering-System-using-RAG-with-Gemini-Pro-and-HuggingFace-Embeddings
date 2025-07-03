# 📚 AI-Powered PDF Question Answering App (RAG + Gemini + FAISS)

This project is an intelligent question-answering system that allows users to **ask questions directly from uploaded PDF documents**. It leverages **Retrieval-Augmented Generation (RAG)** using **HuggingFace embeddings**, **FAISS vector store**, and **Google Gemini 2.5 Pro/Flash** for accurate and contextual answers.

![Streamlit UI Screenshot](screenshot.png) <!-- Optional image if you want to show a UI preview -->

---

## 🚀 Features

- 📄 Upload and query content from multiple PDFs
- 🧠 Uses `HuggingFace sentence-transformers` for text embeddings
- ⚡ Fast and accurate retrieval with `FAISS` vector indexing
- 🤖 Answer generation using `Gemini 2.5 Pro/Flash`
- 🌐 Web app built with `Streamlit`
- 🔄 Caching and persistence with vector store pickle files

---

## 🛠️ Tech Stack

- **Frontend:** Streamlit
- **LLM:** Google Gemini 2.5 (Pro/Flash)
- **Embedding Model:** all-MiniLM-L6-v2 (HuggingFace)
- **Vector DB:** FAISS
- **PDF Parsing:** PyPDFLoader (LangChain)
- **Frameworks:** LangChain, dotenv

---

## 📁 Project Structure

```bash
├── app.py                 # Streamlit app UI
├── rag_pipeline.py        # RAG logic and chain creation
├── test.py                # CLI testing script
├── requirements.txt       # Required packages
├── .env                   # API keys and environment variables
├── vector_store/          # FAISS index stored here
└── data/                  # Folder for uploaded PDF files
