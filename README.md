# PrivacyRAG Local LLM with Streamlit

## Overview
This project is a private, local Retrieval-Augmented Generation (RAG) chatbot application. It leverages FastAPI for the backend and Streamlit for the frontend, allowing users to chat with a local LLM, upload documents, and perform RAG-based question answering over their own data.

## Features
- **Local LLM Chatbot**: Interact with a local language model using a chat interface.
- **Document Upload**: Upload PDF, DOCX, or HTML files for ingestion and retrieval.
- **RAG Pipeline**: Uses LangChain and ChromaDB for document indexing and retrieval.
- **Session Management**: Maintains chat history per session.
- **Document Management**: List and delete uploaded documents.

## Directory Structure
```
├── app/
│   ├── streamlit_app.py      # Streamlit entry point
│   ├── sidebar.py            # Sidebar UI (upload, list, delete docs)
│   ├── chat_interface.py     # Chat UI logic
│   └── api_utils.py          # API calls from Streamlit to FastAPI
├── main.py                   # FastAPI backend (API endpoints)
├── db_utils.py               # Database utilities (SQLite)
├── chroma_utils.py           # ChromaDB integration
├── langchain_utils.py        # LangChain RAG chain setup
├── pydantic_models.py        # Pydantic models for API
├── requirements.txt          # Python dependencies
├── README.md                 # Project documentation
```

## Setup & Installation
1. **Clone the repository**
   ```bash
   git clone <repo-url>
   cd <repo-directory>
   ```
2. **Create and activate a virtual environment**
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```
3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Running the Application
### 1. Start the FastAPI Backend
```bash
uvicorn main:app --reload
```
- The backend will be available at `http://localhost:8000`.

### 2. Start the Streamlit Frontend
```bash
streamlit run app/streamlit_app.py
```
- The frontend will be available at `http://localhost:8501`.

## Usage
- **Chat**: Enter your queries in the chat interface. The model will respond using RAG over your uploaded documents.
- **Upload Documents**: Use the sidebar to upload PDF, DOCX, or HTML files. Uploaded documents are indexed for retrieval.
- **List/Delete Documents**: View and manage your uploaded documents from the sidebar.

## API Endpoints (FastAPI)
- `POST /chat` — Chat with the LLM (RAG over uploaded docs)
- `POST /upload-doc` — Upload and index a document
- `GET /list-docs` — List all uploaded documents
- `POST /delete-doc` — Delete a document by file ID

## Dependencies
See `requirements.txt` for the full list. Key packages:
- `fastapi`, `uvicorn` — Backend API
- `streamlit` — Frontend UI
- `langchain`, `langchain-openai`, `langchain-core`, `langchain_community`, `langchain_chroma`, `langchain-ollama` — RAG pipeline
- `chroma-db` — Vector database
- `pypdf`, `docx2txt` — Document parsing
- `python-multipart` — File uploads

## Notes
- Ensure both backend and frontend are running for full functionality.
- The backend uses a local SQLite database (`rag_app.db`).
- The LLM and RAG chain are configured in `langchain_utils.py`.

## License
Specify your license here (e.g., MIT, Apache 2.0, etc.).
