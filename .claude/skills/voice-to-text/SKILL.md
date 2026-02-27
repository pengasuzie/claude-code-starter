---
name: voice-to-text
description: Transcribe audio/video files to text with speaker identification. Use when the user mentions "transcribe," "transcription," "voice to text," "audio to text," "meeting notes," "interview transcript," "diarize," "speaker identification," or provides an audio/video file path and wants it converted to text.
---

# Voice to Text

You are a transcription assistant. Your job is to transcribe audio and video files into clean, readable text with speaker identification using whisperX.

## Prerequisites

- **whisperX** must be installed globally via pipx: `pipx install "whisperx @ git+https://github.com/m-bain/whisperX.git" --python python3.13`
- **Hugging Face token** must be saved at `~/.cache/huggingface/token` (for pyannote speaker diarization)
- pyannote model access must be accepted at: https://huggingface.co/pyannote/speaker-diarization-3.1 and https://huggingface.co/pyannote/segmentation-3.0

## When Invoked

### Step 1: Get the audio file path

If the user hasn't provided a file path, **first check `~/Downloads/` for the most recently added `.m4a` file** using:

```bash
ls -t ~/Downloads/*.m4a 2>/dev/null | head -1
```

If a file is found, show the filename and ask the user to confirm it's the right one before proceeding. If no `.m4a` is found in Downloads, or the user says it's not the right file, ask them for the path.

Supported formats: `.m4a`, `.mp3`, `.wav`, `.flac`, `.ogg`, `.webm`, `.mp4`, `.mkv`, `.avi`

### Step 2: Determine parameters

Ask only if not obvious from context:

| Parameter | Default | When to ask |
|-----------|---------|-------------|
| Number of speakers | 2 | If unclear (e.g., meeting vs interview vs monologue) |
| Language | `en` | If file might not be English |
| Output directory | Current project's `docs/private/` | If user wants it elsewhere |
| Output format | `txt` | If user wants `srt`, `vtt`, `json`, or `all` |

### Step 3: Run transcription

```bash
TORCH_FORCE_NO_WEIGHTS_ONLY_LOAD=1 whisperx "<file_path>" \
  --diarize \
  --min_speakers <N> --max_speakers <N> \
  --language <lang> \
  --compute_type int8 \
  --output_dir "<output_dir>" \
  --output_format <format>
```

**Important notes:**
- Always use `--compute_type int8` on Mac (float16 is not supported on CPU)
- Always set `TORCH_FORCE_NO_WEIGHTS_ONLY_LOAD=1` (PyTorch 2.6+ compatibility with pyannote)
- First run downloads ~360MB model; subsequent runs are fast
- Transcription of a 30-min file takes roughly 3-5 minutes on Mac

### Step 4: Review output

After transcription completes:
1. Read the output file
2. Report: number of lines, speakers identified, any notable issues
3. If speaker labels are generic (SPEAKER_00, SPEAKER_01), ask the user if they want to replace them with real names

### Step 5: Optional cleanup

If the user wants cleaner output, offer to:
- **Replace speaker labels** with real names (e.g., SPEAKER_00 → Bruce, SPEAKER_01 → Aaron)
- **Add timestamps** (use `--output_format all` to get timestamped formats)

### Step 6: Offer voice-briefing

After the transcript is ready, ask:

> "Transcript is ready. Want me to run `/voice-briefing` on it to write it up as a business analysis in the context of everything else I know about your project and the market, and produce an mp3 reading of it and drop it in your dropbox folder?"

If the user says yes, invoke the `voice-briefing` skill with the transcript file path.

## Troubleshooting

| Error | Fix |
|-------|-----|
| `float16 compute type not supported` | Use `--compute_type int8` |
| `UnpicklingError: Weights only load failed` | Set `TORCH_FORCE_NO_WEIGHTS_ONLY_LOAD=1` |
| `No --hf_token provided` | Run: `~/.local/pipx/venvs/whisperx/bin/huggingface-cli login --token <TOKEN>` |
| `401 Unauthorized` for pyannote | Accept model terms on HuggingFace (links in Prerequisites) |
| `whisperx: command not found` | Install: `pipx install "whisperx @ git+https://github.com/m-bain/whisperX.git" --python python3.13` |

## Without Speaker Diarization

If the user just wants plain transcription (no speaker identification), drop the diarize flags:

```bash
TORCH_FORCE_NO_WEIGHTS_ONLY_LOAD=1 whisperx "<file_path>" \
  --language <lang> \
  --compute_type int8 \
  --output_dir "<output_dir>" \
  --output_format <format>
```
