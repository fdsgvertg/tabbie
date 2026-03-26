TABBIE
Your Local AI Desk Companion
v2.0  —  100% Offline  —  Powered by Ollama
No Cloud	No API Key	Streaming	Voice I/O

What is Tabbie?
Tabbie is a local AI-powered desk companion that lives in your browser as a single HTML file. It connects to Ollama running on your PC to give you a real conversational AI — animated, voice-enabled, and completely private. No internet, no subscriptions, no data leaving your machine.

Features
	Feature	Description
AI	Ollama Chat	Streams responses token-by-token from any local model. Full conversation history maintained per session.
MIC	Voice Input	Tap the mic button and speak. Uses browser Web Speech API for real-time transcription — auto-sends when done.
SPK	Text-to-Speech	Tabbie speaks every reply aloud using your system voices. Toggle on/off, choose voice, adjust speed.
VIZ	Audio Visualizer	Live bar visualizer reacts to your microphone. Switches to wave animation when Tabbie is speaking.
ANI	Animated Face	Pupils track your mouse. Blinks randomly. Face glows change color per emotion (thinking, happy, talking, sad).
ORB	Particle BG	80 glowing particles with connecting network lines animate in the background continuously.
TSK	Task List	Add, check off, and manage tasks with glowing checkmarks. Tabbie reacts when you complete a task.
TMR	Focus Timer	25-minute Pomodoro timer with 5-minute break mode. Tabbie announces start and end with voice.
MOD	Mood Tracker	Five emoji moods. Tabbie responds with a fitting message and emotion for each selection.
NTE	Quick Notes	Persistent textarea for quick thoughts during your session.

Requirements
Software needed to run Tabbie:
•	Ollama  —  local AI runtime (free, open source)
•	Any modern browser  —  Chrome, Edge, or Firefox (recommended: Chrome)
•	At least one Ollama model pulled (llama3, mistral, phi3, qwen2, gemma2, etc.)
•	Minimum 4GB RAM recommended (8GB+ for larger models)

Installation & Setup
Step 1 — Install Ollama
Download and install Ollama for your platform:
•	

Step 2 — Fix CORS (Critical)
Ollama blocks browser requests by default. You must set this environment variable BEFORE starting Ollama. This is required every time, or set it permanently (see below).

Windows (Command Prompt):
set OLLAMA_ORIGINS=*
ollama serve

Windows (PowerShell):
$env:OLLAMA_ORIGINS="*"
ollama serve

Permanent fix (Windows):
1.	Search "Environment Variables" in Start Menu
2.	Click "Edit the system environment variables"
3.	Click "Environment Variables" button
4.	Under "User variables", click New
5.	Variable name: OLLAMA_ORIGINS
6.	Variable value: *
7.	Click OK, restart Ollama

Step 3 — Pull a Model
Pull one or more models. Smaller models are faster; larger ones are smarter.
ollama pull llama3          # Recommended — good balance of speed & quality
ollama pull mistral         # Fast, great for coding
ollama pull phi3            # Tiny, very fast on low RAM
ollama pull qwen2:0.5b      # Ultra small — works on 4GB RAM
ollama pull gemma2          # Google Gemma 2

Step 4 — Open Tabbie
8.	Open tabbie.html in Chrome or Edge
9.	Click the ⚙ pill at the top right
10.	URL is auto-filled as http://localhost:11434 — leave it unless you changed Ollama's port
11.	Click Connect — Tabbie auto-detects all your installed models
12.	Select your preferred model from the dropdown
13.	Start chatting!

Voice Features
Enabling Text-to-Speech
•	Click the "voice off" button in the top-right of the chat panel to enable TTS
•	Open settings (⚙) to select your preferred system voice
•	Use the speed slider to adjust speech rate (0.5x to 2.0x)
•	Tabbie will speak every reply out loud when TTS is on

Using Voice Input (Mic)
•	Click the microphone button (🎤) on the right of the visualizer bar
•	Allow microphone access when the browser prompts
•	Speak clearly — Tabbie transcribes in real time
•	When you stop speaking, it auto-sends your message
•	The audio visualizer shows live mic levels while listening
Note: Voice input requires Chrome or Edge. Firefox does not support the Web Speech API.

Choosing a Model
Model	RAM	Speed	Best For
qwen2:0.5b	~1 GB	Very Fast	Low-end PCs, quick answers
phi3	~2 GB	Fast	Coding, concise answers
llama3	~4.7 GB	Medium	General use, best balance
mistral	~4.1 GB	Medium	Writing, coding, analysis
gemma2	~5 GB	Medium	Google model, well-rounded
llama3.1:8b	~8 GB	Slower	High quality, if you have RAM
Tip: You built Zerotwo with qwen2:0.5b — it works great in Tabbie too for fast, lightweight responses.

Troubleshooting
Problem	Fix
403 error on /api/tags	Set OLLAMA_ORIGINS=* before running ollama serve. This is the most common issue.
Cannot reach Ollama	Make sure Ollama is running. Open a terminal and run: ollama serve
No models found	Pull a model first: ollama pull llama3
Mic button not working	Use Chrome or Edge — Firefox does not support Web Speech API
Voice sounds robotic/wrong	Open ⚙ settings and select a different system voice from the dropdown
Slow responses	Switch to a smaller model like phi3 or qwen2:0.5b in the model dropdown
Page looks broken	Open in a modern browser. Internet Explorer is not supported.
Model dropdown empty	Click Connect again after pulling a new model

File Structure
Tabbie is a single self-contained HTML file. No install, no build step, no dependencies.
tabbie.html          <- Everything. Just this one file.

Open it in Chrome and it works.
Drag it to your desktop for quick access.
Bookmark it in your browser.

Privacy
•	All AI inference runs on your machine via Ollama
•	No messages, data or history is ever sent to any external server
•	No telemetry, no analytics, no accounts
•	Chat history exists only in your browser memory — it clears on page refresh
•	Your notes and tasks are session-only (not saved to disk)

