<img src="https://res.cloudinary.com/dcnncsybz/image/upload/v1756484688/ChatGPT_Image_Aug_29_2025_09_53_13_PM_q7j0bk.png" alt="Banner" style="width:100%;" />

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

🆚 **Uniqueness:** Unlike existing platforms, KrishiMitra AI is:

* Multilingual & voice-first (easy for rural farmers).
* Combines **AI + local agricultural data + government resources**.
* Works as a **24/7 digital companion** instead of static apps.

---

## Use of OpenAI APIs

* **GPT-4.1 / GPT-4o** → For generating farmer-friendly advice in simple local language.
* **Whisper API** → For speech-to-text (farmers can ask queries via voice).
* **DALL·E API** → For generating visual guides (pest identification charts, fertilizer application methods).
* **Vision API (GPT-4o with image input)** → Farmers upload crop images → AI detects disease.

Integration Flow:

1. Farmer speaks/asks → Whisper → text.
2. GPT processes query + context → gives response.
3. If image uploaded → GPT-4o Vision analyzes → suggests solution.
4. Optional: DALL·E creates **visual guides** (infographics).

---

## Feasibility

🛠 **Tech Stack**:

* Frontend → React.js (progressive web app, mobile-friendly).
* Backend → Node.js.
* Database → SQL (farmer profiles, crop history).
* APIs → OpenAI (GPT, Whisper, DALL·E), Weather API, Govt Scheme API (if available).

⚙ **Architecture (Simplified):**
Farmer App (Voice/Chat + Image Upload) → Backend (AI Orchestration) → OpenAI APIs → Response Delivery (Voice/Chat + Visual).

📍 **Constraints & Plans:**

* Offline Mode (basic Q&A cached for poor internet areas).
* Prioritize Telugu/Hindi for Phase 1 rollout.
* Deploy prototype on **Replit/GitHub** for demo.

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

## 🎥 Demo 

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
├── frontend/      # React. js
├── backend/       # Node.js API
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






