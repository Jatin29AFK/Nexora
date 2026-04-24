# Nexora

<div align="center">

## Retrieval-Augmented AI Study Assistant for PDFs and Web Content

Nexora is a RAG-powered learning workspace that ingests PDFs and web content, retrieves relevant source context for each query, and generates grounded answers and quizzes using Supabase and Groq.

It is built around core **RAG concepts** such as source ingestion, chunking, retrieval, context-grounded generation, answer-mode control, and quiz creation from source-backed study material.

![Frontend](https://img.shields.io/badge/Frontend-React-1f6feb)
![Build](https://img.shields.io/badge/Build-Vite-8b5cf6)
![UI](https://img.shields.io/badge/UI-CSS-06b6d4)
![Backend](https://img.shields.io/badge/Backend-Supabase-16a34a)
![Functions](https://img.shields.io/badge/Functions-Edge%20Functions-0f766e)
![Database](https://img.shields.io/badge/Database-Postgres-334155)
![AI](https://img.shields.io/badge/AI-Groq-f59e0b)
![Concepts](https://img.shields.io/badge/Concepts-RAG-ef4444)
![Deploy](https://img.shields.io/badge/Deploy-Vercel-black)

</div>

---

## Live Demo

https://nexora-one-ashen.vercel.app

---

## Overview

Nexora helps users turn raw study material into a searchable, interactive learning workspace. Users can upload PDFs, add website content, ask grounded questions in different answer styles, and generate quizzes directly from their sources.

Unlike generic chat workflows, Nexora is designed around a **retrieval-first pipeline**, where answers are generated using relevant retrieved context instead of relying only on free-form model output.

---

## Core RAG Concepts Implemented

- **Source Ingestion** — accepts PDFs and web content as input sources
- **Text Extraction** — parses PDF text in the browser and extracts readable content from URLs
- **Chunking** — breaks source content into smaller retrievable units
- **Retrieval** — fetches relevant chunks from stored source material
- **Grounded Generation** — generates answers from retrieved context using Groq
- **Answer Modes** — formats responses differently for revision and study use cases
- **Quiz Generation** — creates source-based quizzes for active recall

---

## Features

- Upload and process PDF study material
- Add website URLs and extract readable content
- Ask grounded questions from uploaded sources
- Multiple answer modes:
  - Balanced
  - Concise
  - Detailed
  - Bullet Summary
  - Beginner Friendly
  - Exam Style
- Suggested questions for faster exploration
- Quiz generation from selected sources
- Quiz scoring, explanations, weak-topic detection, and retake flow
- Anonymous user sessions using Supabase Auth
- Persistent source and chunk storage using Supabase


## Architecture

### Current Live Architecture
- **Frontend:** Vercel
- **Database and backend services:** Supabase
- **AI orchestration:** Supabase Edge Functions + Groq

### Legacy Backend
This repository also contains an earlier **FastAPI-based backend** implementation for reference in `backend-legacy/`.  
The live version of Nexora no longer depends on that backend.


## Tech Stack

### Frontend
- React
- Vite
- JavaScript
- CSS

### Backend / Platform
- Supabase Postgres
- Supabase Edge Functions
- Supabase Auth (Anonymous Sign-In)

### AI / Processing
- Groq API
- Browser-side PDF parsing using `pdfjs-dist`

---

## Project Structure

```text
Nexora/
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
├── supabase/
│   ├── functions/
│   │   ├── ask/
│   │   ├── generate-quiz/
│   │   └── extract-url/
│   └── schema.sql
├── backend-legacy/   # optional legacy FastAPI version
├── .gitignore
├── README.md
└── LICENSE
```

## How It Works
1. User uploads a PDF or adds a URL
2. PDF text is extracted in the browser, while URLs are processed via Supabase Edge Functions
3. The extracted content is stored in Supabase as:
- documents
- chunks
4. User asks a question
5. Relevant chunks are retrieved from Supabase
6. Groq generates a grounded answer using the retrieved context
7. User can also generate quizzes from selected sources


## Screenshots

### 1. Workspace Overview
Nexora provides a clean study workspace where users can upload PDFs, add web sources, ask grounded questions, and generate quizzes from their learning material.

<p align="center">
  <img src="./screenshots/HomePage.png" alt="Nexora Workspace Overview" width="900" />
</p>

### 2. Source Upload and Management
Users can upload PDF documents and add website URLs. Extracted content is stored and organized so the workspace remains ready for question answering and quiz generation.

<p align="center">
  <img src="./screenshots/ChatScreen.png" alt="Source Upload and Management" width="900" />
</p>

### 3. Grounded Question Answering
Nexora supports multiple answer modes and responds using retrieved source context, making the experience more useful for revision and study workflows.

<p align="center">
  <img src="./screenshots/QuizStudio.png" alt="Grounded Question Answering" width="900" />
</p>

### 4. Quiz Studio
Users can generate quizzes from selected sources, attempt them inside the app, and review scores, explanations, and weak topics.

<p align="center">
  <img src="./screenshots/QuizResults.png" alt="Quiz Studio" width="900" />
</p>


## Local Setup
1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/Nexora.git
cd Nexora
```

2. Install frontend dependencies
```bash
cd frontend
npm install
```

3. Create environment variables

Create frontend/.env.local:
```bash
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_publishable_key
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

4. Run the frontend
```bash
npm run dev
```
## Supabase Setup
### Database

Run the SQL from:

supabase/schema.sql

### Edge Functions

Deploy or maintain these functions:

- ask
- generate-quiz
- extract-url

### Required Supabase Secrets
- GROQ_API_KEY
- GROQ_MODEL

## Deployment
### Frontend
- Vercel

### Backend Services
- Supabase Edge Functions
- Supabase Postgres

## Environment Variables
### Frontend
- VITE_SUPABASE_URL
- VITE_SUPABASE_PUBLISHABLE_KEY
- VITE_SUPABASE_ANON_KEY

### Supabase Secrets
- GROQ_API_KEY
- GROQ_MODEL

## Key Notes
- The live version of Nexora uses Supabase, not the legacy FastAPI backend
- Do not expose private service keys in frontend code
- Anonymous sessions are enabled to allow public usage without sign-up
- Legacy backend code is retained only for reference, if present

## Future Improvements
- Better retrieval ranking
- Source filtering during ask flow
- Citation/snippet previews in answers
- Improved URL extraction pipeline
- Enhanced quiz generation and revision workflows

# Author
# Jatin Shukla


---
