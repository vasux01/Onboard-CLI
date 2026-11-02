<div align="center">

# 👻 RepoPhantom

### **The Offline-First AI Mentor for Open-Source Onboarding & Issue Triage**

*Built by **Team RasmalaiOverflow** (Vedant Saini & Om Shukla) for **DevForge Hacktoberfest 2026***

[![Hackathon](https://img.shields.io/badge/DevForge-Hacktoberfest_2026-FF6B00?style=for-the-badge)](https://github.com/vasux01/Onboard-CLI)
[![Team](https://img.shields.io/badge/Team-RasmalaiOverflow-9B4DFF?style=for-the-badge)](https://github.com/vasux01/Onboard-CLI)
[![Model](https://img.shields.io/badge/AI_Engine-Gemma_2_(2B)-4285F4?style=for-the-badge&logo=google&logoColor=white)](https://ollama.com/library/gemma2:2b)
[![Backend](https://img.shields.io/badge/Inference-Ollama_Local-000000?style=for-the-badge)](https://ollama.com/)
[![Frontend](https://img.shields.io/badge/UI-Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![Privacy](https://img.shields.io/badge/Privacy-100%25_Offline-2E7D32?style=for-the-badge)](https://github.com/vasux01/Onboard-CLI)

[**Overview**](#-1-project-overview--problem-statement) • [**Architecture**](#️-2-key-features--architecture) • [**Benchmarks**](#-3-benchmarks--hardware-performance) • [**Installation**](#-4-step-by-step-installation-guide) • [**Troubleshooting & FAQ**](#️-5-troubleshooting--faq)

</div>

---

> [!IMPORTANT]
> **100% Offline by Design:** RepoPhantom runs strictly on your local loopback network (`127.0.0.1`). There are **zero API keys**, **zero cloud dependencies**, and **0 bytes of proprietary codebase data ever leaked** to external servers.

---

## 🚀 1. Project Overview & Problem Statement

* **🥶 The "Cold Start" Problem:** Navigating a massive open-source repository for the first time is overwhelming. Hundreds of undocumented folders paralyze new contributors on day one, wasting days of momentum just figuring out where to start.
* **🔒 The Cloud Privacy Dilemma:** Developers want AI to explain unfamiliar codebases, but pasting proprietary directory structures into cloud LLMs (like ChatGPT or Claude) violates enterprise security policies and risks leaking intellectual property.
* **⚡ The RepoPhantom Solution:** RepoPhantom acts as an ultra-fast, local-first intelligence layer. It scans your local directory, filters out dependency bloat, and generates an actionable onboarding roadmap and issue triage guide natively on your hardware.

---

## 🏗️ 2. Key Features & Architecture

~~~text
+-----------------------+      +-----------------------------------+      +----------------------------------+
|   Local Repository    | ---> |     Python os.walk() Scanner      | ---> |   Ollama + Google Gemma 2 (2B)   |
|  Target Path: "."     |      | Strips: venv, node_modules, .git  |      |   Offline Loopback (Port 11434)  |
+-----------------------+      +-----------------------------------+      +----------------------------------+
                                                                                           |
                                                                                           v
                               +-----------------------------------------------------------------------------+
                               |                  Streamlit Dark-Mode Dashboard (Port 8501)                  |
                               |  [Tab 1: General Onboarding Roadmap]   |   [Tab 2: Automated Issue Triage]  |
                               +-----------------------------------------------------------------------------+
~~~

### ✨ Core Capabilities

| Workflow Mode | Developer Input | Under-the-Hood Mechanism | Actionable Output |
| :--- | :--- | :--- | :--- |
| **🗺️ General Onboarding** | Local folder path (`.`) & focus preset | Depth-limited `os.walk` builds a clean structural skeleton for `gemma2:2b` | Prioritized day-one file reading list & architectural map |
| **🎯 Issue Triage** | Plain-English GitHub bug description | Cross-references bug context against the filtered directory tree | Pinpoints the exact file path to edit (e.g., `.streamlit/config.toml`) |
| **🧹 Smart Bloat Filter** | Raw repository directory | Automatically strips `venv`, `node_modules`, `.git`, and `__pycache__` | Reduces prompt token size by **~92%** to prevent context overflow |

---

## 📊 3. Benchmarks & Hardware Performance

| Evaluation Metric | 👻 RepoPhantom (`gemma2:2b` Local) | ☁️ Cloud AI (ChatGPT / Claude / Copilot) |
| :--- | :--- | :--- |
| **Data Privacy & Security** | **100% Air-Gapped (0 bytes leaked)** | Uploads repo structure to external cloud servers |
| **API & Subscription Costs** | **$0 Forever (No API keys needed)** | $20/month per seat or metered token billing |
| **10,000+ File Repo Handling** | **Automated `os.walk` bloat pruning** | Manual copy-paste hits context window limits |
| **Internet Requirement** | **Works in complete Airplane Mode** | Requires constant internet connection |

### 💻 Consumer Hardware Metrics (Tested on Apple Silicon MacBook Air)
* **🧠 RAM Footprint:** `~1.8 GB` (Runs smoothly on standard 8 GB base laptops without a dedicated GPU)
* **⚡ Directory Scan Speed:** `1,000+ files` mapped in `< 1.8 seconds`
* **⏱️ End-to-End Generation Time:** `~10 seconds` from scan to complete markdown roadmap

---

## 💻 4. Step-by-Step Installation Guide

Since RepoPhantom is a 100% local application, it requires both an isolated Python environment and the Ollama local AI engine.

### Step 1: Clone the Repository
~~~bash
git clone https://github.com/vasux01/Onboard-CLI.git
cd Onboard-CLI
~~~

### Step 2: Create & Activate a Virtual Environment (Crucial for macOS)
To bypass macOS PEP 668 security blocks (`externally-managed-environment`), create an isolated container inside the project folder:
~~~bash
python3 -m venv venv
source venv/bin/activate
~~~
> 💡 **Verification:** Your terminal prompt must now begin with `(venv)`.

### Step 3: Install Python Dependencies
~~~bash
pip install streamlit ollama
~~~

### Step 4: Install Ollama & Pull `gemma2:2b`
* **macOS / Linux:**
  ~~~bash
  curl -fsSL https://ollama.com/install.sh | sh
  ~~~
* **Windows:** Download the native installer from [ollama.com/download](https://ollama.com/download)

Next, pull Google's lightweight 2-billion parameter Gemma 2 model:
~~~bash
ollama pull gemma2:2b
~~~
*(Wait for the download to reach 100% and display `success`.)*

### Step 5: Launch RepoPhantom
In your terminal tab where `(venv)` is active, start the Streamlit server:
~~~bash
streamlit run phantom.py
~~~
The dashboard will automatically open in your browser at **`http://localhost:8501`**.

---

## 🛠️ 5. Troubleshooting & FAQ

*(Click any question below to expand the solution)*

<details>
<summary><b>1. Why did <code>pip install</code> fail with <code>error: externally-managed-environment</code> on macOS?</b></summary>
<br>
Modern macOS versions lock the global system Python (PEP 668) to protect OS tools. Always create and activate a local virtual environment first:
<pre><code>python3 -m venv venv
source venv/bin/activate
pip install streamlit ollama</code></pre>
</details>

<details>
<summary><b>2. Why does <code>source venv/bin/activate</code> say <code>no such file or directory</code>?</b></summary>
<br>
The <code>venv</code> folder has not been created inside your current working directory yet, or your terminal is outside the repository folder. Run these commands in order:
<pre><code>cd ~/Desktop/Onboard-CLI
python3 -m venv venv
source venv/bin/activate</code></pre>
</details>

<details>
<summary><b>3. Why did Streamlit throw <code>Error: Invalid value: File does not exist: phantom.py</code>?</b></summary>
<br>
Your terminal is currently sitting on the <code>Desktop</code> (or parent folder) rather than inside the project directory. Run <code>cd Onboard-CLI</code> first, verify <code>phantom.py</code> is present with <code>ls</code>, and then run <code>streamlit run phantom.py</code>.
</details>

<details>
<summary><b>4. Why does the UI show a yellow warning: <code>"Ollama Python package not found"</code> on port <code>8503</code>?</b></summary>
<br>
Seeing port <code>localhost:8503</code> means an older Streamlit instance is running in the background <i>outside</i> of your virtual environment. Press <code>Ctrl + C</code> in your terminal tabs to stop old servers, activate your container with <code>source venv/bin/activate</code>, verify with <code>pip install streamlit ollama</code>, and relaunch on port <code>8501</code>.
</details>

<details>
<summary><b>5. Why did <code>ollama serve</code> fail with <code>listen tcp 127.0.0.1:11434: bind: address already in use</code>?</b></summary>
<br>
That message is actually good news—it means the Ollama background daemon is <b>already running</b> on port <code>11434</code>! You do not need to run <code>ollama serve</code> manually; proceed directly to using the Streamlit app.
</details>

<details>
<summary><b>6. Why does <code>phantom.py</code> specify <code>modelname = "gemma2:2b"</code> instead of <code>"gemma2"</code>?</b></summary>
<br>
Running <code>ollama pull gemma2</code> defaults to the heavy 9B parameter model (~5.4 GB). We specifically target <code>gemma2:2b</code> (~1.8 GB RAM) for fast, low-latency inference on standard laptops. The model string inside <code>phantom.py</code> must exactly match the tag shown in <code>ollama list</code>.
</details>

<details>
<summary><b>7. Where is the "Generate Roadmap" button in the interface?</b></summary>
<br>
Inside the Streamlit UI under the <b>General Onboarding</b> tab, the action button is labeled <b>Generate onboarding guide</b>.
</details>

---

<div align="center">

**Built with ❤️ and 0% Cloud Leakage by Team RasmalaiOverflow**  
*Vedant Saini & Om Shukla • DevForge Hacktoberfest 2026*

</div>
