# 🌾 Adamah AI — Empowering Farmers with Generative AI

## 📌 Overview

**Adamah AI** is an **AI-powered digital copilot for farmers in Bharat**.
It provides **multilingual, trusted, and actionable farm advisory** on crop issues, fertilizer dosages, daily tasks, and mandi prices — all delivered via **web and WhatsApp/IVR**, so even smallholders with basic phones can access it.

---

## 🚜 Problem Statement

* Small and marginal farmers struggle with **timely, reliable advice** on crop diseases, fertilizer dosages, and safe practices.
* They rely on word-of-mouth, middlemen, or outdated pamphlets.
* Language barriers and lack of internet access make existing solutions hard to use.

---

## 💡 Our Solution — Adamah AI

1. Farmers can **ask questions in Telugu/Hindi/English** (typed or spoken).
2. AI provides **grounded answers** using official agricultural advisories (ICAR, KVK, Govt bulletins).
3. Integrated **tools** help with:

   * Fertilizer dosage & seed calculators
   * Weather-aware daily advisories
   * Local mandi price snapshots
4. **Safety-first design:** All outputs include **precautionary notes** + escalation to local KVKs if severe.
5. Works on **low-end devices** via **WhatsApp/IVR**, not just smartphones.

---

## ✨ Key Features

* 🌐 **Multilingual** (Telugu, Hindi, English — extensible to others)
* 🎙️ **Voice-first option** (ASR + TTS integration planned)
* 📖 **RAG-based answers** → grounded in government agri docs
* 🧮 **Dosage calculator** → land area → fertilizer/seed requirements
* 🌦️ **Daily advisory** → crop-stage + weather-based tasks
* 📊 **Mandi price lookup** → CSV/DB for local prices
* 🔒 **Guardrails** → disclaimers, safe instructions, KVK escalation

---

## 🛠️ Tech Stack

**Frontend:** React (Vite) + Tailwind + i18n
**Backend:** Node.js (Express, TypeScript)
**AI/RAG Service:** Python (FastAPI, Sentence Transformers, pgvector)
**Database:** PostgreSQL + pgvector extension
**Deployment:** Vercel (frontend), Railway/Render (backend + DB)

---

## 🔬 AI Approach

* **RAG Pipeline**:

  * Collect govt advisories (ICAR crop sheets, state agri bulletins, KVK docs).
  * Chunk docs (600–800 tokens) → embed with `all-MiniLM-L6-v2`.
  * Store embeddings in Postgres (pgvector).
  * Retrieve relevant chunks → LLM prompt with user profile (district, crop, stage, soil, weather).
  * Answer with **dosages, steps, safety notes, citations**.

* **Tool-Augmented LLM**:

  * `get_weather(lat,lng)` → stubbed/demo API.
  * `dosage_calc(crop, area, fertilizer)` → deterministic rules.
  * `price_helper(district, crop)` → reads from mandi CSV.

* **Guardrails**:

  * Refuse unsafe/non-agri requests.
  * Always output safety + escalation notes.

---

## 📊 System Architecture

```
[React Frontend] --> [Node/Express API] --> [RAG Service: FastAPI + pgvector]
                                 |--> Weather API (stub)
                                 |--> Dosage Calculator
                                 |--> Prices (CSV/DB)
[Postgres + pgvector] --> stores docs, embeddings, user queries
```

---

## 🎥 Demo (2 min flow)

1. **Farmer asks in Telugu:** “నా వరి ఆకులు పసుపు రంగులోకి మారుతున్నాయి”

   * AI → suggests likely causes, fertilizer dosage, safety, and sources.
2. **Dosage Calculator:** Paddy, 1.5 acres, Urea → 75 kg total, clear breakdown.
3. **Mandi Prices:** Sample CSV shows local market rates.
4. **Switch to Hindi:** Same query answered fluently in Hindi.

---

## 🌍 Impact for Bharat

* **120M+ farmers** in India face crop losses due to late/misinformed advice.
* Adamah AI offers **timely, local, and safe guidance**.
* **Supports Govt vision**: Digital Bharat, agri productivity, farmer welfare.
* **Public good + AI showcase** → knowledge democratized for rural India.

---

## 🚀 Future Roadmap

* 📷 Leaf image analysis (basic pest detection)
* 📱 Offline advisory packs (last 10 answers + prices cached)
* 🎙️ Voice input/output (IVR, WhatsApp audio replies)
* 🌍 Scale to more crops, states, and languages
* 🤝 Partnership with **KVKs, ICAR, NGOs** for verified data

---

## 📂 Repo Structure

```
Adamah-ai/
├── frontend/      # React + Tailwind + i18n
├── backend/       # Node.js Express API
├── rag-service/   # Python FastAPI RAG + embeddings
├── db/            # SQL migrations
└── README.md
```

---

## 📜 Disclaimer

Adamah AI is an **advisory support tool only**.
It does **not replace agricultural experts**.
For severe issues, farmers should **contact local KVKs or extension officers**.

---

⚡ **Made with ❤️ for Bharat** | NXTwave x OpenAI Innovation Challenge 2025

---

