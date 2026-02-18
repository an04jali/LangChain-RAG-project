# 📚 Simple RAG App (LangChain + FAISS + HuggingFace)

A simple **Retrieval Augmented Generation (RAG)** project that scrapes data from a website, converts it into embeddings, stores it in a vector database (FAISS), and allows querying the data using semantic search.

This project demonstrates **GenAI + LangChain + Vector Database pipeline** end-to-end.

---

## 🚀 Features

* 🌐 Web scraping using LangChain `WebBaseLoader`
* ✂️ Text chunking using `RecursiveCharacterTextSplitter`
* 🧠 Embeddings using **HuggingFace (Free & Offline)**
* 🗂 Vector storage using **FAISS**
* 🔍 Semantic search / document retrieval
* ⚡ Fully local (no OpenAI billing required)

---

## 🧠 Tech Stack

* Python
* LangChain
* FAISS (Vector Database)
* HuggingFace Sentence Transformers
* BeautifulSoup (Web scraping)
* Jupyter Notebook

---

## 📂 Project Structure

```
SimpleApp/
│── simpleApp.ipynb
│── requirements.txt
│── README.md
│── .env   (not pushed to GitHub)
```

---

## ⚙️ Installation

### 1. Clone repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
cd SimpleApp
```

### 2. Create virtual environment (optional)

```bash
python -m venv venv
venv\Scripts\activate   # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ How It Works

### Step 1 — Scrape data from website

```python
from langchain_community.document_loaders import WebBaseLoader

loader = WebBaseLoader("https://example.com")
docs = loader.load()
```

---

### Step 2 — Split text into chunks

```python
from langchain_text_splitters import RecursiveCharacterTextSplitter

splitter = RecursiveCharacterTextSplitter(chunk_size=1000, chunk_overlap=200)
documents = splitter.split_documents(docs)
```

---

### Step 3 — Create embeddings (FREE)

```python
from langchain_community.embeddings import HuggingFaceEmbeddings

embeddings = HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2")
```

---

### Step 4 — Store in FAISS vector DB

```python
from langchain_community.vectorstores import FAISS

db = FAISS.from_documents(documents, embeddings)
```

---

### Step 5 — Retrieve relevant documents

```python
retriever = db.as_retriever()
results = retriever.get_relevant_documents("Your question here")
print(results[0].page_content)
```

---

## 📦 Requirements

Main dependencies:

* langchain
* langchain-community
* langchain-text-splitters
* faiss-cpu
* sentence-transformers
* beautifulsoup4

