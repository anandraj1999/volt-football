# ⚡ VOLT — Volunteer On-site Live Translator

### GenAI-Powered Real-Time Assistant for Stadium Volunteers, built for PromptWars — Global Prompt Challenge

**🔗 Live App:** https://volt-volunteer-on-site-live-translator-750416859101.asia-southeast1.run.app/
**🏆 Hackathon:** PromptWars x Global Prompt Challenge — organized by Hack2Skill in partnership with Google for Developers
**☁️ Built with:** Google AI Studio → deployed on Google Cloud Run

---

## ⚽ The Problem

Inside a stadium packed with 80,000+ fans from every corner of the world, volunteers are the frontline of the fan experience. In seconds, they need to understand a question asked in a language they don't speak, and respond with accurate, grounded directions — about gates, medical posts, accessible ramps, food allergies, or separated families — while standing in a loud, high-pressure environment.

A language barrier at the wrong moment can turn a minor request into a real safety issue.

## 💡 The Solution

**VOLT** is a high-contrast, mobile-first web app that gives on-site volunteers instant, GenAI-powered translation and triage — so any question, in any language, gets a fast, correct, sunlight-readable answer in under 10 seconds.

---

## 🧬 How It Works

### 1. Real-Time Grounded Translation
A fan speaks or types a question. VOLT sends it to a Gemini-powered backend endpoint (`/api/translate`), which is grounded against a structured, hard-coded stadium knowledge base (gates, concessions, medical stations, accessibility, bag policy) to avoid hallucinated directions. Gemini returns:
- Detected language + intent category (gate / food / accessibility / medical / etc.)
- A one-line English triage summary for the volunteer to scan instantly
- A fully worded response in the fan's own language
- A phonetic spelling so the volunteer can attempt to say it out loud

### 2. Quick Answers — Stadium Guide
A tappable bento grid of the most common fan questions, answered instantly from the local grounded dataset — works even with poor stadium Wi-Fi/5G since the core data is compiled client-side.

### 3. "Show to Fan" Flip Mode
One tap flips the screen into a glare-readable, large-type card so the volunteer can simply show the translated answer to the fan instead of speaking it.

### 4. Priority Alert Escalation
For medical incidents, safety hazards, or crowd issues, volunteers log an urgency level (Medium/High/Critical) with location, which posts to a live shared incident feed for control-room coordination.

### 5. Megaphone Announcement Generator
Describe a crowd bottleneck in plain text, and Gemini drafts a short, clear, action-oriented crowd-control announcement in English, Spanish, and Portuguese — ready to read aloud.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 19, Vite, Tailwind CSS v4, Framer Motion (motion) |
| Speech | Web Speech API (browser-native mic capture) |
| Backend | Express (Node.js), rate-limited API layer |
| AI | Google Gemini API via `@google/genai` SDK, server-side only |
| Deployment | Google Cloud Run (containerized, built in Google AI Studio) |
| Alt. Deploy | Cloudflare Workers-ready port included (`/worker`) |

**Why this stack:** the Gemini calls are proxied entirely server-side so no API key ever touches the client, and the grounded stadium dataset keeps every response tied to real facts instead of open-ended generation.

---

## 📖 Grounded Data Model

To keep responses accurate and non-hallucinated, VOLT ships with a hard-compiled stadium dataset covering:
- 8 gates (A–H) with live wait-queue estimates and accessibility turnstiles
- 12+ concession stands tagged for dietary needs (vegetarian, vegan, gluten-free, halal, nut-free)
- 4 medical first-aid stations with locations and contact extensions
- Accessibility ramps, sensory suites, and guest services desks
- Clear bag policy and re-entry rules

---

## 🚀 Run Locally

```bash
# 1. Add your Gemini API key
echo 'GEMINI_API_KEY="YOUR_ACTUAL_GEMINI_API_KEY"' > .env

# 2. Start the dev server (Express + Vite, port 3000)
npm install
npm run dev

# 3. Production build
npm run build
npm run start
```

---

## 🌍 Impact

VOLT turns any stadium volunteer into a 100+ language interpreter with grounded local knowledge — cutting fan-assistance time from minutes of confusion to a single tap, and giving control rooms real-time visibility into on-ground incidents.

---

## 🏷️ Hackathon

Built for **PromptWars — Global Prompt Challenge**, organized by **Hack2Skill** in partnership with **Google for Developers**.
