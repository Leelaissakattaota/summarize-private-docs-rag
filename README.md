# 📄 Summarize Private Documents Using RAG, LangChain & LLMs

![Language](https://img.shields.io/badge/Language-Python%203.11-3776AB?style=flat-square&logo=python&logoColor=white)
![Framework](https://img.shields.io/badge/Framework-LangChain%200.1-FF6B35?style=flat-square)
![LLM](https://img.shields.io/badge/LLM-IBM%20Flan--UL2%20%7C%20Granite%203.3-052FAD?style=flat-square&logo=ibm&logoColor=white)
![VectorDB](https://img.shields.io/badge/VectorDB-ChromaDB-2E7D32?style=flat-square)
![Embeddings](https://img.shields.io/badge/Embeddings-HuggingFace%20SentenceTransformers-FFD21E?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)

## 📌 Project Overview
End-to-end **RAG pipeline for private document Q&A and summarization** using LangChain, IBM Watsonx (Flan-UL2 + Granite 3.3), HuggingFace embeddings, and ChromaDB. Loads a company policy document, splits it into chunks, embeds into a vector store, and answers questions like "What is the mobile policy?" using `RetrievalQA`.

**Domain:** RAG — Private Document Intelligence  
**LLMs:** IBM Flan-UL2 + IBM Granite 3.3 8B (Watsonx)  
**Embeddings:** HuggingFace SentenceTransformers  
**Vector Store:** ChromaDB  

## 🚀 RAG Pipeline
```
companyPolicies.txt
  → TextLoader → CharacterTextSplitter (1000 chars, 0 overlap)
  → HuggingFaceEmbeddings → ChromaDB vector store
  → RetrievalQA (stuff chain) + IBM Watsonx LLM
  → Q&A: "What is mobile policy?" / "Summarize this document"
```

## 🔑 Key Code
```python
# Split
texts = CharacterTextSplitter(chunk_size=1000).split_documents(documents)

# Embed + Store
docsearch = Chroma.from_documents(texts, HuggingFaceEmbeddings())

# RAG Q&A
qa = RetrievalQA.from_chain_type(llm=flan_ul2_llm,
                                  chain_type="stuff",
                                  retriever=docsearch.as_retriever())
qa.invoke("Can you summarize the document for me?")
```

## 🎓 Skills Demonstrated
LangChain RAG · TextLoader + CharacterTextSplitter · HuggingFace embeddings · ChromaDB · RetrievalQA chain · IBM Flan-UL2 + Granite 3.3 · Private document Q&A

## 🤝 Connect
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Leela%20A-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/leela-a)
[![Gmail](https://img.shields.io/badge/Gmail-attotaleelaissak@gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:attotaleelaissak@gmail.com)
