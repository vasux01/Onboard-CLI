👻 RepoPhantom

Built by Team RasmalaiOverflow (Vedant Saini & Om Shukla) for DevForge Hacktoberfest 2026.

Instantly generate architectural roadmaps and issue-resolution guides for complex repositories using local, open-weight AI.

🚀 1. Project Overview & Problem Statement

The "Cold Start" Problem
Navigating a massive open-source project for the first time is overwhelming. Hundreds of undocumented folders paralyze new developers on day one, wasting hours of momentum just trying to figure out where to start.

The Privacy Dilemma
Developers want AI to explain the codebase to them, but pasting enterprise directory trees into cloud-based LLMs (like ChatGPT or Claude) violates strict company privacy policies and risks leaking proprietary intellectual property.

The Solution
RepoPhantom acts as an ultra-fast, local-first intelligence layer. It reads your local directory, ignores the bloat, and generates an architectural map natively on your machine. Zero data ever leaves your hardware.

🏗️ 2. Key Features & Architecture

Dual-Mode Streamlit Dashboard:

General Onboarding: Generates a structured reading list and architectural map for day-one contributors.

Issue Triage: Pinpoints the exact file path you need to edit to fix a specific bug or issue.

Smart Directory Filtering: The Python backend uses os.walk to scan folders while automatically stripping out heavy bloat (node_modules, venv, .git, __pycache__) to keep the AI prompt lean and within context limits.

100% Local Inference Engine: Powered by Google's open-weight gemma2:2b model running entirely offline via Ollama.

📊 3. Benchmarks & Hardware Performance

Feature

RepoPhantom

Cloud AI (ChatGPT/Claude)

Data Privacy

100% Offline (0 bytes leaked)

Sends proprietary data to cloud

API Costs

$0 forever

Subscription / per-token fees

Context Limit

Optimized (Bloat filtered)

Often overloaded by folder trees

Setup Time

< 2 minutes

Requires enterprise API keys

Hardware Performance (Apple Silicon / Standard Laptops):

RAM Footprint: ~1.8 GB

Scan Speed: 1,000+ files mapped in under 2 seconds.

Generation Time: ~10 seconds from scan to full roadmap.

💻 4. Step-by-Step Installation Guide

Since RepoPhantom is a 100% local application, it requires both a Python environment and the Ollama AI engine.

Step 1: Clone the Repository

git clone https://github.com/vasux01/Onboard-CLI.git
cd Onboard-CLI


Step 2: Create a Virtual Environment (Crucial for macOS)

To avoid system security blocks and keep dependencies isolated, build a local virtual environment:

python3 -m venv venv
source venv/bin/activate


(Note: Your terminal prompt must now begin with (venv))

Step 3: Install Python Dependencies

pip install streamlit ollama


Step 4: Install the Local AI Engine (Ollama)

Mac/Linux: Run this in a new terminal tab: curl -fsSL https://ollama.com/install.sh | sh

Windows: Download the installer from ollama.com/download

Once installed, download the lightweight Gemma 2 model:

ollama pull gemma2:2b


(Wait for the download to reach 100% and display "success")

Step 5: Launch RepoPhantom

Return to your original terminal tab (where your venv is active) and start the application:

streamlit run phantom.py


The dashboard will automatically open in your browser at http://localhost:8501.

🛠️ 5. Troubleshooting & FAQ

Q: Why did pip install fail with error: externally-managed-environment on my Mac?
macOS locks the global Python installation (PEP 668). You must create and activate a virtual environment (python3 -m venv venv then source venv/bin/activate) before running pip install.

Q: Why does source venv/bin/activate say no such file or directory?
You likely haven't created the container yet, or you aren't in the project folder. Run cd Onboard-CLI, then python3 -m venv venv, and finally run the activate command.

Q: Why did Streamlit say Error: Invalid value: File does not exist: phantom.py?
Your terminal is in the wrong directory (likely on the Desktop). Run cd Onboard-CLI to enter the project folder before running streamlit run phantom.py.

Q: The web UI shows a yellow warning: "Ollama Python package not found" (on localhost:8503).
You have an older Streamlit server running outside of your virtual environment. Press Ctrl + C in your terminal to kill it, ensure you run source venv/bin/activate, install the packages (pip install streamlit ollama), and run Streamlit again.

Q: Why did ollama serve say listen tcp 127.0.0.1:11434: bind: address already in use?
This means the Ollama background engine is already running successfully on your machine. You do not need to run ollama serve again.

Q: Why does the code use modelname = "gemma2:2b" instead of just gemma2?
gemma2:2b is the ultra-fast, lightweight 2-billion parameter model perfectly optimized for laptops without dedicated GPUs. Your Python code string must exactly match the model tag you downloaded via ollama pull.

Q: Where is the "Generate Roadmap" button mentioned in the pitch?
In the UI, the button is labeled Generate onboarding guide under the General Onboarding tab.
