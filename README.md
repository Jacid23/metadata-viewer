# Metadata Center 👁

Single-file pure HTML tool for viewing metadata from AI model files, images, videos, and audio — all locally in your browser with no installation required.

## Usage
Open `index.html` in any modern web browser and drag a supported file onto the drop zone, or click to select one. No setup, no server needed.

## Demo
https://jacid23.github.io/metadata-viewer

## Supported File Types

| Type | Formats |
|------|---------|
| AI Models | `.safetensors`, `.gguf` |
| Images | `.png`, `.jpg`, `.jpeg`, `.webp` |
| Video | `.mp4`, `.webm`, `.mov`, `.mkv` |
| Audio | `.mp3`, `.wav`, `.flac`, `.ogg`, `.m4a`, `.aac` |

## Features

### AI Models (Safetensors / GGUF)
- View, edit, and remove embedded metadata
- Configurable metadata summary dashboard
- Configurable training tag frequency summary
- CivitAI resource lookup — model info, preview images, trained words *(requires internet)*
- Arc En Ciel resource lookup *(requires internet)*
- SHA-256 / AutoV3 hash calculation for large file support (>2 GB)

### Images
- Reads AI generation metadata from PNG, JPEG, and WebP files
- Supports SD WebUI, ComfyUI, InvokeAI, and generic formats
- Displays generation settings: model, resolution, steps, scheduler, CFG, seed, LoRAs
- Falls back gracefully when no AI metadata is present — shows thumbnail, resolution, and file info

### Video
- Captures a still frame (frame ~100) as the summary thumbnail
- Reads container metadata: duration, resolution, video/audio codec, creation date, title, encoder
- Handles both faststart (moov-first) and moov-last files (camera recordings)
- Supports MP4/MOV, WebM/MKV
- Playable video in the Online Lookup panel

### Audio
- Reads embedded tags: title, artist, album, album artist, year, genre, track, composer, comment
- ID3v2 tag parsing for MP3 (UTF-8 and UTF-16)
- Vorbis comment parsing for FLAC
- MP4 container tag parsing for M4A
- Inline audio player in the summary

### General
- Multiple summary layout options: Dashboard, Table, Grid, Custom
- Custom field calculations (JavaScript expressions) with access to file metadata, CivitAI data, and previously defined fields
- Multiple themes with color variants
- Fully offline — no data leaves your browser
- Single self-contained HTML file (no dependencies to install)

## Offline Execution
The tool is designed to be used offline and processing is entirely done on your browser. However, the following features require fetching some resources on the internet and will not work without internet connectivity:
- CivitAI data lookup
- Processing large files (greater than 2GB)
    - Optionally, if you wish to maintain everything local, you may download the <a name="unique-anchor-name" href='https://cdn.jsdelivr.net/npm/hash-wasm@4/dist/sha256.umd.min.js'>sha256.umd.min.js</a> file, place it in the same directory as the HTML file, and replace this line
        ```html
        <script src="https://cdn.jsdelivr.net/npm/hash-wasm@4/dist/sha256.umd.min.js"></script>
        ```
        with 
        ```html
        <script src="sha256.umd.min.js"></script>
        ```

## Screenshots
![App Screenshot](https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/5c3b0f97-d7ff-4c7a-b9c5-d5f176544151/original=true,quality=90/Screenshot%202025-10-01%20195536.jpeg)
