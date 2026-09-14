# Alpha Clips

> **Transform long-form YouTube content into scroll-stopping TikToks, Shorts, and Reels — complete with animated captions, automatic face framing, and background music, all in just a few minutes.**

---

## Getting Started (3 Simple Steps)

### Step 0: Get the Code
Clone the repository and move into the project folder:
```bash
git clone https://github.com/JerrardJ/alpha-clipping-tool.git
cd alpha-clipping-tool
```

### Step 1: Prerequisites
1. **[Git](https://git-scm.com/)** — install via `winget install Git.Git` on Windows, `brew install git` on Mac, or download from [git-scm.com](https://git-scm.com/).
2. **[Node.js](https://nodejs.org/)** (version 18 or later)
3. **Python** (version 3.10 or later) — grab it from [python.org](https://www.python.org/downloads/) or the [Microsoft Store (Windows)](https://apps.microsoft.com/detail/9ncvdn91xzqp)
4. **FFmpeg and yt-dlp** (needed for downloading and rendering videos)
   * **Windows (PowerShell):**
     ```powershell
     winget install Gyan.FFmpeg
     winget install yt-dlp.yt-dlp
     ```
     *(Restart your terminal afterward so Windows picks up the new tools)*
   * **Mac (Terminal):**
     ```bash
     brew install ffmpeg yt-dlp
     ```
     *(No Homebrew yet? Install it first from [brew.sh](https://brew.sh))*

### Step 2: Install Project Dependencies
From inside the project folder, run:
```bash
npm install
python -m pip install -r backend/requirements.txt
```
*(Mac users should use `python3 -m pip install -r backend/requirements.txt` instead)*

### Step 3: Launch the App
```bash
npm run dev
```
Then open **`http://localhost:5173`** in your browser.

---

## Keeping Your Copy Up to Date

To pull down the newest features and bug fixes, run this from inside the `alpha-clipping-tool` folder:

```bash
git pull
npm install
python -m pip install -r backend/requirements.txt
```
*(Mac: `python3 -m pip install -r backend/requirements.txt`)*

---

## Getting a Free Google Gemini API Key (1 Minute)

Alpha Clips relies on Google's AI to identify the strongest viral-worthy moments, at no cost:
1. Visit **[Google AI Studio](https://aistudio.google.com/)** and log in with any Google account.
2. Select **"Get API key"** (or **"Create API key"**).
3. Copy the generated key (it begins with `AIzaSy...`).
4. Drop it into the **Gemini API Key** field within the app.

> **Tip:** Don't have a key yet? Type `mock` in the API Key field to try the app with sample data instead.

---

## How It Works

1. **Drop in a YouTube link** — any podcast, livestream, or standard video works.
2. **Pick your clip length** — `~15s` for quick hooks, `~30s` for standard shorts, or `~60s` for longer storytelling clips.
3. **Hit "Analyze Video"** — the AI scans YouTube retention data to surface the most engaging segments.
4. **Fine-tune in Clip Studio**:
   * **Frame and Crop**: vertical 9:16 fullscreen, square, or split-screen facecam layouts.
   * **Face Tracking**: keeps the speaker centered automatically as they move.
   * **Subtitles**: pick from viral-style animated karaoke captions and font options.
   * **Branding and Audio**: layer in a watermark logo, background music, and hook sound effects.
   * **Hardware Acceleration**: select your GPU (NVIDIA, AMD, Intel) or fall back to CPU rendering.
5. **Render in Batch and Download** — click **Batch Render**, then grab every finished clip together as a single **.ZIP** file.

---

## Troubleshooting

### 1. "Failed to render video" or `The system cannot find the file specified`
* **Cause:** `ffmpeg` or `yt-dlp` isn't installed on your machine.
* **Fix:**
  * **Windows (PowerShell):**
    ```powershell
    winget install Gyan.FFmpeg
    winget install yt-dlp.yt-dlp
    ```
    *(Restart your terminal after installing)*
  * **Mac (Terminal):**
    ```bash
    brew install ffmpeg yt-dlp
    ```
  * Alternatively, install via Python: `pip install yt-dlp`

### 2. "Sign in to confirm you're not a bot"
* **Cause:** YouTube throttles downloads once too many requests come in without an authenticated session.
* **Fix:** Click the **Cookies** button in the top navigation bar, export your YouTube cookies with a free browser extension (such as *Get cookies.txt locally*), then paste them into the app.

### 3. Is AMD and Mac hardware supported?
* **Yes.** Alpha Clips automatically detects and supports:
  * **NVIDIA** (`h264_nvenc`)
  * **AMD** (`h264_amf` for Radeon GPUs and Ryzen CPUs)
  * **Intel** (`h264_qsv` for Arc and UHD Graphics)
  * **Apple/Mac and CPU fallback** (`libx264`, a universal high-speed software encoder)
* Your preferred hardware encoder can be switched anytime from the Render Settings or History panel.

---

## License

Released under the **MIT License** — free to use for both personal and commercial projects.
