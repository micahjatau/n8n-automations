# 💬 Case Study: Automated Web Scraping with RAG & Supabase

## 🎯 Problem

The client needed an automated way to:

- Scrape markdown content from websites  
- Clean and structure that content  
- Enable retrieval-augmented generation (RAG) search  
- Run everything with minimal manual effort  

---

## 🧪 Solution

Built an end-to-end workflow using:

- Firecrawl for deep site scraping  
- n8n for orchestrating the flow  
- Mistral Cloud for generating dense vector embeddings  
- Supabase for vector DB and semantic search  
- Telegram Bot for real-time updates  

---

## 🔧 Improvements

- Smart chunking by paragraphs  
- Vector search with top-k reranking  
- Telegram summary alerts for completed runs  
- Metadata-enriched storage for analytics  

---

## 🧠 RAG Enhancements

- Each query generates a Mistral embedding  
- Vector match using `semantic_search_enhanced` Supabase function  
- Chatbot powered by OpenRouter LLM (e.g., Llama 3.1 70B)  
- Answers grounded with source attribution  

---

## 📈 Results

| Metric             | Value          |
|--------------------|----------------|
| Pages scraped      | 5              |
| Docs processed     | 4              |
| Vector chunks made | 27             |
| Response time      | ~1 minute/run  |
| Error retries      | ✅ Built-in     |
| Chatbot readiness  | ✅ Enabled      |

---

## 🔮 Next Steps

- Schedule recurring crawls (e.g. monthly)  
- Ingest PDFs & CSVs  
- Add recency filtering (`processed_at DESC`)  
- Build caching layer for repeated queries  

---

## 👨‍💻 Credits

Micah Jatau – Automation Specialist & Builder  
🔗 [micahjatau.github.io](https://micahjatau.github.io) | [n8n.io](https://n8n.io)
