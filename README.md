#  ACity RAG Assistant

**Academic City University — Introduction to AI Project-Exam**

A manually-implemented Retrieval-Augmented Generation (RAG) system for querying Ghana Election Results and the 2025 Budget Statement.

**Live Demo:** *https://ai-10022200095.vercel.app/*
**Video Explanation of App:** *https://drive.google.com/drive/folders/1S0idYCBlq9bQmYCpZeNimvQlrq8V3Ks1?usp=drive_link*
*Refer to documentation.md file for detailed report documentation of the entire project*

---

## Quick Start

### 1. Get a FREE Groq API Key
- Go to [console.groq.com](https://console.groq.com)
- Sign up (free) → API Keys → Create Key
- Copy the key (starts with `gsk_...`)

### 2. Set Up Your Environment
```bash
# Clone the repo
git clone https://github.com/WesTurkson/ai_10022200095.git
cd acicity-rag

# Install dependencies
npm install

# Set your API key
cp .env
# Open .env and replace: VITE_GROQ_API_KEY=your_actual_key_here
```

### 3. Run Locally
```bash
npm run dev
# Open http://localhost:5173
```

---

##  Deploy to Vercel

```bash
# Push to GitHub first
git add .
git commit -m "ACity RAG System"
git push origin main
```

Then:
1. Go to [vercel.com](https://vercel.com) → New Project → Import your GitHub repo
2. Add Environment Variable: `VITE_GROQ_API_KEY` = your key
3. Click Deploy → get your live URL ✅

---

##  Architecture

```
User Query
  → Query Expansion (domain synonyms)
  → TF-IDF Embedding (manual, ~800 vocab terms)
  → Cosine Similarity against 27 knowledge chunks
  → Hybrid Score = 0.7×vector + 0.3×keyword
  → Feedback Boost (session-persistent weights)
  → Prompt Construction (hallucination guards)
  → Groq API (LLaMA3-70B)
  → Response with source citations
```

---

##  Components

| File | Purpose |
|------|---------|
| `src/App.jsx` | Full RAG pipeline + React UI |
| `.env` | Your Groq API key (never commit this) |
| `.env.example` | Template for others to set up |

---

##  Constraints Satisfied

- ❌ No LangChain
- ❌ No LlamaIndex  
- ❌ No pre-built RAG pipelines
- ✅ Manual TF-IDF embedding
- ✅ Custom cosine similarity
- ✅ Manual hybrid search
- ✅ Query expansion
- ✅ Feedback loop (Part G innovation)
- ✅ Logging at every pipeline stage

---

##  Datasets

- `Ghana_Election_Result.csv` — presidential results 1992–2024
- `2025-Budget-Statement.pdf` — Ghana fiscal year 2025 budget

---

*Academic City University | April 2026*
