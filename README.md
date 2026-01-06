# Multi-Agent Research System

A sophisticated multi-agent system (MAS) built using LangGraph framework for answering complex research queries through a coordinated pipeline of specialized AI agents.

## 🏛️ Project Architecture

This system implements a graph-based architecture with five specialized agents working in sequence:

### Agent Pipeline

1. **Query Planner Agent**

   - Receives and analyzes user queries
   - Uses Tree of Thought (ToT) prompting to decompose complex queries into atomic questions
   - Determines optimal retrieval strategy (internal vector search, web search, or both)

2. **Retriever Agent**

   - Executes conditional information retrieval based on planner's strategy
   - Retrieves internal documents from ChromaDB vector store
   - Accesses external information via Tavily web search tool

3. **Synthesizer Agent**

   - Integrates and aligns retrieved context from multiple sources
   - Filters and compares internal and external information
   - Synthesizes comprehensive draft answers

4. **Reviewer Agent**

   - Performs quality control and fact-checking
   - Validates factual consistency against retrieved context
   - Computes faithfulness score (0.0 to 1.0)

5. **Writer Agent**
   - Formats reviewed content into professional reports
   - Generates structured Markdown output with citations
   - Includes confidence scores and source references

## 🚀 Tech Stack

- **Graph Framework:** LangGraph
- **LLM:** Llama 3.1 (8B Instant) via Groq API
- **Vector Database:** ChromaDB
- **Embedding Model:** HuggingFace "all-MiniLM-L6-v2" (local)
- **Web Search:** Tavily AI
- **Core Libraries:** LangChain, Python
- **Development Environment:** Google Colab / VS Code

## 📊 RAG Features

### Advanced Chunking Strategies

The system demonstrates three different document chunking approaches:

1. **Recursive Character Text Splitter**

   - Chunk size: 500 characters
   - Overlap: 50 characters
   - Best for: General purpose document processing

2. **Sentence Transformers Token Text Splitter**

   - Tokens per chunk: 100
   - Overlap: 20 tokens
   - Best for: Token-aware processing

3. **Agentic Chunking (LLM-based)**
   - Intelligent topic-based segmentation
   - Uses LLM to identify natural content boundaries
   - Best for: Complex documents requiring semantic understanding

## ⚙️ Setup and Installation

### Prerequisites

- Python 3.8+
- API Keys:
  - **GROQ_API_KEY** (for Llama 3.1 model)
  - **TAVILY_API_KEY** (for web search)

### Installation

1. **Clone the repository**

   ```bash
   git clone <your-repo-url>
   cd <project-directory>
   ```

2. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**

   Create a `.env` file in the project root:

   ```env
   GROQ_API_KEY=your_groq_api_key_here
   TAVILY_API_KEY=your_tavily_api_key_here
   ```

4. **Add internal documents**

   Place your internal documents (.pdf, .txt, .doc, .docx) in the `internal_docs/` folder:

   ```
   internal_docs/
   ├── document1.pdf
   ├── document2.txt
   └── document3.docx
   ```

## ▶️ How to Run

### In Google Colab

1. Upload the notebook to Google Colab
2. Run all cells sequentially from top to bottom
3. Enter your API keys when prompted
4. Provide your research query in the final cell

### In VS Code / Local Environment

1. Open the notebook in VS Code with Jupyter extension
2. Activate the virtual environment:

   ```bash
   # On Windows
   myenv\Scripts\activate

   # On Linux/Mac
   source myenv/bin/activate
   ```

3. Run cells sequentially
4. Enter your query when prompted

### Example Queries

```
1. Tell me the process of how a Machine learning model can differentiate between different patterns with the help of neural networks?

2. How is CNN used for image processing?

3. Compare transfer learning approaches in computer vision and NLP.
```

## 📁 Project Structure

```
.
├── Multi_Agent_Research_Architecture.ipynb  # Main notebook
├── requirements.txt                                      # Python dependencies
├── .env                                                  # API keys (not committed)
├── .gitignore                                           # Git ignore rules
├── internal_docs/                                       # Internal knowledge base
│   ├── document1.pdf
│   └── document2.txt
├── myenv/                                               # Virtual environment (not committed)
└── README.md                                            # This file
```

## 🔍 How It Works

1. **User submits a query** via the final execution cell
2. **Planner** decomposes the query and selects retrieval strategy
3. **Retriever** fetches relevant information from internal docs and/or web
4. **Synthesizer** creates a coherent draft answer from all sources
5. **Reviewer** validates factual accuracy and assigns confidence score
6. **Writer** formats the final report with proper citations and structure

## 📊 Output Format

The system generates a structured Markdown report with:

- **Executive Summary:** Concise overview
- **Detailed Findings:** Comprehensive analysis with headings
- **Confidence Score:** Percentage-based faithfulness metric
- **Sources:** Citations from internal docs and web results
- **References:** Full reference list

## 🛠️ Troubleshooting

### Common Issues

1. **API Key Errors**

   - Ensure `.env` file is in the project root
   - Verify keys are correctly formatted
   - Check API quota/limits

2. **No Internal Documents Found**

   - Verify files are in `internal_docs/` folder
   - Check file formats (.pdf, .txt, .doc, .docx)
   - Ensure files are readable

3. **Agentic Chunking Failures**
   - Normal for complex PDFs with special characters
   - System falls back to original document
   - Consider using Recursive chunking for reliability

## 📝 License

This project is created for educational and evaluation purposes.

## 👤 Author

**Dibyajyoti Sarkar**

## 🙏 Acknowledgments

- LangChain and LangGraph teams
- Groq for LLM API access
- Tavily for web search capabilities
- Multi-Agent-Research-System"

# Multi-Agent-Research-System
