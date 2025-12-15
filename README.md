# Kael: The Recursive Logic Architect (v3.2 Platinum)

![Version](https://img.shields.io/badge/Version-v3.2_Platinum-blue?style=flat-square) ![Target](https://img.shields.io/badge/Target-Gemini_Enterprise_%2F_Advanced-green?style=flat-square) ![Architecture](https://img.shields.io/badge/Architecture-Evaluator--Optimizer-purple?style=flat-square)

**Kael** is a high-fidelity System Prompt designed for **Gemini Enterprise / Advanced**. It transforms the LLM from a conversational chatbot into a **Recursive Logic Engine** capable of self-verification, deep architectural planning, and autonomous research.

> **Core Philosophy:** *Verification > Generation.* Never trust latent knowledge without an external citation.

---

## 🧠 System Architecture

Kael is not a standard "Persona." It is a **Virtual Operating System** running inside the context window. It overrides default RLHF (helpfulness) behaviors with a strict **Finite State Machine (FSA)** that forces "System 2" thinking.

### The Neural Toolkit
Kael operates using three specific cognitive patterns derived from SOTA research:
1.  **Evaluator-Optimizer (Reflexion):** It does not just write code; it writes, audits, fails, and corrects itself in a loop before showing you the result.
2.  **Tree-of-Thought Planning:** Before executing a task, it generates multiple architectural approaches and selects the optimal path.
3.  **Least-to-Most Decomposition:** Complex tasks are broken into atomic, isolated sub-steps to reduce hallucination.

### The Lifecycle (State Machine)
Unlike linear prompts, Kael moves through immutable states:
* **S0 (Ingestion):** Analyzes intent and selects a specific "Mode."
* **S1 (Orchestration):** Researches and builds a Strategy/Plan. **(Stops for User Approval)**.
* **S2 (Convergence):** Executes the plan using the Cyclic Logic loop.
* **S3 (Termination):** Flushes short-term memory for the next task.

---

## 🛠️ Operational Modes

Kael is strict. It does not guess your intent. It relies on **Trigger Keywords** at the start of your prompt to load specific neural circuits.

| Mode | Trigger Keyword | Function | S1 Output Schema |
| :--- | :--- | :--- | :--- |
| **New Build** | `NEW_BUILD` | Creating architectures, codebases, or complex logic from scratch. | **Requirements Matrix** + Strategy Plan |
| **Refactor** | `REFACTOR` | Optimizing existing code/text. Requires a source input. | **SWOT Audit** (Strengths/Weaknesses) + Refactor Plan |
| **Direct** | `OVERRIDE` | Bypasses the Planning Phase (S1) for immediate answers. | *None* (Jumps to Execution) |

---

## 🚀 Installation & Usage

### 1. Prerequisite
You must have access to **Gemini Advanced** (with Thinking Mode) or **Gemini Enterprise** (Google Workspace). This prompt relies on large context windows and high-reasoning capabilities.

### 2. Injection
1.  Copy the full XML content from `kael_v3.2_system_prompt.xml`.
2.  Open **Gemini System Instructions** (or "Custom Instructions" in your API settings).
3.  Paste the XML raw.
4.  Save.

### 3. Verification
Start a new chat. Kael should immediately silence the default "Hello!" and output his CLI Boot Sequence:

```yaml
KAEL_CORE_SYSTEM: ONLINE
-----------------------
[✔] KNOWLEDGE_ENGINE:   ACTIVE (Deep Research Enabled)
[✔] LOGIC_CORE:         RECURSIVE (Evaluator-Optimizer Loaded)
[✔] USER_CONTEXT:       STAFF_ENGINEER (High-Bandwidth Protocol)
[✔] MODE_SELECTOR:      READY (New_Build / Refactor / Override)

> Awaiting Directive...