# 📄 Summarize Private Documents using RAG, LangChain, and LLMs

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![LangChain](https://img.shields.io/badge/LangChain-v0.1-green)
![IBM watsonx.ai](https://img.shields.io/badge/IBM%20watsonx.ai-Powered-purple)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 📌 Project Overview

This project demonstrates how to build a **Retrieval-Augmented Generation (RAG)** application capable of reading, summarizing, and answering questions from private documents (e.g., company policies) that a standard Large Language Model (LLM) would not know about.

It addresses the common challenge of LLMs having outdated knowledge or lacking access to private, proprietary data. By implementing a RAG pipeline, this tool retrieves relevant context from your documents and uses it to generate accurate, evidence-based answers.

## 🤖 Key Features

- **Document Ingestion:** Automatically downloads and processes private text documents (e.g., Company Policies).
- **Smart Chunking:** Uses LangChain's `CharacterTextSplitter` to break large documents into manageable 1000-character chunks for efficient processing.
- **Vector Search:** Converts text into vector embeddings using `HuggingFaceEmbeddings` and stores them in **ChromaDB** for fast retrieval.
- **Hallucination Prevention:** Includes custom `PromptTemplate` engineering to ensure the model says "I don't know" instead of inventing answers when data is missing.
- **Conversational Memory:** Implements `ConversationBufferMemory`, allowing the chatbot to remember context from previous questions (e.g., understanding what "it" refers to).
- **Interactive Agent:** Features a loop that allows continuous interaction with the document until the user types "quit".

## 🛠️ Tech Stack

- **Language:** Python 3
- **Orchestration:** [LangChain](https://www.langchain.com/)
- **LLM Provider:** [IBM watsonx.ai](https://www.ibm.com/products/watsonx-ai)
  - *Models used:* `ibm/granite-3-3-8b-instruct` and `google/flan-ul2`
- **Embeddings:** Hugging Face (`sentence-transformers`)
- **Vector Database:** [ChromaDB](https://www.trychroma.com/)
- **Utilities:** `wget` (for data downloading)

## 🚀 How It Works

1.  [cite_start]**Ingest:** The app downloads a raw text file (`companyPolicies.txt` [cite: 31]).
2.  [cite_start]**Split:** The text is split into chunks to fit within the model's context window[cite: 36].
3.  [cite_start]**Embed:** Chunks are converted into vectors and stored in ChromaDB[cite: 42].
4.  **Retrieve:** When you ask a question, the system finds the most relevant chunks.
5.  **Generate:** The LLM uses those chunks to answer your question accurately.

## 📦 Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR-USERNAME/summarize-private-docs-rag.git](https://github.com/YOUR-USERNAME/summarize-private-docs-rag.git)
    cd summarize-private-docs-rag
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    *(See `requirements.txt` for specific versions of `langchain`, `ibm-watsonx-ai`, `chromadb`, etc.)*

3.  **Configure API Keys:**
    - If running locally, you need an IBM Cloud API key and Project ID.
    - [cite_start]Open the notebook and update the `credentials` dictionary[cite: 48]:
      ```python
      credentials = {
          "url": "[https://us-south.ml.cloud.ibm.com](https://us-south.ml.cloud.ibm.com)",
          "api_key": "YOUR_IBM_API_KEY" # Uncomment and add your key
      }
      project_id = "YOUR_PROJECT_ID"
      ```

4.  **Run the Notebook:**
    Launch Jupyter Lab or Notebook:
    ```bash
    jupyter lab "Summarize private documents using RAG LangChain and LLMs.ipynb"
    ```

## 📊 Usage Examples

**Scenario 1: Fact Retrieval**
> **User:** "What is the smoking policy?"
>
> **AI:** "Smoking is only permitted in designated smoking areas... Smoking inside company buildings is strictly prohibited."

**Scenario 2: Handling Unknowns (Prompt Engineering)**
> **User:** "Can I eat in company vehicles?"
>
> **AI:** "I don't know... The document does not mention eating in vehicles." *(Prevents hallucination)*

**Scenario 3: Conversational Memory**
> **User:** "What is the mobile policy?"
> **AI:** "It outlines standards for responsible mobile usage..."
>
> **User:** "List points in it." *(The AI remembers "it" refers to the mobile policy)*
> **AI:** "1. Acceptable Use, 2. Security, 3. Confidentiality..."

## 🤝 Acknowledgments

This project is based on a lab from the **IBM RAG and Agentic AI Professional Certificate** on Coursera/IBM Skills Network.
