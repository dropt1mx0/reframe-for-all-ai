# Universal `/reframe` + `/sharpen` Skill for All AI

[![Works With](https://img.shields.io/badge/Works%20With-Cursor%20%7C%20Claude%20Code%20%7C%20Windsurf%20%7C%20Gemini%20%7C%20ChatGPT-2563eb?style=for-the-badge)](https://github.com/dropt1mx0/reframe-for-all-ai)
[![Format](https://img.shields.io/badge/Standard-SKILL.md-16a34a?style=for-the-badge)](#installation--setup)
[![License: MIT](https://img.shields.io/badge/License-MIT-7c3aed?style=for-the-badge)](LICENSE)

> **Stop getting fragile spaghetti code from AI.** Translate rough "vibe-coding" ideas into domain-accurate engineering specs, architectural guardrails, and verifiable execution plans — before a single line of code is written.

Inspired by xAI's `pstack` `/reframe` and `/sharpen` workflow, rebuilt as a **platform-agnostic, zero-dependency skill** that works across every major AI coding IDE and chat assistant.

---

## Why This Exists

When you build software outside your core specialty (audio/video processing, real-time sync, fintech, scraping, compilers), you don't know what you don't know.

If your prompt omits industry terms like **Voice Activity Detection (VAD)**, **Non-Destructive Editing (EDL)**, or **Idempotency Keys**, coding agents fill the gaps with naive, brittle workarounds that collapse as soon as you add a second feature.

### Before vs. After `/reframe`

| Without `/reframe` (Typical Prompt) | With `/reframe` + `/sharpen` |
| :--- | :--- |
| *"Build a web video editor that cuts out silent pauses automatically."* | Maps domain to **VAD (Silero / WebRTC)**, **Non-Destructive EDL (Edit Decision List)**, **WebCodecs / FFmpeg.wasm**, and **Waveform Peak Caching**. |
| Agent re-encodes the entire video on every cut, freezes the browser main thread, and breaks undo/redo. | Explicitly bans destructive file overwrites, moves processing to a **Web Worker**, separates timeline JSON state from media buffers, and outputs a **5-step build pipeline with Definition of Done tests**. |

---

## How the 6-Stage Protocol Works

When triggered, the AI switches into **Principal Software Architect** mode and refuses to write implementation code until the problem is properly framed:

1. **Intent & Domain Mapping** — Extracts hidden requirements and teaches 4–7 critical industry terms you missed, explained in plain language.
2. **Blind Spots, Edge Cases & Trade-offs** — Surfaces failure modes (memory leaks, race conditions, rate limits, state desync) and explicit architectural choices calibrated to your project scale (MVP vs. Production).
3. **Prior Art & Proven Stack** — Points to real open-source benchmarks, libraries, or RFC patterns worth borrowing.
4. **The Reframed Spec** — Outputs a single, copy-pasteable engineering prompt with data models, architectural rules, and explicit **DO NOTs (anti-patterns)**.
5. **Sharpen Protocol** — Breaks the build into 4–6 atomic milestones with verification checkpoints and testable **Definition of Done** assertions.
6. **Decision Forks** — Asks 2–3 high-leverage multiple-choice questions (with recommended defaults) to lock in Iteration 2.

### Optional Mode Modifiers

* `/reframe <idea>` — Standard full 6-stage architecture & sharpen cycle.
* `/reframe --lite <idea>` — Compact 3-block version for small features or scripts.
* `/reframe --deep <idea>` — Full RFC-grade analysis with trade-off matrix and failure recovery.
* `/reframe --sharpen-only <spec>` — Skip terminology mapping; go straight to execution order and acceptance tests.

---

## Installation & Setup

### 1. Cursor
Place `SKILL.md` in your project or global skills directory:
```bash
mkdir -p .cursor/skills/reframe
cp reframe/SKILL.md .cursor/skills/reframe/SKILL.md
```
*Alternative:* Add its contents to `.cursor/rules/reframe.mdc`.

### 2. Claude Code
```bash
mkdir -p .claude/skills/reframe
cp reframe/SKILL.md .claude/skills/reframe/SKILL.md

# For a global installation:
mkdir -p ~/.claude/skills/reframe
cp reframe/SKILL.md ~/.claude/skills/reframe/SKILL.md
```

### 3. Windsurf / Cline / Roo Code / GitHub Copilot
Copy the body of `reframe/SKILL.md` into your agent's rules file:
* **Windsurf:** `.windsurf/rules/reframe.md` (or `.windsurfrules`)
* **Cline / Roo Code:** `.clinerules` or `.roo/rules/reframe.md`
* **GitHub Copilot:** `.github/copilot-instructions.md`

### 4. Gemini (Gems), ChatGPT (Custom GPTs), Claude Projects
Use the **Two-Window Architect Pattern**:
1. Create a dedicated **Gem**, **Custom GPT**, or **Claude Project**.
2. Paste the contents of `reframe/SKILL.md` into **System Instructions**.
3. Describe your raw idea in this Architect chat.
4. Copy the generated **Reframed Spec** (Stage 4) and **Execution Pipeline** (Stage 5) into a fresh coding session for clean, zero-noise code generation.

---

## Usage Example

```text
/reframe I want to build a lightweight web app where friends can watch YouTube videos together and stay synced even if someone pauses or has bad internet
```

The agent will automatically map concepts like **Drift Compensation**, **Server-Authoritative Playback Clock**, **WebSockets + Heartbeat RTT estimation**, and **Optimistic UI with Debounced Seek**, then hand you a ready-to-build engineering prompt. The skill answers in the user's language and keeps canonical engineering terms in English.

A Russian translation is available in [reframe/SKILL.ru.md](reframe/SKILL.ru.md).

---

## Repository Structure

```text
.
├── LICENSE
├── README.md
└── reframe/
    ├── SKILL.md        # English core /reframe + /sharpen skill
    └── SKILL.ru.md     # Russian translation
```

---

## Contributing

Pull requests are welcome! High-impact contributions:
* Domain-specific add-ons (GameDev, ML Pipelines, Fintech, Embedded, Mobile)
* Real before/after `/reframe` case studies
* Translations and IDE-specific install scripts

If this skill saved you from rewriting an entire AI-generated codebase, consider dropping a star!
