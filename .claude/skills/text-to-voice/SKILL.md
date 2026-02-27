---
name: text-to-voice
description: Convert any text file to an MP3 audio file using local TTS. Supports 3 engines (Kokoro, Orpheus, Coqui XTTS v2). Use when the user mentions "text to voice," "text to speech," "TTS," "generate audio," "make an MP3," "read this aloud," or wants to convert a text file to audio.
---

# Text to Voice

You are a TTS assistant. Your job is to convert text files into high-quality MP3 audio using one of three locally-installed TTS engines.

## Workflow

### Step 1: Identify the Input

The user will provide a path to a text file. If no path is given:

1. Check if a recent `/strategic-analysis` run produced an `analysis-voice.txt` in the current directory or a nearby `docs/private/` subdirectory
2. If not found, ask the user for the file path

Read the file and confirm the content length (word count, estimated audio duration) before proceeding.

**Supported input:** Any `.txt` or `.md` file. If the input is markdown, create a TTS-optimized plain text version first (see "Markdown to TTS Text" section below).

### Step 2: Select TTS Engine

Ask the user which engine to use (or use their stated preference). If they don't specify, use Kokoro (fastest).

| Engine | Speed | Best for |
|--------|-------|----------|
| **Kokoro** (default) | Fast (seconds) | Quick iterations, bulk generation |
| **Orpheus** | Slow (~3.5x real-time on M4) | Natural prosody, technical terms |
| **Coqui XTTS v2** | Medium (~1x real-time) | Voice cloning from any WAV sample |

### Step 3: Generate Audio

Generate the WAV file using the selected engine:

**Engine 1 — Kokoro (default):**
```bash
kokoro-tts "<input-file>" "<output-dir>/audio.wav" \
  --voice bf_lily \
  --speed 1.05 \
  --lang en-gb \
  --model ~/Projects/Consulting/tools/kokoro/kokoro-v1.0.onnx \
  --voices ~/Projects/Consulting/tools/kokoro/voices-v1.0.bin
```

**Engine 2 — Orpheus:**
```bash
~/Projects/Consulting/tools/orpheus-tts/venv/bin/python \
  ~/Projects/Consulting/tools/orpheus-tts/orpheus-generate.py \
  --file "<input-file>" \
  --voice tara \
  --output "<output-dir>/audio.wav"
```

**Engine 3 — Coqui XTTS v2:**
```bash
~/Projects/Consulting/tools/coqui-tts/venv/bin/python \
  ~/Projects/Consulting/tools/coqui-tts/coqui-generate.py \
  --file "<input-file>" \
  --speaker-wav "<path-to-reference-voice.wav>" \
  --output "<output-dir>/audio.wav"
```
Note: For XTTS v2, the user must provide a reference WAV file (6+ seconds of the voice to clone). Ask for this path if not provided.

**Output naming:** Use the input filename as the base. E.g., `analysis-voice.txt` → `analysis-voice.wav` → `analysis-voice.mp3`. If the input is just `notes.txt`, output `notes.wav` → `notes.mp3`.

### Step 4: Convert to MP3

Convert the WAV to MP3 using ffmpeg, then remove the WAV:

```bash
ffmpeg -y -i "<output-dir>/audio.wav" \
  -codec:a libmp3lame -b:a 128k \
  "<output-dir>/audio.mp3"
rm "<output-dir>/audio.wav"
```

### Step 5: Copy to Dropbox

Copy the MP3 to the Dropbox "Voice Files Work" folder for easy access on any device:

```bash
# Determine Dropbox path (try both possible locations)
DROPBOX_DIR=""
if [ -d "$HOME/Dropbox/Voice Files Work" ]; then
  DROPBOX_DIR="$HOME/Dropbox/Voice Files Work"
elif [ -d "$HOME/Library/CloudStorage/Dropbox/Voice Files Work" ]; then
  DROPBOX_DIR="$HOME/Library/CloudStorage/Dropbox/Voice Files Work"
fi

# Copy with a descriptive filename
FOLDER_NAME=$(basename "$(dirname "<input-file>")")
FILE_NAME=$(basename "<input-file>" .txt)
cp "<output-dir>/audio.mp3" "$DROPBOX_DIR/${FOLDER_NAME} - ${FILE_NAME}.mp3"
```

If the Dropbox folder doesn't exist at either path, create it at `~/Dropbox/Voice Files Work/` and try the copy. If Dropbox access is denied (sandbox permissions), inform the user and suggest they run the copy command manually.

### Step 6: Report Results

Show the user:

```
Output:
├── <filename>.mp3     (audio — Xm Xs, Y MB)
└── Engine: <engine>, Voice: <voice>

Dropbox:
└── Voice Files Work/<folder> - <filename>.mp3
```

Include the audio duration and file size.

---

## Markdown to TTS Text

If the input file is `.md` (markdown), convert it to TTS-friendly plain text before generating audio:

- Remove all `#`, `##`, `###` heading markers — use the heading text followed by a period instead
- Remove all `---` horizontal rules
- Remove all `**bold**` and `*italic*` markers — use the plain text
- Remove all `|` table formatting — convert tables to prose sentences
- Remove all `- ` bullet markers — convert to flowing prose or use "First:", "Second:", etc.
- Remove all backticks and code formatting
- Replace em dashes `—` with commas or periods for natural speech flow
- Ensure every section transition has a clear spoken cue ("Now let's move to...", "Next,")
- End sentences with periods for natural pauses
- **Acronyms (Kokoro only):** Expand common acronyms for correct pronunciation: ETA → E.T.A., PDF → P.D.F., AI → A.I., GST → G.S.T., HS → H.S., BOL → B.O.L., API → A.P.I.

Save the converted text as `<original-name>-voice.txt` in the same directory, then use that as the TTS input.

---

## TTS Engine Details

### Engine 1: Kokoro (default)
- **Speed:** Fast (seconds per clip)
- **Voices:** 50 built-in voices
- **Best for:** Quick iterations, bulk generation
- **Limitation:** Acronyms need manual expansion (ETA → E.T.A.)

### Engine 2: Orpheus
- **Speed:** Slow (1-3 minutes per clip on CPU, ~3.5x real-time on M4 Metal)
- **Voices:** 8 voices (tara, leah, jess, leo, dan, mia, zac, zoe)
- **Best for:** Natural prosody, emotional speech, technical terms
- **Supports:** Emotion tags: `<laugh>`, `<sigh>`, `<gasp>`, `<chuckle>`
- **License:** Apache 2.0 (free for any use)

### Engine 3: Coqui XTTS v2
- **Speed:** Medium (~1x real-time, ~30s per clip)
- **Voices:** Voice cloning from any 6-second WAV sample
- **Best for:** Cloning a specific person's voice, multilingual (17 languages)
- **License:** Non-commercial model license (Coqui Public Model License)
- **Requires:** A reference WAV file (`--speaker-wav`)

---

## Voice Options

### Kokoro Voices (Engine 1)

Default voice is `bf_lily` (female, British English).

**American English:**
- `af_heart`, `af_bella`, `af_sarah`, `af_nova` (female)
- `am_adam`, `am_michael`, `am_eric`, `am_liam` (male)

**British English:**
- `bf_emma`, `bf_lily`, `bf_isabella` (female)
- `bm_george`, `bm_daniel`, `bm_lewis` (male)

Use `--help-voices` flag with kokoro-tts to list all 50 voices.

### Orpheus Voices (Engine 2)

- `tara` (recommended), `leah`, `jess` (female)
- `leo`, `dan`, `zac` (male)
- `mia`, `zoe` (female, lighter)

### XTTS v2 (Engine 3)

No preset voices — provide any WAV file as a reference for cloning.

---

## Prerequisites

All three engines are installed. Locations:

### Kokoro TTS (Engine 1)
- **CLI:** `kokoro-tts` (installed via pipx)
- **Model:** `~/Projects/Consulting/tools/kokoro/kokoro-v1.0.onnx`
- **Voices:** `~/Projects/Consulting/tools/kokoro/voices-v1.0.bin`

### Orpheus TTS (Engine 2)
- **Venv:** `~/Projects/Consulting/tools/orpheus-tts/venv/`
- **Script:** `~/Projects/Consulting/tools/orpheus-tts/orpheus-generate.py`
- **Model:** `~/Projects/Consulting/tools/orpheus-tts/orpheus-3b-0.1-ft-q4_k_m.gguf`

### Coqui XTTS v2 (Engine 3)
- **Venv:** `~/Projects/Consulting/tools/coqui-tts/venv/`
- **Script:** `~/Projects/Consulting/tools/coqui-tts/coqui-generate.py`
- **Model:** Auto-downloaded on first run (~1.9 GB, cached in HF cache)

### Common
- **ffmpeg** for WAV→MP3 conversion: `brew install ffmpeg`
- **Python 3.12**: `brew install python@3.12`

---

## Error Handling

- If `kokoro-tts` is not found, show the installation command and ask the user to run it
- If model files are missing, show the curl download commands
- If ffmpeg is not found, suggest `brew install ffmpeg`
- If the input file doesn't exist, ask the user to provide the correct path

---

## Chaining

This skill works standalone or as the final step in a chain:

1. **`/voice-to-text <recording.m4a>`** — transcribes audio to `transcript.md`
2. **`/strategic-analysis transcript.md`** — produces `analysis.md` + `analysis-voice.txt`
3. **`/text-to-voice analysis-voice.txt`** — generates MP3 audio

Or skip straight to audio: `/text-to-voice any-text-file.txt`
