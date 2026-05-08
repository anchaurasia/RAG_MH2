RAG Chatbot using LangChain + FAISS
📌 Project Overview

This project implements a Retrieval Augmented Generation (RAG) system that answers user queries based on a custom knowledge base (AST-1 & AST-2 documents).

The system retrieves relevant document chunks using semantic search and generates accurate responses using a language model.

🎯 Features
📄 Load PDF documents as knowledge base
✂️ Dynamic text chunking
🔍 Semantic search using embeddings
🧠 Vector database using FAISS
🤖 LLM-based answer generation (FLAN-T5)
🔄 Comparison between:
Basic Retrieval
MMR (Max Marginal Relevance)
🎛️ Interactive Gradio UI
⚙️ Adjustable chunk size (300 / 500 / 800)
🧠 What is RAG?

Retrieval Augmented Generation (RAG) combines:
Retrieval → Fetch relevant context from documents
Generation → Use LLM to generate answers


🏗️ Project Pipeline
PDF Documents
      ↓
Document Loader
      ↓
Text Chunking
      ↓
Embeddings (MiniLM)
      ↓
FAISS Vector Database
      ↓
Retriever (Basic / MMR)
      ↓
LLM (FLAN-T5)
      ↓
Final Answer


⚙️ Tech Stack
LangChain
FAISS
HuggingFace Transformers
Sentence Transformers (MiniLM)
Gradio
Python


📂 Dataset
AST-1 → ML modular pipeline
AST-2 → Testing & packaging
🚀 Installation
git clone https://github.com/anchaurasia/RAG_MH2.git
cd rag-chatbot

python -m venv venv
venv\Scripts\activate

pip install -r requirements.txt
▶️ Run the App
python app.py

or inside notebook:

app.launch()
