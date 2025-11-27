---

# 🚀 LangChain RAG System with FastAPI, Chroma & Neon PostgreSQL

A production-ready **Retrieval-Augmented Generation (RAG)** backend built using **FastAPI**, **LangChain**, **HuggingFace Embeddings**, **Chroma**, and **Neon PostgreSQL**.
Supports **PDF/Web ingestion**, **vector search**, **JWT-secured APIs**, and **structured LLM topic generation**.

---

## ⚡ My Personal Contributions

I contributed a major portion of the **API layer, database schemas, authentication, and ingestion workflow** for this project. Specifically, I implemented:

### ✅ **What I Built**

* **Production-grade API** using FastAPI

  * JWT-based authentication (register/login, protected routes)
  * Secure password hashing with bcrypt
* **Multiple API Routes & Schemas**

  * User, workspace, query, topic generation
* **Persistent Logging System**

  * Saved user queries & LLM responses into **Neon PostgreSQL**
  * SQLAlchemy models + structured migrations-ready schema
* **Topic-generation microservice**

  * Structured LLM output using Pydantic models
* **Background ingestion system**

  * Async document scraping + vector ingestion per workspace
* **Git merging & conflict resolution for the entire repo**

### 🛠 Additional Points I Implemented

* Clear folder structure for the API and utilities
* Modular utils (JWT helpers, password hashing, text splitter)
* Workspace lifecycle logic (create/update/delete + vector DB cleanup)


---

## 📁 My Folder Structure (the structure I built)

```
rag_project/api
├─ db/                # DB connection + session + vector store helpers  
├─ embedding/         # HuggingFace embedding wrappers  
├─ model_state/       # Pydantic output schemas for structured LLM results  
├─ prompts/           # Prompt templates  
├─ routes/            # FastAPI routes (user, query, workspace, topic generation)  
├─ schema/            # SQLAlchemy models (User, Workspace, QueryLog, TopicGeneration)  
├─ scrape/            # Scrapers & loaders  
├─ state/             # Request schemas, OAuth helpers  
├─ utils/             # text_splitter, jwt, hashing, helpers  
└─ server.py          # Main FastAPI app + router registration  
```

---

---

## 🔥 Core Features

### 📄 Document Ingestion

* PDF ingestion
* Web scraping / loader support
* Recursive text splitting

### 🧠 Embeddings & Vector Store

* HuggingFace embeddings
* Chroma vector store
* Workspace-specific vector DB lifecycle

### 🔍 Retrieval System

* Similarity search
* RAG pipeline (Retriever → Context → LLM)

### 🤖 LLM Support

* Groq
* OpenAI
* Structured output with Pydantic

### 🛡 Authentication

* JWT
* bcrypt password hashing
* Protected routes

### 📊 Query Logging

* Every query & response stored in Neon PostgreSQL

### 📚 Topic Generation

* LLM structured topic extraction
* JSON schema enforced via Pydantic models

---

## 🌱 Environment Setup

### 1️⃣ Create Virtual Environment

```bash
python -m venv .venv
```

Activate:

**Windows**

```bash
.venv\Scripts\activate
```

**Linux/Mac**

```bash
source .venv/bin/activate
```

---

### 2️⃣ Install Dependencies (using uv OR pip)

#### Install using **uv** (recommended)

```bash
uv pip install -r requirements.txt
```

#### Or install using **pip**

```bash
pip install -r requirements.txt
```

---

### 3️⃣ Create `.env` File

```
DATABASE_URL=postgresql+psycopg2://<user>:<password>@<neon_host>/<db>?sslmode=require
SECRET_KEY=<your_jwt_secret>
ALGORITHM=HS256
OPENAI_API_KEY=...
GROQ_API_KEY=...
```

---

### 4️⃣ Run FastAPI Server

```bash
uvicorn rag_project.api.server:app --reload
```

---

## 🧪 Key Endpoints

### 🔐 Auth

* `POST /user/register`
* `POST /user/login`

### 🗂 Workspaces

* `POST /workspace/create_workspace`
* `GET /workspace/read_workspace`
* `PUT /workspace/update_workspace`
* `DELETE /workspace/delete_workspace`

### 🤖 RAG

* `POST /query/query`

### 🧵 Topic Generation

* `POST /topic_generation/generate_topic`

---

## 🛠 Implementation Notes (for reviewers & employers)

* JWT middleware allows either `Bearer <token>` or raw header token
* Text splitter optimized for high recall
* Vector store created/destroyed per workspace
* Topic generation enforces strict JSON schema
* Neon used for cloud PostgreSQL storage
* Compatible with latest `langchain-core` + `langgraph`

---

## 📚 What I Learned

* Building a **production-grade RAG backend**
* Writing modular & scalable FastAPI architectures
* Secure JWT authentication
* SQLAlchemy ORM relationships
* Async ingestion workflows
* Git conflict resolution & merging feature branches
* Best practices for structuring AI backend projects

---

## 👥 Contributors

* **Wahab418** — LLM setup, data extraction, text splitting, RAG pipeline construction, vectorstore creation, SQLAlchemy schema design for RAG responses, and PDF parsing (tables, text, images).
* **Arsalan Azhar** — API development (FastAPI), request/response schemas, authentication (JWT + bcrypt), workspace logic, structured LLM topic-generation pipeline, background ingestion tasks, Neon/PostgreSQL logging system, and Git merging & conflict resolution.
* **Jalalahmadhub** — Docker configuration, Docker Compose setup, CI/CD pipeline implementation, and Docker Hub deployment automation.

---


## 📝 License

MIT License 

---
