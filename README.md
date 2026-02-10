# 📄 DocuMind AI – Intelligent Document Question Answering System (RAG)

DocuMind AI is an **AI-powered document question answering system** built using **Retrieval-Augmented Generation (RAG)**.  
It allows users to upload documents and ask questions, and the system answers **strictly based on the document content**, ensuring **accuracy, grounding, and transparency**.

This project demonstrates a **real-world GenAI system** combining **LLMs, vector databases, AI agents, and backend APIs**.

---

## 🚀 Features

- 📚 Upload and process documents (PDF / text-based)
- 🔍 Semantic search using embeddings
- 🤖 AI-generated answers grounded in document data
- 🧠 Multi-turn conversational support
- 📑 Source transparency for answers
- ⚡ FastAPI-based backend
- 🎨 Streamlit-based interactive frontend

---

## 🧠 Why Retrieval-Augmented Generation (RAG)?

Large Language Models (LLMs) are powerful but:

- They may hallucinate
- They do not know private or custom documents
- They cannot be trusted without grounding

**RAG solves this problem by:**

1. Retrieving relevant document content
2. Passing it as context to the LLM
3. Generating answers strictly from retrieved data

This ensures:
- ✅ Accurate answers  
- ✅ No hallucinations  
- ✅ Trustworthy responses  

---
## 🛠️ Tech Stack

| Layer | Technology |
|-----|-----------|
| Backend | FastAPI |
| Frontend | Streamlit |
| AI Agent | CrewAI |
| RAG Framework | LlamaIndex |
| Embeddings | HuggingFace |
| Vector Database | ChromaDB |
| LLM Provider | Groq |
| Language | Python |
| Version Control | GitHub |


## 🔄 End-to-End Workflow

### 1️⃣ Document Upload
- User uploads a document via Streamlit UI
- File is sent to FastAPI backend

---

### 2️⃣ Document Chunking
- Document is split into smaller chunks
- Chunk size ~1024 tokens with overlap
- Improves retrieval accuracy and context relevance

---

### 3️⃣ Embedding Generation
- Each chunk is converted into vector embeddings
- Uses HuggingFace sentence transformer models
- Embeddings capture semantic meaning, not keywords

---

### 4️⃣ Vector Storage (ChromaDB)
- Embeddings are stored in ChromaDB
- Database is persistent for faster future queries

---

### 5️⃣ Semantic Retrieval
- User question is converted into an embedding
- Similarity search is performed in ChromaDB
- Top relevant chunks are retrieved

---

### 6️⃣ CrewAI Agent Reasoning
- Retrieved chunks are passed to a CrewAI agent
- Agent responsibilities:
  - Understand document context
  - Prevent hallucinations
  - Generate structured answers

---

### 7️⃣ Answer Generation (LLM)
- Agent uses Groq-powered LLM
- Answer is generated only from retrieved content
- No external or fabricated information

---

### 8️⃣ Response with Sources
- Final answer is returned to frontend
- Source document chunks are displayed
- Ensures transparency and trust

---

## 🤖 CrewAI Agent Design

The CrewAI agent is responsible for:

- Context understanding
- Grounded answer generation
- Clean and readable output

**Agent rules:**
- Answer only from retrieved document data
- If answer is not present, say:
  > "Information not available in the document"
- Keep responses concise and clear
  
---

## 🧪 Example Use Case

1. Upload a company policy PDF
2. Ask: **"What is the leave policy?"**
3. System retrieves relevant sections
4. AI generates an answer
5. Supporting document sources are shown

---
