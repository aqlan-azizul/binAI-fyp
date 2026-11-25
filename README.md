# binAI-fyp
AI-powered maintenance reporting and payment claim system using Watermark OCR (PaddleOCR), Address-Temporal-Visual task clustering, VLM Before–During–After captioning, and Hybrid RAG over local authority service catalogs. Built with Next.js, FastAPI, and Supabase (pgvector).

# BinAI — Intelligent Maintenance Reporting & Payment Claim System

An end-to-end AI-assisted web application developed in collaboration with **MDN Construction Sdn. Bhd.** (WIA3002/WIA3003 Academic Project, FCSIT Universiti Malaya) to automate local authority (*Pihak Berkuasa Tempatan*) maintenance pictorial reporting and monthly payment claim preparation.

## Core Pipeline
1. **Watermark OCR & Address Normalization:** Extracts burned-in timestamps, Malaysian postcodes, and normalized street addresses from mobile site photos using `PaddleOCR` (`PP-OCRv5`).
2. **Multi-Signal Task Clustering:** Groups photos into a `Project → Task` hierarchy via normalized address similarity, temporal windows (`Δt ≤ 4h`), and `CLIP` visual embeddings.
3. **BDA Selection & Captioning:** Uses `Gemini Flash` (schema-constrained JSON) to recommend *Before–During–After* photo slots and generate editable engineering captions.
4. **Template Pictorial Reporting:** Compiles standardized `.PDF` and `.DOCX` pictorial reports.
5. **Hybrid RAG Claim Mapping:** Combines `pgvector` dense semantic search and `BM25` lexical retrieval (Reciprocal Rank Fusion) to match completed tasks against local authority Service Catalogs (*Jadual Kadar Harga*) inside an editable `.XLSX` claim grid.

## Tech Stack
- **Frontend:** Next.js (App Router), TypeScript, Tailwind CSS, TanStack Table
- **Backend & AI:** Python FastAPI, PaddleOCR, Sentence-Transformers (CLIP), Google GenAI SDK
- **Database & Storage:** Supabase (PostgreSQL 16 + `pgvector`, Storage)

## Repository Structure
- `/notebooks` — Google Colab prototypes and Chapter 6 evaluation experiments
- `/backend` — FastAPI AI inference microservices and document compilers
- `/frontend` — Next.js role-based web application (Admin, Site Supervisor, Company Management)
