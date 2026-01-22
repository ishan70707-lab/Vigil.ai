# Vigil.ai
### The Multi-Modal Therapeutic Council & Proactive Sentinel System

**Vigil.ai** is a next-generation therapeutic AI designed to solve the "Goldfish Memory" problem inherent in standard Large Language Model (LLM) chatbots. Unlike reactive systems that reset context with every session, Vigil maintains a persistent memory core and employs a **Multi-Agent Cognitive Architecture** to analyze user distress through distinct psychological lenses (Empathy, Logic, and History).

Crucially, Vigil is **Proactive**. It features a background "Sentinel" system that monitors user well-being even when the application is closed. By analyzing historical memory data for distress patterns or "open loops" (e.g., missed high-stakes events), Vigil autonomously dispatches context-aware "nudge" notifications via email, transforming the AI from a passive tool into an active guardian of mental well-being.

---

## Key Features

### 1. Multi-Agent Cognitive Architecture
Instead of relying on a single LLM prompt, Vigil triangulates responses using a "Council" of specialized agents running in parallel:
* **The Validator:** A specialized agent that prioritizes emotional resonance and validation, ensuring the user feels heard before solutions are offered.
* **The Challenger:** A Cognitive Behavioral Therapy (CBT) specialist that identifies and counters cognitive distortions (e.g., catastrophizing).
* **The Historian:** Retrieves specific past context to create a seamless, long-term therapeutic relationship.

### 2. Proactive Safety Monitoring (The Sentinel)
* **Background Scanning:** A scheduled asynchronous process scans recent memories for high-distress trends.
* **Open Loop Detection:** Identifies unclosed events (e.g., "I have surgery tomorrow") and flags them for follow-up.
* **External Intervention:** Autonomously drafts and sends context-aware HTML emails to check in on the user if they go silent during a crisis.

### 3. Persistent Contextual Memory
* **Hybrid Database:** Utilizes **Qdrant** for semantic vector search (concepts) combined with a custom **Lexical Rescue** engine (keywords). This ensures the system retains specific details like names, dates, and triggers across sessions.

### 4. Multi-Modal Accessibility
* **Voice-First Design:** Users can interact via natural speech using audio files.
* **STT/TTS Integration:** Powered by **Groq Whisper-v3** (Input) and **gTTS** (Output) to facilitate hands-free therapeutic sessions.

---

## System Architecture

The system operates on a Hub-and-Spoke model orchestrated by a central logic unit.

1.  **Input Layer:** Normalizes Text or Audio inputs (transcribed via Whisper).
2.  **Orchestrator:** Determines the user's psychological state (e.g., Venting vs. Probing) and routes tasks accordingly.
3.  **Cognitive Council:** Manages the parallel execution of Validator, Challenger, and Historian agents.
4.  **Memory Core:** Handles Read/Write operations to the local Vector Database.
5.  **Sentinel Layer:** Performs asynchronous safety checks and email dispatch.

---

## Technology Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **LLM Inference** | **Groq API** | Ultra-fast inference (<0.5s) for Llama-3.1 & Whisper. |
| **Vector DB** | **Qdrant** | Local RAM-based semantic memory storage. |
| **Embeddings** | **SentenceTransformers** | `all-MiniLM-L6-v2` for text-to-vector encoding. |
| **Orchestration** | **Python Futures** | Managing parallel multi-agent execution. |
| **Voice** | **gTTS / Pygame** | Text-to-Speech generation and playback. |
| **Notifications** | **SMTP (Gmail)** | Sending proactive HTML wellness emails. |

---

## How to Run

This project is designed as a self-contained **Google Colab Notebook** for immediate deployment without local environment configuration.

1.  **Open the Notebook:** Locate the file `Vigil_AI_Final.ipynb` in this repository and open it in Google Colab.
2.  **API Configuration:** You will need a Groq API Key (available at console.groq.com).
3.  **Execution:**
    * Run all cells in order. The notebook automatically handles the installation of dependencies (`groq`, `qdrant-client`, `sentence-transformers`, etc.).
    * Enter your API Key when prompted by the secure input field.
4.  **Interaction:** The chat interface will initialize directly within the notebook output area.

*(Optional)*: To enable the **Sentinel Email** feature, update the `EmailDispatcher` configuration cell with valid SMTP credentials before running the final execution block.

---

## Privacy & Safety

* **Local Storage:** All memories are stored in a local Qdrant instance (`:memory:` mode). Data is ephemeral to the runtime session and is not transmitted to external storage.
* **Transparency:** The system includes a "Glass Box" logging feature, printing the internal reasoning of the Validator and Challenger agents to the console for transparency.

---

## Authors

* **Ishan Singh**
* **Daksh Dadeech**

---

## License
This project is licensed under the MIT License - see the LICENSE file for details.
