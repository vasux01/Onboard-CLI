# 👻 RepoPhantom

**Instantly generate architectural roadmaps and issue-resolution guides for complex repositories using local, open-weight AI.**

Built for the **DevForge Hacktoberfest 2026 Finals** | Track: AI for Open Source

## 🚀 The Problem
Navigating a massive open-source project for the first time is overwhelming. RepoPhantom acts as a local "tour guide" that reads your directory tree, ignores bloat, and uses offline AI to tell you exactly where to start and which files to edit to fix specific issues.

## 🛠️ Tech Stack & AI Policy
* **Frontend:** Python & Streamlit
* **AI Engine:** Local Gemma 2 2B (via Ollama)
* **Privacy:** 100% offline processing. No cloud APIs, no exposed secrets, and zero codebase leakage.

## ⚙️ Setup & Installation
1. Install [Ollama](https://ollama.com/) and download the open-weight model:
   ```bash
   ollama run gemma2:2b