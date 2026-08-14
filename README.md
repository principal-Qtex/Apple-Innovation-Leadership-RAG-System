# Apple-Innovation-Leadership-RAG-System
End-to-end Retrieval-Augmented Generation (RAG) pipeline demonstrating semantic search and grounded LLM response generation on corporate strategy documents. Analyzes "How Apple Is Organized for Innovation" (HBR) to extract leadership principles, organizational design patterns, and innovation case studies.

What It Does:

Loads multi-page PDFs and cleans boilerplate text (headers, footers, disclaimers) via regex patterns
Chunks documents using token-aware splitting (256 tokens, 20-token overlap) for optimal retrieval
Generates vector embeddings using OpenAI's text-embedding-ada-002
Stores embeddings in ChromaDB for semantic similarity search
Retrieves top-K relevant chunks and grounds LLM responses in source context
Evaluates RAG quality with RAGAS framework (faithfulness, answer relevancy, context precision/recall)

Key Results:

Question 1 (Authors & Publisher): Correctly identified Joel M. Podolny, Morten T. Hansen, Harvard Business Review
Question 2 (Leadership Characteristics): Extracted Deep Expertise, Immersion in Details, Willingness to Collaboratively Debate
Question 3 (Innovation Examples): Provided specific examples (dual-lens camera collaboration, discretionary leadership model, organizational attention to detail)
RAGAS Metrics: Faithfulness 1.00, Answer Relevancy 0.96, Context Precision 0.97, Context Recall 1.00

Tech Stack: Python, LangChain, ChromaDB, OpenAI API, tiktoken, pandas, RAGAS

Key Notebook Sections:

Data Preparation – PDF loading, text cleaning, boilerplate removal
Chunking & Embedding – Token-aware splitting, OpenAI embeddings, vector storage
Vector Store Setup – ChromaDB initialization and persistence
RAG Inference – System prompt design, retriever + LLM chain
Evaluation – RAGAS quantitative assessment

Learnings:
Demonstrates importance of prompt engineering (system + user message framing) for grounding LLMs. Shows how proper data cleaning and chunking dramatically improves retrieval quality. RAGAS evaluation confirms no hallucinations and high context relevance
