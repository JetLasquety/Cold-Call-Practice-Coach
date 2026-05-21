# Cold Call Practice Coach — Voice Mode

AI-powered cold call simulator for outbound web design appointment setters.  
Speak your lines via mic. The prospect responds with audio. Get a structured coaching report when you end the call.

**Stack:** Streamlit · Google Gemini (`gemini-2.0-flash`) · gTTS

---

## How It Works

1. Select difficulty → prospect profile is randomly generated
2. Prospect speaks first (auto-plays via browser audio)
3. Record your line → transcribed by Gemini → prospect replies via audio
4. End the call → AI coaching report generated from full transcript

---

## Setup

### Install dependencies

```bash
pip install streamlit google-generativeai gtts
```

Or add to `requirements.txt`:

```
streamlit
google-generativeai
gtts
```

### API Key

Add to Streamlit Cloud secrets (**Manage app → Secrets**):

```toml
GEMINI_API_KEY = "your_key_here"
```

For local development, set as environment variable:

```bash
export GEMINI_API_KEY=your_key_here
```

### Run locally

```bash
streamlit run app.py
```

---

## Difficulty Levels

| Level  | Prospect Type                                     |
|--------|---------------------------------------------------|
| Easy   | Owner-heavy, low resistance, open to conversation |
| Medium | Moderate friction, neutral to skeptical           |
| Hard   | Guarded, dismissive, burned by agencies           |

---

## Voice Flow

| Step | What Happens |
|------|-------------|
| Call connects | Prospect greets you (audio auto-plays) |
| Your turn | Click mic → record → stop → auto-submits |
| Transcription | Gemini converts your audio to text |
| Prospect reply | Text generated → converted to speech → auto-plays |
| End call | Click ⚡ End Call → coaching report generated |

---

## Coaching Report Sections

1. **Outcome** — booked / deflected / hung up / neutral
2. **Prospect Context** — resistance level vs. actual call behavior
3. **Control Breakdown** — where frame was held or lost
4. **Alignment Check** — pitch fit vs. prospect's digital situation
5. **Objection Handling** — what was missed or fumbled
6. **KPI Check** — clear next step established? Yes/No
7. **One Practice Line** — weakest line quoted + rewritten

---

## Notes

- Prospect temperature: `0.45` · Coach temperature: `0.2`
- History window: last 10 exchanges (20 messages) sent per API call
- `st.audio_input` requires **Streamlit ≥ 1.31**
- Browser autoplay policies may mute audio on first load in some browsers; a page interaction (any click) unblocks it
- Transcript is text-based (transcribed speech); full transcript viewable after call ends
