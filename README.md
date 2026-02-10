# 📄 DocuMind AI – Intelligent Document Question Answering System (RAG)

DocuMind AI is an AI-powered document question answering system built using Retrieval-Augmented Generation (RAG).  
It allows users to upload documents and ask questions, and the system answers strictly based on the document content, ensuring accuracy, grounding, and transparency.

This project demonstrates a real-world GenAI system by combining LLMs, vector databases, AI agents, and backend APIs.

---

## 🚀 Features

- Upload and process documents (PDF / text-based files)
- Semantic search using vector embeddings
- AI-generated answers grounded in document data
- Multi-turn conversational support
- Source transparency for each answer
- FastAPI-based backend
- Streamlit-based interactive frontend

---

## 🧠 Why Retrieval-Augmented Generation (RAG)?

Large Language Models (LLMs) are powerful but:
- They can hallucinate
- They do not know private documents
- They cannot be trusted without grounding

RAG solves this by:
1. Retrieving relevant document content
2. Passing it as context to the LLM
3. Generating answers strictly from retrieved data

This ensures accurate, reliable, and trustworthy responses.

---

## 🏗️ System Architecture

User  
↓  
Streamlit Frontend  
↓  
FastAPI Backend  
- Document Loader  
- Chunking Engine  
- HuggingFace Embedding Generator  
- ChromaDB Vector Store  
- Semantic Retriever  
- CrewAI Agent  
↓  
Groq LLM  
↓  
Final Answer with Sources  

---

## 🛠️ Tech Stack

Backend: FastAPI  
Frontend: Streamlit  
AI Agent: CrewAI  
RAG Framework: LlamaIndex  
Embeddings: HuggingFace  
Vector Database: ChromaDB  
LLM Provider: Groq  
Language: Python  
Version Control: GitHub  

---

## 📂 Project Structure

DocuMind-AI/  
├── backend/  
│   ├── main.py  
│   ├── rag_pipeline.py  
│   ├── crew_agent.py  
│   ├── embeddings.py  
│   ├── vector_store.py  
│   └── utils.py  
│  
├── frontend/  
│   └── app.py  
│  
├── data/  
│   └── uploads/  
│  
├── chroma_db/  
│  
├── requirements.txt  
├── .env.example  
└── README.md  

---

## 🔄 End-to-End Workflow

1. User uploads a document using the Streamlit UI  
2. Document is sent to FastAPI backend  
3. Document is split into chunks (~1024 tokens with overlap)  
4. Each chunk is converted into embeddings using HuggingFace models  
5. Embeddings are stored in ChromaDB  
6. User question is converted into an embedding  
7. Semantic search retrieves the most relevant document chunks  
8. Retrieved chunks are passed to a CrewAI agent  
9. Agent generates a grounded response using Groq LLM  
10. Final answer is returned with supporting document sources  

---

## 🤖 CrewAI Agent Design

The CrewAI agent is responsible for:
- Understanding retrieved document context
- Generating structured and grounded responses
- Preventing hallucinations

Agent rules:
- Answer only from retrieved document content  
- If information is not found, respond with:  
  "Information not available in the document"  
- Keep answers clear and concise  

---

## 🔐 Environment Variables

Create a `.env` file in the root directory:

GROQ_API_KEY=your_groq_api_key

---

## ▶️ How to Run the Project

1. Clone the repository

git clone https://github.com/your-username/DocuMind-AI.git  
cd DocuMind-AI  

2. Create a virtual environment

python -m venv venv  
source venv/bin/activate   (Windows: venv\Scripts\activate)

3. Install dependencies

pip install -r requirements.txt

4. Start the backend server

cd backend  
uvicorn main:app --reload  

Backend will run on:  
http://localhost:8000  

5. Start the frontend application

cd frontend  
streamlit run app.py  

Frontend will run on:  
http://localhost:8501  

---

## 🧪 Example Use Case

1. Upload a company policy document  
2. Ask: "What is the leave policy?"  
3. System retrieves relevant sections  
4. AI generates an accurate answer  
5. Supporting document sources are shown  

---

## 📈 Future Improvements

- Redis caching for faster repeated queries  
- Support for multiple document collections  
- Authentication and user management  
- OCR support for scanned PDFs  
- Feedback loop for answer improvement  

---

## 🎯 What This Project Demonstrates

- Real-world RAG architecture  
- Vector databases and semantic search  
- AI agent orchestration using CrewAI  
- Backend and frontend integration  
- Production-style GenAI system design  

---

## 👨‍💻 Author
Ritik Garg  
