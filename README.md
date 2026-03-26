# 🤖 Arush's Desktop AI Companion

A fully local AI voice companion that runs entirely on your PC — no paid APIs needed.

---

## Quick Start

### 1. Install Python dependencies
```bash
pip install -r requirements.txt
```

### 2. Install & start Ollama
Download from https://ollama.com then:
```bash
ollama pull phi3:mini
ollama serve
```

### 3. Run the companion
```bash
python main.py
```

---

## File Structure

```
companion/
├── main.py              # Entry point
├── config.py            # All settings (edit this!)
├── companion.py         # Main orchestrator loop
├── audio_recorder.py    # Microphone input + silence detection
├── speech_recognizer.py # Whisper STT
├── ai_brain.py          # Ollama LLM integration
├── tts.py               # Edge TTS voice synthesis
├── audio_player.py      # pygame audio playback
├── memory.py            # Conversation + long-term memory
├── wake_word.py         # Wake word handling
├── requirements.txt
└── memory.json          # Auto-created: persistent memory
```

---

## Configuration (config.py)

| Setting | Default | Description |
|---|---|---|
| `ollama_model` | `phi3:mini` | Swap for `llama3`, `mistral`, etc. |
| `whisper_model` | `base` | `tiny` = faster, `small` = more accurate |
| `tts_voice` | `en-US-AriaNeural` | Any Edge TTS neural voice |
| `record_seconds` | `5.0` | Max recording duration |
| `wake_word_enabled` | `False` | Set True + configure wake word |
| `memory_enabled` | `True` | Persist memory across sessions |

---

## Recommended Model Upgrades

| Use Case | Model | Command |
|---|---|---|
| Fastest (low RAM) | phi3:mini | `ollama pull phi3:mini` |
| Balanced | llama3.2:3b | `ollama pull llama3.2:3b` |
| Best quality | llama3.1:8b | `ollama pull llama3.1:8b` |
| Best quality (16GB RAM) | mistral:7b | `ollama pull mistral:7b` |

---

## Voice Commands

Say these out loud during a conversation:

- **"What time is it?"** — tells you the time
- **"What day is it?"** — tells you today's date
- **"Clear memory"** / **"Forget everything"** — resets conversation history
- **"Goodbye"** / **"Bye"** — saves memory and exits

---

## Roadmap (Future Features)

- [ ] **Avatar** — animated face using tkinter or PyQt
- [ ] **Camera vision** — describe what the webcam sees (llava model)
- [ ] **Emotion detection** — detect mood from voice tone
- [ ] **Wake word** — "Hey Aria" via pvporcupine
- [ ] **Screen understanding** — describe what's on screen (screenshot → VLM)
- [ ] **Better memory** — semantic search with ChromaDB / FAISS
- [ ] **Hotkey push-to-talk** — hold a key instead of auto-recording

---

## Troubleshooting

**No audio / mic not detected**
```bash
python -c "import sounddevice; print(sounddevice.query_devices())"
```
Set `device` parameter in `AudioRecorder` if needed.

**Ollama connection refused**
Make sure Ollama is running: `ollama serve`

**TTS not working**
Edge TTS needs internet for first use but caches voices locally.
Offline alternative: `pip install pyttsx3` and swap in `tts.py`.

**Slow transcription**
Switch to `whisper_model = "tiny"` in config.py for 3x speed boost.
