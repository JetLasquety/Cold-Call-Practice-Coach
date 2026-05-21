# Cold-Call-Practice-Coach
Cold Call Practice Coach
AI-powered cold call simulator for outbound web design appointment setters.
Built with Streamlit + Google Gemini (gemini-2.5-flash).

What It Does
Simulates a live cold call with an AI-generated prospect, then generates a structured coaching report when the call ends.
Flow: Select difficulty → Mock call → Coaching report

Features

Randomized prospect profiles across 3 difficulty tiers (Easy / Medium / Hard)

Varies by business type, industry, digital presence, role, persona, mood, and resistance level


Live mock call — AI plays a realistic prospect; stays in character; does not coach mid-call
Auto coaching report — generated after call ends, covering outcome, objection handling, frame control, KPI check, and a rewritten practice line
Bounded history — last 10 exchanges (20 messages) sent to API per turn


Setup
Requirements
streamlit
google-generativeai
Install:
bashpip install streamlit google-generativeai
API Key

Replace with an environment variable:
pythonimport os
GEMINI_API_KEY = os.environ["GEMINI_API_KEY"]
Set it before running:
bashexport GEMINI_API_KEY=your_key_here
Run
bashstreamlit run app.py

Difficulty Levels
LevelProspect TypeEasyOwner-heavy, low resistance, open to conversationMediumModerate friction, neutral to skepticalHardGuarded, dismissive, burned by agencies, impatient

App Modes
ModeDescriptionselectionChoose difficulty, generate prospect, start callmock_callLive chat with AI prospectcoach_evaluationStructured report + transcript review

Coaching Report Sections

Outcome
Prospect Context
Control Breakdown
Alignment Check
Objection Handling
KPI Check (next step established?)
One Practice Line (weakest line + rewrite)


Notes

Prospect temperature: 0.45 (realistic variation)
Coach temperature: 0.2 (consistent, analytical output)
Model: gemini-2.5-flash (set via MODEL_NAME constant)
History window: MAX_EXCHANGES = 10 — adjust to control API token usage
