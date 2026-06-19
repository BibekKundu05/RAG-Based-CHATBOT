# 🚀 Gemini-Powered RAG Assistant

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/LangChain-RAG-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Google-Gemini-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/ChromaDB-Vector%20Store-purple?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Gradio-Web%20UI-red?style=for-the-badge" />
</p>

## 📖 Overview

This project demonstrates a complete **Retrieval-Augmented Generation (RAG)** pipeline using **Google Gemini**, **LangChain**, and **ChromaDB**.

The system allows users to upload or provide documents, converts them into semantic embeddings, stores them in a vector database, retrieves the most relevant information for a query, and generates context-aware responses using Gemini.

Unlike traditional chatbots, this RAG system grounds its answers in the provided documents, reducing hallucinations and improving factual accuracy.

---

## ✨ Features

✅ Document Loading and Processing

✅ Intelligent Text Chunking

✅ Google Gemini Embeddings

✅ ChromaDB Vector Storage

✅ Semantic Similarity Search

✅ Retrieval-Augmented Generation (RAG)

✅ Gemini 2.5 Flash Integration

✅ Interactive Gradio Interface

✅ Context-Aware Question Answering

✅ Modular and Easy-to-Extend Architecture

---

## 🏗️ Architecture

```text
┌──────────────────┐
│   Input Document │
└─────────┬────────┘
          │
          ▼
┌──────────────────┐
│ Document Loader  │
└─────────┬────────┘
          │
          ▼
┌──────────────────┐
│ Text Splitter    │
│ Chunk Size: 500  │
│ Overlap: 200     │
└─────────┬────────┘
          │
          ▼
┌─────────────────────────┐
│ Gemini Embeddings       │
│ gemini-embedding-001    │
└─────────┬───────────────┘
          │
          ▼
┌──────────────────┐
│ ChromaDB         │
│ Vector Store     │
└─────────┬────────┘
          │
          ▼
┌──────────────────┐
│ Retriever        │
└─────────┬────────┘
          │
          ▼
┌──────────────────┐
│ Gemini 2.5 Flash │
└─────────┬────────┘
          │
          ▼
┌──────────────────┐
│ Final Response   │
└──────────────────┘
```

---

# 🛠️ Tech Stack

| Component       | Technology                     |
| --------------- | ------------------------------ |
| LLM             | Gemini 2.5 Flash               |
| Embeddings      | Gemini Embedding 001           |
| Framework       | LangChain                      |
| Vector Database | ChromaDB                       |
| Interface       | Gradio                         |
| Language        | Python                         |
| Document Loader | TextLoader                     |
| Chunking        | RecursiveCharacterTextSplitter |

---

# 📂 Project Structure

```text
project/
│
├── RAG_Implementation.ipynb
├── harrypotter.txt
├── requirements.txt
├── README.md
│
└── assets/
```

---

# ⚙️ Installation

### Clone Repository

```bash
git clone https://github.com/yourusername/gemini-rag-assistant.git

cd gemini-rag-assistant
```

### Install Dependencies

```bash
pip install -qU langchain-google-genai
pip install -qU langchain-community
pip install -qU langchain
pip install chromadb
pip install gradio
```

---

# 🔑 Setup API Key

Create a Google AI Studio API Key:

https://aistudio.google.com/

Set the key:

```python
import os

os.environ["GOOGLE_API_KEY"] = "YOUR_API_KEY"
```

---

# 📥 Document Loading

The project currently supports:

* TXT files
* PDF files (commented support available)

```python
loader = TextLoader(filepath)

# PDF Support
# loader = PyPDFLoader(filepath)
```

---

# ✂️ Text Chunking Strategy

To improve retrieval performance, documents are divided into overlapping chunks.

```python
RecursiveCharacterTextSplitter(
    chunk_size=500,
    chunk_overlap=200
)
```

### Why Overlapping Chunks?

* Preserves context
* Improves retrieval quality
* Reduces information loss
* Better semantic matching

---

# 🧠 Embedding Generation

Document chunks are converted into vector embeddings using:

```python
GoogleGenerativeAIEmbeddings(
    model="gemini-embedding-001",
    task_type="retrieval_document"
)
```

These embeddings capture semantic meaning rather than simple keyword matching.

---

# 🗄️ Vector Database

The project uses **ChromaDB** as the vector store.

```python
vectorstore = Chroma.from_documents(
    documents=splits,
    embedding=embeddings
)
```

Benefits:

* Fast retrieval
* Lightweight
* Open-source
* Easy integration with LangChain

---

# 🔍 Retrieval Process

When a user asks a question:

1. Query is converted into embeddings
2. Similar document chunks are retrieved
3. Relevant context is extracted
4. Context is sent to Gemini
5. Grounded answer is generated

```python
retriever = vectorstore.as_retriever()
```

---

# 🤖 Prompt Engineering

The RAG system uses a focused prompt:

```python
Answer the question based only on the following context:

{context}

Question:
{question}

Helpful Answer:
```

This ensures the model answers strictly from retrieved information.

---

# 💬 Question Answering

Example:

```python
message = input("Ask Question: ")

output = rag_chain.invoke(message)

print(output)
```

### Sample Query

```text
Who is Harry Potter?
```

### Sample Response

```text
Harry Potter is the main protagonist...
```

---

# 🌐 Gradio Interface

A simple Gradio UI is included for interactive usage.

```python
import gradio as gr
```

Benefits:

* User-friendly
* Browser-based
* No frontend coding required
* Quick deployment

---

# 🚀 Running the Project

```bash
jupyter notebook
```

Open:

```text
RAG_Implementation.ipynb
```

Run all cells.

Then ask questions about your document.

---

# 📊 Workflow Summary

```text
Load Document
      ↓
Split into Chunks
      ↓
Create Embeddings
      ↓
Store in ChromaDB
      ↓
Retrieve Relevant Context
      ↓
Generate Answer with Gemini
      ↓
Display Response
```

---

# 🎯 Learning Outcomes

This project demonstrates:

* Retrieval-Augmented Generation (RAG)
* Vector Databases
* Semantic Search
* Embeddings
* Prompt Engineering
* LangChain Pipelines
* Gemini API Integration
* Gradio Deployment

---

# 🔮 Future Improvements

* Multi-document support
* PDF ingestion
* Metadata filtering
* Chat memory
* Source citations
* Hybrid search (BM25 + Vector Search)
* Streaming responses
* Persistent vector storage
* Conversation history
* Enterprise RAG capabilities

---

# 🤝 Contributing

Contributions are welcome.

1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Open a Pull Request

---

# ⭐ If You Found This Useful

Consider giving the repository a star.

It helps others discover the project and supports future development.

---

## Author

Developed as a practical implementation of **Retrieval-Augmented Generation (RAG)** using **Google Gemini, LangChain, ChromaDB, and Gradio**.
