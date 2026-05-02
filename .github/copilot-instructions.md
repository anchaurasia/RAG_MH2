# RAG System Development Guide

## Project Overview
This is a Retrieval-Augmented Generation (RAG) system built with LangChain, using FAISS for vector storage, HuggingFace models for embeddings and generation, and Gradio for the user interface. Data sources are PDF documents stored in the `data/` directory.

## Core Architecture
- **Data Ingestion**: Load PDFs using `PyPDFLoader` from `langchain_community.document_loaders`
- **Text Processing**: Split documents with `RecursiveCharacterTextSplitter` from `langchain_text_splitters`
- **Embeddings**: Generate vectors using `HuggingFaceEmbeddings` with sentence-transformers models
- **Vector Storage**: Store and search vectors with `FAISS` from `langchain_community.vectorstores`
- **Retrieval Chain**: Use `RetrievalQA` from `langchain.chains` for question-answering
- **UI**: Build interface with Gradio for document querying

## Key Patterns
- Use pinned package versions: `transformers==4.38.2` for compatibility
- Store PDF files in `data/` directory with descriptive names (e.g., `AST-1.pdf`, `AST-2.pdf`)
- Configure embeddings with `model_name="sentence-transformers/all-MiniLM-L6-v2"` for efficient retrieval
- Implement chunking with `chunk_size=1000, chunk_overlap=200` for optimal text splitting
- Use FAISS for local vector storage to avoid external dependencies

## Development Workflow
- Set up virtual environment: `python -m venv venv`
- Install dependencies from notebook cell 2 (includes langchain ecosystem, faiss-cpu, sentence-transformers, pypdf, gradio)
- Run notebook cells sequentially to initialize environment
- Build RAG pipeline: load docs → split text → create embeddings → store in FAISS → create retrieval chain → launch Gradio interface

## Code Structure
- Keep data processing and model logic in separate functions
- Use LangChain's `Document` objects for text chunks with metadata
- Implement error handling for PDF loading and embedding generation
- Cache FAISS index to disk for faster reloads using `save_local()` and `load_local()`

## Integration Points
- HuggingFace models: Use `HuggingFacePipeline` for text generation with local models
- Gradio interface: Expose query endpoint with `gr.Interface` for user interactions
- File system: Read PDFs from `data/` directory, save FAISS index to local files