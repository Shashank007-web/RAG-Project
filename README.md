RAG Document Q&A System
An advanced Retrieval-Augmented Generation (RAG) system that enables intelligent question-answering over PDF documents using Google's Gemini 2.0 Flash model, vector embeddings, and adaptive query routing strategies.
🎯 Project Description
This application implements a sophisticated RAG pipeline that goes beyond simple vector similarity search. It intelligently analyzes incoming queries to determine their complexity and automatically selects the optimal retrieval strategy:

Direct Retrieval: For simple, straightforward questions
Decomposed Retrieval: Breaks complex queries into sub-queries for comprehensive answers
Hierarchical Retrieval: Uses iterative refinement for analytical questions

The system features a modern React frontend with real-time chat interface and a FastAPI backend powered by ChromaDB for vector storage, sentence-transformers for embeddings, and Gemini AI for answer generation.
✨ Features

📄 PDF Upload & Processing: Automatic text extraction and intelligent chunking with overlap
🧠 Smart Query Analysis: Automatic detection of query complexity (simple, complex, multi-hop, analytical)
🔀 Adaptive Routing: Dynamic selection of retrieval strategy based on query type
🔍 Vector Search: Semantic search using sentence-transformers embeddings
📊 Re-ranking: Hybrid scoring combining semantic similarity and keyword matching
💬 Chat Interface: Clean, intuitive UI with message history and source citations
📈 Metadata Tracking: Detailed query analysis metrics and retrieval statistics

🏗️ Architecture
Backend Components

Query Analyzer: Classifies queries and determines routing strategy
Query Decomposer: Breaks complex queries into manageable sub-queries using Gemini
Hybrid Retriever: Performs vector similarity search using ChromaDB
Re-Ranker: Improves result relevance through hybrid scoring
RAG Pipeline: Orchestrates the entire retrieval and generation process

Frontend Components

React-based single-page application
Real-time file upload with progress feedback
Chat-style Q&A interface with user/assistant avatars
Source citation display
Query metadata visualization

🚀 Getting Started
Prerequisites

Python 3.8+
Node.js 14+
Google Gemini API key

Backend Setup

Clone the repository:

bashgit clone <your-repo-url>
cd <repo-name>

Install Python dependencies:

bashpip install fastapi uvicorn[standard] python-multipart pydantic
pip install PyPDF2
pip install google-generativeai sentence-transformers chromadb
pip install python-dotenv numpy

Create a .env file in the root directory:

GEMINI_API_KEY=your_gemini_api_key_here

Run the backend server:

bash# If using the Jupyter notebook
jupyter notebook main.ipynb
# Run all cells up to and including Cell 13

# Or create a standalone Python script from the notebook cells
The backend will start on http://localhost:8000
Frontend Setup

Navigate to the frontend directory:

bashcd frontend

Install dependencies:

bashnpm install

Install required packages:

bashnpm install lucide-react

Start the development server:

bashnpm start
The frontend will open at http://localhost:3000
📖 Usage

Upload a PDF: Click "Choose File" and select a PDF document, then click "Upload"
Wait for Processing: The system will extract text, create embeddings, and store them in the vector database
Ask Questions: Type your question in the input box and press Enter or click "Send"
View Results: See the AI-generated answer along with:

Source chunks from the document
Query analysis metadata (type, strategy, complexity)
Number of chunks used



🛠️ API Endpoints

POST /upload - Upload and process a PDF document
POST /query - Query a processed document
GET /documents - List all uploaded documents
DELETE /document/{document_id} - Delete a document
GET /health - Health check endpoint
GET /docs - Interactive API documentation (Swagger UI)

🧪 Example Queries
Simple Query:

"What is the main topic of this document?"

Complex Query:

"Compare the advantages and disadvantages mentioned in the document"

Multi-hop Query:

"What are the key findings and how do they impact future research?"

Analytical Query:

"Analyze the methodology used in this research and explain how it differs from traditional approaches while considering the limitations discussed"

🔧 Configuration
Chunking Parameters

chunk_size: 500 words (default)
overlap: 50 words (default)

Retrieval Parameters

Direct: 5 results → reranked to top 3
Decomposed: 3 results per sub-query → reranked to top 5
Hierarchical: 10 initial → 5 refined → reranked to top 4

Model Configuration

Embedding Model: all-MiniLM-L6-v2
Generation Model: gemini-2.0-flash-exp

🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

🙏 Acknowledgments
Google Gemini AI for natural language generation
Sentence-Transformers for embedding models
ChromaDB for vector storage
FastAPI for the backend framework
React and Lucide React for the frontend

📧 Contact
For questions or feedback, please open an issue on GitHub.
