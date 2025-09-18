# Personal-Document-Assistant-Using-RAG

An AI-powered document helper that allows you to ask questions on Word documents containing text and images. It uses **Retrieval-Augmented Generation (RAG)** to find relevant information in your documents and falls back to OpenAI's language model if the answer is not found.

---

## Features

- Supports **Word documents** (.docx) with **text and images** (OCR included)
- Uses **vector embeddings (OpenAI)** and **Chroma** for semantic search
- **RAG-based QA**: Answers questions grounded in your documents
- **Fallback to OpenAI LLM** if information is not found
- **Interactive Notebook Interface** for testing queries
- **Persistent vector store** for large input documents

<img width="1340" height="865" alt="image" src="https://github.com/user-attachments/assets/1512a48b-b967-4ace-858e-9e743a5cbf4f" />

---

## Installation

```bash
pip install -r requirements.txt
```

Requirements include: langchain, langchain-community, chromadb, openai, pytesseract, python-docx, Pillow, tiktoken, graio (optional)

---

## Usage
1. Place your Word documents in the documents/ folder
2. Run the notebook RAG_Document_Assistant.ipynb
3. Use the interactive input loop in the last cell to ask questions.
4. Enjoy answers grounded in your uploads. In case the answer is not there in the documents, it uses general LLM to predict an answer for you after stating it is not coming directly from the documents.

---

## How it Works
1. Document Ingestion: Reads text and images from the Word docs
2. OCR on images: Extracts text from screenshots using pytesseract
3. Chunking & Embeddings: Splits documents into manageable chunks and converts to embeddings using OpenAI Embeddings.
4. Vector Store: Stores embeddings in Chroma for semantic search. Stores it in a presistent directory so that the Chroma Store can be re-used in a new notebook.
5. RAG + LLM: Retrieves relevant chunks and answers using OpenAI’s GPT, falls back to general LLM answer, if necessary.

---

## Data Engineering Aspect 
This project is not just AI - it demonstarates key data engineering skills as well:
- Data Ingestion and processing: Reading Documents and Extracting Text/Images
- Data Transformation: Chunking and storing the Data as Embeddings in a Vector Store like Chroma.
- Data Storage & retrieval: Persistent Vectore Store with Chroma, for re-usabiltiy and removing the need to convert the document into embeddings every run.
- Efficient Querying: Use of semantic Search to effectively query over document collections.

---

## Optional Enhancements that can be taken up in this
- Multi-format document ingestion (PDF, Markdown, CSV)
- Gradio/Streamlit web interface
- Highlight top-k retrieved chunks with snippets
- Track retriever confidence and fallback behavior
- Visualization of embedding similarities
