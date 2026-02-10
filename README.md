📄 DocuMind AI – Intelligent Document Q&A System (RAG-based)
============================================================

DocuMind AI is an **AI-powered document question-answering system** built using **Retrieval-Augmented Generation (RAG)**.It allows users to upload documents and ask questions, and the system answers **strictly based on the document content**, ensuring **accuracy, grounding, and transparency**.

This project demonstrates **real-world GenAI system design**, combining **LLMs, vector databases, agents, and APIs**.

🚀 Features
-----------

*   📚 Upload and process documents (PDF / text-based files)
    
*   🔍 Semantic search using embeddings and vector database
    
*   🤖 AI-generated answers grounded in document content
    
*   🧠 Multi-turn conversational memory
    
*   📑 Source transparency (answers are backed by retrieved chunks)
    
*   ⚡ Fast and scalable backend using FastAPI
    
*   🎨 Simple and interactive UI using Streamlit
    

🧠 Why Retrieval-Augmented Generation (RAG)?
--------------------------------------------

Large Language Models (LLMs) are powerful but:

*   They **hallucinate**
    
*   They **don’t know private documents**
    
*   They **cannot be trusted blindly**
    

**RAG solves this by:**

1.  Retrieving **relevant document content**
    
2.  Feeding it to the LLM as **context**
    
3.  Generating answers **only from retrieved data**
    

This ensures:

*   ✅ Accuracy
    
*   ✅ Trustworthiness
    
*   ✅ No hallucinations
    

🏗️ System Architecture
-----------------------

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   User │ │ Question ▼Streamlit UI │ ▼FastAPI Backend │ ├── Document Loader │ ├── Chunking Engine │ ├── Embedding Generator (HuggingFace) │ ├── Vector Store (ChromaDB) │ ├── Retriever (Semantic Search) │ └── CrewAI Agent        │        ▼     Groq LLM        │        ▼   Final Answer + Sources   `

🛠️ Tech Stack
--------------

LayerTechnologyBackend APIFastAPIFrontendStreamlitAI AgentCrewAIRAG FrameworkLlamaIndexEmbeddingsHuggingFaceVector DatabaseChromaDBLLM ProviderGroqLanguagePythonVersion ControlGitHub

📂 Project Structure
--------------------

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   DocuMind-AI/│├── backend/│   ├── main.py              # FastAPI entry point│   ├── rag_pipeline.py      # RAG logic│   ├── crew_agent.py        # CrewAI agent definition│   ├── embeddings.py        # HuggingFace embedding setup│   ├── vector_store.py      # ChromaDB integration│   └── utils.py             # Helper functions│├── frontend/│   └── app.py               # Streamlit UI│├── data/│   └── uploads/             # Uploaded documents│├── chroma_db/               # Persistent vector database│├── requirements.txt├── .env.example└── README.md   `

🔄 End-to-End Flow (How Everything Works)
-----------------------------------------

### 1️⃣ Document Upload

*   User uploads a document from Streamlit UI
    
*   Document is sent to FastAPI backend
    

### 2️⃣ Document Chunking

*   Large documents are split into **smaller chunks**
    
*   Chunk size: ~1024 tokens with overlap
    
*   This improves:
    
    *   Retrieval accuracy
        
    *   Context relevance
        

### 3️⃣ Embedding Generation

*   Each chunk is converted into a **vector embedding**
    
*   Uses **HuggingFace sentence transformer models**
    
*   Embeddings capture **semantic meaning**, not keywords
    

### 4️⃣ Vector Storage (ChromaDB)

*   Embeddings are stored in **ChromaDB**
    
*   Persistent storage enables:
    
    *   Faster future queries
        
    *   No need to re-embed documents
        

### 5️⃣ Semantic Retrieval

*   User question is converted into an embedding
    
*   ChromaDB performs **similarity search**
    
*   Top-k most relevant chunks are retrieved
    

### 6️⃣ CrewAI Agent Reasoning

*   Retrieved chunks are passed to a **CrewAI agent**
    
*   Agent responsibilities:
    
    *   Read retrieved content
        
    *   Stay strictly grounded to documents
        
    *   Structure a clean, understandable answer
        

### 7️⃣ LLM Response Generation

*   Agent uses **Groq-powered LLM**
    
*   LLM generates answer **only using provided context**
    
*   No external or hallucinated data
    

### 8️⃣ Answer + Sources

*   Final answer is sent to frontend
    
*   Supporting document chunks are shown as **sources**
    
*   Ensures transparency and trust
    

🤖 CrewAI Agent Design
----------------------

The CrewAI agent is responsible for:

*   Context understanding
    
*   Answer structuring
    
*   Preventing hallucinations
    

**Agent Instructions (Conceptually):**

*   Answer only from retrieved documents
    
*   If answer not found, say _“Information not available in the document”_
    
*   Be concise and clear
    

🔐 Environment Variables
------------------------

Create a .env file:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   GROQ_API_KEY=your_groq_api_key   `

▶️ How to Run the Project
-------------------------

### 1️⃣ Clone Repository

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   git clone https://github.com/your-username/DocuMind-AI.gitcd DocuMind-AI   `

### 2️⃣ Create Virtual Environment

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   python -m venv venvsource venv/bin/activate   # Windows: venv\Scripts\activate   `

### 3️⃣ Install Dependencies

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   pip install -r requirements.txt   `

### 4️⃣ Start Backend (FastAPI)

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   cd backenduvicorn main:app --reload   `

Backend runs at:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   http://localhost:8000   `

### 5️⃣ Start Frontend (Streamlit)

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   cd frontendstreamlit run app.py   `

Frontend runs at:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   http://localhost:8501   `

🧪 Example Use Case
-------------------

1.  Upload a company policy PDF
    
2.  Ask: _“What is the leave policy?”_
    
3.  System retrieves relevant policy sections
    
4.  AI answers with exact policy explanation
    
5.  Source text is displayed for verification
    
    

🎯 What This Project Demonstrates
---------------------------------

*   Real-world **RAG architecture**
    
*   Vector databases & semantic search
    
*   AI agent orchestration
    
*   Backend–Frontend integration
    
*   Production-style AI system design
    

🧑‍💻 Author
------------

**Ritik Garg**
