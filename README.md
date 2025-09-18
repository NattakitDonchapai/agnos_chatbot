# 🤖 Agnos Health Forum Chatbot

This project is a RAG (Retrieval-Augmented Generation) chatbot designed to answer questions based on the knowledge from the Agnos Health forum. It's a submission for the Agnos Data Science assignment (Task 1).

## 🏛️ Architecture

The chatbot operates on a simple yet powerful RAG pipeline:
1.  **Scraper (`scraper.py`):** Fetches forum posts from the Agnos Health website.
2.  **Ingestion (`ingest.py`):** Processes the scraped text, creates vector embeddings using an open-source model, and stores them in a FAISS vector database.
3.  **RAG Core (`rag_core.py`):** When a user asks a question, this module retrieves the most relevant documents from the vector database.
4.  **Application (`app.py`):** A Streamlit web interface that takes user input, passes it to the RAG Core, sends the retrieved context and question to an LLM (via Ollama), and displays the generated answer.

## 🛠️ Tech Stack
* **Web Framework:** Streamlit
* **RAG/LLM Orchestration:** LangChain
* **LLM Serving:** Ollama (with models like LLaMA 3)
* **Vector Database:** FAISS (CPU)
* **Web Scraping:** BeautifulSoup & Requests

## 🚀 How to Run

### Prerequisites
* Python 3.9+
* Git
* Ollama installed and running. Download from [ollama.com](https://ollama.com/).

### 1. Setup
```bash
# Clone the repository
git clone [https://github.com/YOUR_USERNAME/agnos-rag-chatbot.git](https://github.com/YOUR_USERNAME/agnos-rag-chatbot.git)
cd agnos-rag-chatbot

# Install dependencies
pip install -r requirements.txt

# Download the LLM model via Ollama
ollama pull llama3
```

### 2. Run the Pipeline
The pipeline must be run in order.

**Step 1: Scrape the data**
```bash
python scraper.py
```
This will create a `data/` folder with the forum content.

**Step 2: Create the vector database**
```bash
python ingest.py
```
This will create a `vectorstore/` folder with the FAISS index.

**Step 3: Launch the chatbot**
```bash
streamlit run app.py
```
Open your web browser to the local URL provided by Streamlit to start chatting.
