

# Corporate Q&A Bot (Azure AI Search + Azure OpenAI)

A **Retrieval-Augmented Generation (RAG) chatbot** that answers questions from company documents using:

* Azure AI Search for document retrieval
* Azure OpenAI for response generation
* Azure Blob Storage for document storage

The bot searches relevant document chunks and generates answers with **citations from source documents**.

---

# Features

* Document search using **Azure AI Search**
* AI-powered answers using **Azure OpenAI**
* **Streaming responses** in the terminal
* **Source citations** for answers
* Folder-level filtering for documents
* Simple **CLI chatbot interface**
* Secure configuration using `.env`

---

# Architecture

```
User Question
     │
     ▼
Azure AI Search
(Document Retrieval)
     │
     ▼
Top Relevant Document Chunks
     │
     ▼
Azure OpenAI (GPT Model)
     │
     ▼
Generated Answer + Citations
```

This pattern is known as **Retrieval-Augmented Generation (RAG)**.

---

# Project Structure

```
corporate-Q-A-bot
│
├── main.py              # Main chatbot application
├── requirements.txt    # Python dependencies
├── .env                # Environment variables (not committed)
├── .gitignore          # Ignore secrets & venv
└── README.md           # Project documentation
```

---

# Prerequisites

Before running the project, you need:

* Python 3.10+
* Azure Account
* Azure AI Search Service
* Azure OpenAI Resource
* Azure Blob Storage

---

# Azure Services Required

1. **Azure AI Search**

Create an index containing:

* `content`
* `metadata_storage_path`

2. **Azure OpenAI**

Deploy a chat model such as:

* `gpt-4o`
* `gpt-4`
* `gpt-35-turbo`

3. **Azure Blob Storage**

Upload documents into a container folder such as:

```
container-name/
    Kenneth/
        document1.pdf
        document2.pdf
```

---

# Environment Variables

Create a `.env` file in the project root.

```
AZURE_SEARCH_ENDPOINT=https://your-search-service.search.windows.net
AZURE_SEARCH_INDEX_NAME=your-index-name
AZURE_SEARCH_API_KEY=your-search-key

AZURE_OPENAI_ENDPOINT=https://your-openai-resource.openai.azure.com
AZURE_OPENAI_API_KEY=your-openai-key
AZURE_OPENAI_DEPLOYMENT_NAME=your-model-deployment
AZURE_OPENAI_API_VERSION=2024-02-01

AZURE_STORAGE_ACCOUNT_URL=https://yourstorageaccount.blob.core.windows.net
BLOB_CONTAINER_NAME=your-container
```

---

# Installation

Clone the repository from GitHub

```bash
git clone https://github.com/your-username/corporate-Q-A-bot.git
cd corporate-Q-A-bot
```

Create a virtual environment

```bash
python -m venv .venv
```

Activate the environment

Windows

```bash
.venv\Scripts\activate
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

# Running the Bot

Start the chatbot

```bash
python main.py
```

Example terminal:

```
💬 CORPORATE Q&A BOT

You: What are the main company policies?

🤖 Bot:
The main policies include workplace conduct, data protection,
and employee responsibilities. [Source: policy.pdf]
```

Exit the bot anytime using:

```
exit
```

or

```
quit
```

---

# Example Query

```
What are the security policies mentioned in the Kenneth documents?
```

The bot will:

1. Search Azure AI Search
2. Retrieve document chunks
3. Send context to Azure OpenAI
4. Generate an answer with citations

---

# Security Notes

Never commit the following files:

```
.env
.venv
API keys
```

Use `.gitignore` to exclude them.

---

# Future Improvements

* Web UI using **Streamlit**
* Vector search for better retrieval
* Conversation memory
* PDF highlighting for citations
* Deployment to Azure App Service

---

# License

This project is provided for educational and experimental purposes.

