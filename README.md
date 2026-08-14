# Apple Innovation & Leadership RAG System

An end-to-end **Retrieval-Augmented Generation (RAG)** pipeline demonstrating semantic search and grounded LLM response generation on corporate strategy documents. This project analyzes the Harvard Business Review article *"How Apple Is Organized for Innovation"* to extract leadership principles, organizational design patterns, and innovation case studies.

---

## 📌 Overview & Objective

As organizations scale, analyzing dense business reports manually becomes a major bottleneck. This application serves as an intelligent assistant for business analysts and VC decision-makers to interactively query complex documents in natural language without manual read-throughs.

---

## 🛠️ Tech Stack & Dependencies

* **Language:** Python
* **Framework:** LangChain (`langchain-openai`, `langchain-community`)
* **LLM & Embeddings:** OpenAI GPT-4o-mini (`gpt-4o-mini`), Text-Embedding-Ada-002 (`text-embedding-ada-002`)
* **Vector Store:** ChromaDB
* **PDF Parser:** PyMuPDF (`fitz`)
* **Tokenizer:** Tiktoken (`cl100k_base`)
* **Evaluation Framework:** RAGAS

---

## 🚀 Key Features & Workflow

1. **Document Ingestion & Boilerplate Removal:**
   * Parsed multi-page PDFs using PyMuPDF.
   * Cleaned repetitive headers, footers, page numbers, and copyright disclaimers using custom regex patterns.
2. **Token-Aware Chunking:**
   * Split document content using `RecursiveCharacterTextSplitter` configured for 256 tokens per chunk with a 20-token overlap for context retention.
3. **Vector Database & Retrieval:**
   * Generated vector embeddings via OpenAI `text-embedding-ada-002`.
   * Indexed and stored vectors in ChromaDB with persistent local storage.
   * Configured top-$k$ similarity retriever ($k=8$) to supply rich context to the LLM.
4. **Prompt Engineering & Grounded Response:**
   * Designed system prompts enforcing strict context adherence ("answer *only* based on the provided context") to prevent hallucinations.
5. **Quantitative Evaluation:**
   * Automated quality scoring using the RAGAS evaluation framework across Faithfulness, Answer Relevancy, Context Precision, and Context Recall.

---

## 📊 RAGAS Evaluation Results

| Metric | Score | Description |
| :--- | :---: | :--- |
| **Faithfulness** | **1.00** | High factual consistency; no LLM hallucinations. |
| **Context Recall** | **1.00** | Retrieved context covers all necessary facts. |
| **Context Precision** | **0.97** | High concentration of relevant chunks in retrieved context. |
| **Answer Relevancy** | **0.96** | Generated responses directly address the questions asked. |

---

## 📁 Repository Structure

```text
├── Inayat_Aziz_Apple_Project_Learners_Notebook_Full_Code.ipynb  # Main Jupyter Notebook
├── README.md                                                     # Project Overview
├── config.example.json                                          # Template for API credentials
└── .gitignore                                                   # Excludes sensitive keys & DB files
