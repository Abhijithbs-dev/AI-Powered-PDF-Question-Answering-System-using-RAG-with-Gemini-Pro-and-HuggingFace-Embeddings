# PDF Question Answering with RAG, Gemini, and FAISS

A Streamlit application for asking questions about PDF documents using a retrieval-augmented generation (RAG) pipeline.

## How it works

1. PDF files are loaded from the local `data/` directory.
2. The documents are split into overlapping text chunks.
3. Hugging Face sentence-transformer embeddings represent the chunks.
4. FAISS provides vector similarity retrieval.
5. Gemini generates an answer using the retrieved context.

The current application expects PDF files in `data/` and uses a local FAISS pickle file at `vector_store/faiss_index.pkl`.

## Project files

- `app.py` — Streamlit interface
- `rag_pipeline.py` — PDF loading, chunking, vector-store creation, retrieval, and Gemini chain
- `test.py` — project test/experiment script
- `requirements.txt` — Python dependencies
- `.env.example` — placeholder for the Google API key

## Requirements

- Python 3
- pip
- A Google Gemini API key with access to the model configured in `rag_pipeline.py`

## Setup

1. Clone the repository and open its directory.
2. Create and activate a virtual environment:

   ```bash
   python -m venv .venv
   # macOS/Linux
   source .venv/bin/activate
   # Windows PowerShell
   .venv\\Scripts\\Activate.ps1
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a local `.env` file from the template and set your own key:

   ```bash
   cp .env.example .env
   ```

   Set `GOOGLE_API_KEY` in `.env`. Never commit the populated file. You can instead inject the variable through your shell or deployment secret manager.

5. Create the PDF input directory and add documents:

   ```bash
   mkdir -p data
   ```

6. Start the application:

   ```bash
   streamlit run app.py
   ```

## Local data and security

- `.env`, `data/`, `vector_store/`, and generated pickle files are excluded from Git.
- Only load PDF documents you trust.
- The FAISS index is stored using Python pickle in the current implementation. Do not load an index from an untrusted source.
- A previously committed API key must be considered exposed. Rotate/revoke it with the key owner/provider; removing the current file does not remove it from past commits or from upstream repositories.

## Known implementation detail

The README describes the current code paths. Verify and pin compatible LangChain, Gemini, and Hugging Face package versions before relying on a fresh environment; dependency compatibility has not been tested as part of this documentation change.
