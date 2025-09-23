# Enhanced Web Scraping & RAG Workflow (n8n + Supabase + Mistral)

This workflow automates **web scraping, processing, vector storage, and RAG-powered chatbot responses**.  
It is built in **n8n**, using **Firecrawl** for crawling, **Supabase** for vector storage, and **Mistral embeddings** for semantic search.

---

## 🚀 Features

### 1. **Configuration & Triggers**
- Manual trigger or Webhook trigger (`/webhook-scrape-trigger`)
- Adjustable parameters:  
  - `max_pages` (crawl depth limit)  
  - `chunk_size` (text chunk length)  
  - `chunk_overlap` (overlapping context)

### 2. **Web Scraping (Firecrawl)**
- Smart crawl filtering (skips admin/media/login paths)
- Depth control & timeout handling
- Returns structured markdown for each page

### 3. **Processing Intelligence**
- Filters out low-quality or duplicate content
- Cleans whitespace, formatting, and line breaks
- Extracts titles & counts words
- Tracks metadata for every document

### 4. **Smart Chunking**
- Paragraph-aware splitting with overlap
- Configurable chunk sizes
- Tracks `chunk_index`, `total_chunks`, and timestamps

### 5. **Vector Storage (Supabase)**
- Embeddings generated via **Mistral Cloud**
- Inserted into `rag_markdown_enhanced` table
- Metadata stored alongside embeddings:
  - `source_url`, `title`, `chunk_index`, `total_chunks`, `processed_at`, `word_count`

### 6. **Summary Alerts**
- After each run:
  - Pages scraped  
  - Documents processed  
  - Chunks created  
  - Completion timestamp  
- Delivered via **Telegram bot**

### 7. **RAG Chatbot**
- Enhanced AI Agent with:
  - OpenRouter LLM (Llama 3.1 70B)  
  - Supabase vector search (`semantic_search_enhanced`)  
  - Query embeddings with Mistral  
  - Reranking & context-aware responses  
  - Source attribution in answers

---

## 🛠️ Tech Stack
- **n8n** (workflow engine)
- **Firecrawl API** (web scraping)
- **Supabase + pgvector** (vector storage)
- **Mistral Cloud** (embeddings)
- **OpenRouter API** (LLM responses)
- **Telegram API** (alerts & chatbot interface)

---

## ⚙️ Setup

### 1. Supabase
```sql
create extension if not exists vector;

create table rag_markdown_enhanced (
    id bigserial primary key,
    page_content text not null,
    source_url text not null,
    title text,
    chunk_index int,
    total_chunks int,
    word_count int,
    processed_at timestamptz,
    embedding vector(1024)
);

-- Semantic search function
create or replace function semantic_search_enhanced(
  query_embedding vector(1024),
  match_count int default 5,
  filter jsonb default '{}'
) returns table (
  id bigint,
  page_content text,
  source_url text,
  title text,
  chunk_index int,
  total_chunks int,
  word_count int,
  processed_at timestamptz,
  similarity float
) language plpgsql as $$
begin
  return query
  select
    id,
    page_content,
    source_url,
    title,
    chunk_index,
    total_chunks,
    word_count,
    processed_at,
    1 - (embedding <=> query_embedding) as similarity
  from rag_markdown_enhanced
  order by embedding <=> query_embedding
  limit match_count;
end;
$$;
2. Environment Variables
ini
Copy code
N8N_PORT=5678
SUPABASE_URL=...
SUPABASE_KEY=...
MISTRAL_API_KEY=...
OPENROUTER_API_KEY=...
TELEGRAM_API_KEY=...
3. Run
bash
Copy code
docker compose up -d
Access at http://localhost:5678

📊 Workflow Overview
Crawl Website → Firecrawl

Check Crawl Status → Waits until complete

Process & Filter Content → Cleans & extracts

Smart Chunking → Splits into vector-friendly units

Generate Embeddings → Mistral API

Store Vectors → Supabase with metadata

Scraping Summary → Telegram notification

Enhanced Chatbot → Ask questions via Telegram, powered by RAG

✅ Use Cases
Knowledge base ingestion

Website monitoring

Semantic FAQ chatbot

RAG pipeline prototype

yaml
Copy code
