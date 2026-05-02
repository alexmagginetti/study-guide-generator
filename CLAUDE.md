# CLAUDE.md — Project Context for Claude Code Sessions

## What this project is

The **Study Guide Generator** is an open-source prompt library that lets a non-technical Christian use any major AI (Claude, Gemini, or Grok — explicitly **not** OpenAI/ChatGPT, by the maintainer's conviction) to generate publication-ready Bible studies. The user drops the kit's files into a fresh AI chat (or points the AI at the GitHub raw URL), says "I want to study X," and the AI executes the kit's instructions to produce a single self-contained HTML study file. The kit is positioned as **an open-source prompt library** while keeping the user-friendly name **Study Guide Generator**.

## Maintainer

Alex Magginetti — Christian layman, not a professional developer. Treats AI assistants as collaborators. Speaks in long, dictated, run-on sentences (likely speech-to-text). Engaging substance is welcome; correcting his speech patterns is not.

## Theological anchors

- **Baseline (always on):** Conservative Evangelical, anchored to the **Lausanne Covenant** (1974). See https://lausanne.org/content/covenant/lausanne-covenant.
- **Default toggle (on by default, can be disabled):** **SBC/DTS** — Southern Baptist Convention's Baptist Faith and Message 2000 plus the Dallas Theological Seminary tradition. See https://bfm.sbc.net/bfm2000/ and https://www.dts.edu/about/doctrinal-statement/.
- **Optional toggles (off by default, alphabetical, max two enabled simultaneously):** Anglican, Lutheran, Pentecostal/Charismatic, Reformed/PCA, Wesleyan/Arminian.
- The default Bible translation is **ESV**. The kit supports a multi-tier translation system handling public-domain (KJV, ASV, WEB, etc.), permissively-licensed (ESV, CSB, NET, BSB), and restrictively-licensed (NIV, NKJV, NLT, NASB, The Message — link out only, do not reproduce) translations correctly.

## File inventory (as of Phase 2A)

- `README.md` — short human-facing entry point; under 250 words.
- `GENERATOR.md` — the LLM's full instruction file. The user does not need to read this; their AI does.
- `PHASE_2A_CLAUDE_CODE_BRIEF.md` — this brief (you are executing it).
- `Bible_Study_Generator_v1.1_FINAL.docx` — STALE pre-v1.2 artifact. Phase 2B regenerates this from the current GENERATOR.md and the old one will be replaced. You do not need to touch it.
- `EXAMPLES/daniel_unit_01.html` — proof-of-concept finished study.
- `EXAMPLES/daniel_unit_01_qa_report.txt` — QA report from the proof-of-concept run.
- `for_gemini/` — packet that was handed to Gemini for competitive analysis. Snapshot.

## Future file inventory (after Phase 2B)

- `LICENSE.txt` — currently All Rights Reserved; subject to maintainer's decision.
- `CONTRIBUTING.md` — short, friendly contribution guide.
- `CHECKSUMS.txt` — SHA-256 hashes of canonical files for tamper detection.
- A regenerated `.docx` companion replacing the stale one.

## What you can touch in future sessions

- `.gitignore` — yes, can extend.
- `CLAUDE.md` — yes, can update with new context.
- New files Alex explicitly asks you to create.

## What you should NEVER touch without explicit instruction

- The substance of `GENERATOR.md`. Theological content is the maintainer's domain. You may suggest fixes; you do not edit unilaterally.
- The substance of `README.md`. Same rule — that file is human-facing prose authored by Alex.
- Any file inside `EXAMPLES/`.
- The `for_gemini/` folder.
- Git history (no `git reset --hard`, no `git push --force` without asking).

## Posture for working with Alex

- Lead with substance, no preamble.
- When in doubt, ask before doing anything destructive.
- Save progress aggressively; sessions can be interrupted.
- The repo stays private until Alex explicitly says to make it public. He has not yet decided on a final license.
