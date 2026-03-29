# YT Helper

An AI-powered YouTube assistant for searching and downloading videos/audio, built with **Gemini CLI** and **MCP (Model Context Protocol)**.

`yt-helper` is designed to streamline the process of finding and downloading content from YouTube. It can even "see" a song list from an image and help you search and download the entire collection automatically.

## ✨ Features

- **🖼️ Image-to-Song List**: Automatically extract song titles and artists from images (e.g., printed song lists).
- **🔍 Intelligent Search**: Uses `yt-mcp-server` to find the most relevant high-quality videos on YouTube.
- **🎵 Flexible Downloads**: Support for MP3 (audio) and MP4 (video) formats using `yt-dlp`.
- **🚀 Automated Workflow**: Integrated "Search -> Confirm -> Download -> Archive" lifecycle managed by Gemini CLI.
- **📂 Smart Archiving**: Automatically organizes downloaded files into `assets/now` and moves completed tasks to `assets/history`.
- **🛡️ Secure & Isolated**: Runs `yt-dlp` in a local virtual environment managed by `uv`.

## 🛠️ Prerequisites

Before you begin, ensure you have the following installed:

- **[uv](https://docs.astral.sh/uv/)**: Fast Python package and project manager.
- **[ffmpeg](https://ffmpeg.org/)**: Required for audio extraction and format merging.
- **[Gemini CLI](https://github.com/google-gemini/gemini-cli)**: The core engine driving the AI interactions.
- **[MCP Server](https://github.com/modelcontextprotocol)**: For YouTube API integration.

## 🚀 Getting Started

### 1. Clone the Project
```bash
git clone https://github.com/kime541200/yt-helper.git
cd yt-helper
git submodule update --init --recursive
```

### 2. Configure Environment
Copy `.env.example` to `.env` in `modules/yt-mcp-server` and add your YouTube API Key:
```bash
cp modules/yt-mcp-server/.env.example modules/yt-mcp-server/.env
# Edit modules/yt-mcp-server/.env and add YOUTUBE_API_KEY
```

### 3. Usage
Simply trigger the `youtube-downloader` skill through Gemini CLI:

```bash
# In Gemini CLI
"Help me download videos using the youtube-downloader skill."
```

#### Workflow Example:
1. **Input**: Put a song list image in `assets/now/song-list.jpg`.
2. **Detection**: The AI reads the image and extracts the song titles.
3. **Search**: The AI searches YouTube for each song.
4. **Download**: Confirm the list and format (MP3/MP4), and the AI downloads everything for you.
5. **Archive**: Files are saved to `assets/now/<date>/` and then archived to `assets/history/`.

## 📂 Project Structure

```text
yt-helper/
├── .gemini/            # Gemini CLI configuration and skills
├── .agent/             # AI agent specific instructions
├── assets/
│   ├── examples/       # Example song lists
│   ├── now/            # Current workspace for downloads
│   └── history/        # Archived downloads
├── modules/
│   ├── yt-mcp-server/  # YouTube MCP server for searching
│   └── yt-dlp-downloader-skill/ # Core download logic
└── README.md
```

## 📜 License

MIT

## 🙌 Credits

- **[yt-dlp](https://github.com/yt-dlp/yt-dlp)**: The powerful video downloader engine.
- **[Gemini CLI](https://github.com/google-gemini/gemini-cli)**: For providing the interactive AI environment.
- **[MCP](https://modelcontextprotocol.io/)**: For seamless tool integration.
