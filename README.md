# Socratic — AI-Powered Active Learning Through Guided Discovery

> An AI companion that **never gives answers** — only the questions that lead you to them.

![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python)
![Flask](https://img.shields.io/badge/Flask-3.0-green?logo=flask)
![Gemini](https://img.shields.io/badge/Google%20Gemini-Free%20API-orange?logo=google)

---

## The Problem

Every AI education tool **gives answers**. But decades of research consistently show that students retain 2-3x more when they **discover answers themselves** through guided questioning — the Socratic method. No tool implements this properly.

## The Solution

**Socratic** is an AI learning companion that implements the Socratic method through:

1. **Never giving direct answers** — always responding with guiding questions
2. **Progressive difficulty** — adapting from foundational → intermediate → advanced → mastery
3. **Misconception detection** — identifying and gently exposing flawed reasoning
4. **Real-time understanding tracking** — quantifying comprehension with a live score
5. **Session summaries** — AI-generated learning reports with discovered insights

## Why It's Different

| Feature | Typical AI Tools | Socratic |
|---------|-----------------|----------|
| Approach | Gives answers directly | Guides to discovery via questions |
| Learning model | Passive consumption | Active construction of knowledge |
| Misconceptions | Ignored or corrected bluntly | Detected and gently probed |
| Progress tracking | Quiz scores | Multi-dimensional understanding signals |
| Pedagogy | None specific | Implements the Socratic method |

## Tech Stack

- **Backend:** Python + Flask
- **AI Engine:** Google Gemini 1.5 Flash (free tier)
- **Database:** SQLite (local, zero-config)
- **Frontend:** Vanilla HTML/CSS/JS (no framework bloat)

## Quick Start

### 1. Get a Free Gemini API Key
Visit [https://aistudio.google.com/apikey](https://aistudio.google.com/apikey) and create a free API key.

### 2. Clone & Setup

```bash
cd inrhackzproject

# Create a virtual environment (recommended)
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # Mac/Linux

# Install dependencies
pip install -r requirements.txt
```

### 3. Configure

Edit the `.env` file and replace `your_gemini_api_key_here` with your actual key:

```
GEMINI_API_KEY=your_actual_key_here
```

### 4. Run

```bash
python app.py
```

Open [http://localhost:5000](http://localhost:5000) in your browser.

## How It Works

### Learning Flow
1. Enter any topic you want to understand
2. Socratic asks a **foundational question** to gauge your baseline
3. You respond with your reasoning (not just "yes/no")
4. Socratic analyzes your response for:
   - **Correct insights** (acknowledged, then pushed deeper)
   - **Misconceptions** (probed with counter-questions)
   - **Knowledge gaps** (addressed through simpler sub-questions)
5. Difficulty progressively increases as understanding grows
6. End the session to receive a comprehensive learning summary

### Key Features
- **Understanding Gauge:** Live circular progress showing your comprehension (0-100%)
- **Difficulty Progression:** Visual tracker from Foundational → Mastery
- **Hint System:** Get directional hints (not answers) when stuck
- **Learning Insights Panel:** Real-time view of your correct insights, misconceptions, and gaps
- **Session Summaries:** AI-generated analysis of what you discovered, what you missed, and what to explore next
- **Learning History:** Track all past sessions with stats and conversation replay

## Project Structure

```
inrhackzproject/
├── app.py                    # Flask application (routes + API)
├── requirements.txt          # Python dependencies
├── .env                      # API key configuration
├── models/
│   └── database.py           # SQLAlchemy models
├── services/
│   └── ai_service.py         # Gemini AI integration (Socratic engine)
├── templates/
│   ├── base.html             # Base template
│   ├── index.html            # Landing page
│   ├── session.html          # Active learning session
│   ├── history.html          # Session history
│   └── review.html           # Session review/summary
└── static/
    ├── css/
    │   └── style.css         # Complete stylesheet
    └── js/
        ├── index.js          # Landing page logic
        ├── session.js        # Session interaction logic
        ├── history.js        # History page logic
        └── review.js         # Review page logic
```

## The AI Engine

The core innovation is in the **system prompt engineering** within `services/ai_service.py`. The AI is constrained to:

- **Never answer directly** — every response is a question
- **Track understanding signals** — correct insights, misconceptions, gaps
- **Score comprehension** — 0-100 understanding metric per exchange
- **Adapt difficulty** — automatically progress or regress based on performance
- **Follow pedagogical principles** — Bloom's taxonomy-aligned difficulty levels

All AI responses are structured JSON, enabling the frontend to parse and visualize learning progress in real-time.

## License

MIT — Built for the Studygy AI App Hackathon
