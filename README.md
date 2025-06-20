# Self-RAG-Based-Intelligent-Retrieval-System-with-OpenAI-Embeddings-and-FAISS-Search

A fully local, high-performance Question Answering (QA) system built without LangChain. It uses OpenAI's embedding models to semantically encode document chunks and FAISS to perform lightning-fast similarity search across local `.txt` files. The system retrieves relevant content based on a user's question and generates precise answers using ChatGPT.

---

## 🧠 Why This Project?

This project demonstrates how to build an end-to-end RAG (Retrieval-Augmented Generation) system:
- without relying on external tools like LangChain,
- while leveraging the power of OpenAI’s APIs,
- and maintaining complete control over your data with **local file storage** and **in-memory vector search (FAISS)**.

---
## ✅ Step-by-Step Workflow

### 1. 🔍 Load Local Documents
All `.txt` files from the `docs/` folder are read into memory for processing.

### 2. ✂️ Split Documents into Chunks
Each document is split into smaller overlapping chunks (default: 1000 characters) to preserve context.

### 3. 🔢 Generate Embeddings (OpenAI)
Each chunk is embedded using OpenAI’s `text-embedding-3-small` model, which turns it into a vector that captures its semantic meaning.

### 4. 🧲 Store Embeddings in FAISS
The system builds a FAISS index that stores these vectors and allows fast cosine similarity search to retrieve semantically similar text chunks.

### 5. ❓ User Question Input
The user inputs a natural language question. This is also embedded using the same OpenAI embedding model.

### 6. 🚀 Semantic Retrieval
FAISS compares the question vector to document vectors and returns the top-k most relevant document chunks.

### 7. ✅ Relevance Grading (Optional)
The retrieved chunks are passed to `gpt-4o` to determine if they are actually relevant to the user query — filtering false positives.

### 8. 🧠 Answer Generation
The most relevant chunks are used as context. A prompt is created and sent to `gpt-3.5-turbo` to generate the final answer.




