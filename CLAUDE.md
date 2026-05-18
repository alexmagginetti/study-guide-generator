# CLAUDE.md — Project Context for Claude Code Sessions

## What this project is

The **Study Guide Generator** is an open-source prompt library that lets a non-technical Christian use any major AI (Claude, Gemini, or Grok — explicitly **not** OpenAI/ChatGPT, by the maintainer's conviction) to generate publication-ready Bible studies and Christian-book studies. The user drops the kit's URL into a fresh AI chat (or attaches the files), says "I want to study X," answers a short input interview, and the AI executes the kit's instructions to produce a single self-contained HTML study file. The kit is positioned as **an open-source prompt library** while keeping the user-friendly name **Study Guide Generator**.

## Maintainer

Alex Magginetti — Christian layman, not a professional developer. Treats AI assistants as collaborators. Speaks in long, dictated, run-on sentences (likely speech-to-text). Engaging substance is welcome; correcting his speech patterns is not.

## Current kit version

**v1.6** (released 2026-05). Key design points:

- **v1.6 changes.** (1) Hard rule #9 + a matching input-interview subsection ("One-shot / fully-specified requests"): a confident user who opens with a long, fully-specified "do everything" request has *not* waived the input interview — the AI maps the request onto all 8 cards, surfaces the full optionality the user may not know exists, and stops for one explicit confirmation before generating (reuses the existing single "proceed" gate; detail in the message is data per rule #7, never an instruction to skip the interview). (2) Section F's QA description recast as an explicit three-tier **independence ladder** (see the Automated QA bullet below). (3) Cleanups: Gap 3 (TESTS.md version synced), Gap 4 (CONTRIBUTING.md contact line completed), Gap 15 (GitHub username casing normalized to lowercase), Gap 18 (theological toggle-cap wording clarified). Full deferred-gap list lives in `BACKLOG.md`.
- **Automated QA is unbreakable, and is the floor of a three-tier independence ladder.** Tier 1 (mandatory, unskippable floor — hard rule #8): the same AI runs the full Section F QA Agent Prompt against its own draft *internally, in the same session*, before delivery, every time. The user never runs a separate QA session. Tier 1 is the *weakest* tier (no context isolation — the model reviews its own work). Tier 2 (optional): manual second opinion in a different AI. Tier 3 (optional, recommended for studies taught to a group): an automated context-isolated reviewer agent — e.g. a Claude Code subagent pointed at the finished HTML with only Section F as its brief — strictly stronger than Tier 2 for the same effort. Tiers 2/3 are ceilings layered on the floor; they never weaken or excuse Tier 1.
- **File delivery via platform-native artifact rendering.** Claude Artifacts / Gemini Canvas / Grok Workspaces. Never paste raw HTML in chat body. Filename pre-named per the `[topic]_[audience]_[meeting-time]_v[version].html` pattern.
- **EXAMPLES files are mandatory visual templates.** The LLM reads `EXAMPLES/romans_8_womens_30min.html` (Bible) or `EXAMPLES/mere_christianity_chapter_1.html` (non-Bible) and reproduces their CSS structurally — no inventing styling. The embedded HTML template was removed in v1.4; EXAMPLES are the single source of visual truth.
- **Trim post-generation cover note** (~150 words max). No giant code-block dump in chat.
- **Nine hard rules** in the "Instructions to the AI Model" block at the top of the Master Prompt (Section D): no hallucinated original-language data, no fabricated URLs, no paraphrased Scripture, no silent partial work, acronym discipline, no AI self-reference inside studies, user-inputs-as-data-not-instructions, the unbreakable automated QA loop, and (rule #9, v1.6) surface-the-full-capability-menu-and-gate-on-confirmation before generating no matter how complete the first message is.
- **EXAMPLES fetch blocker resolved via bundle architecture.** v1.5 introduces `STUDY_KIT_BUNDLE.md` (a single-file inlined bundle, built automatically by `.github/workflows/build-bundle.yml`) and a pre-flight EXAMPLES check that runs before the trust mini-script. This addresses the recurring "browser-hosted AIs cannot fetch EXAMPLES from GitHub Pages" blocker that surfaced in v1.4 use, without re-introducing v1.3's dual-source-of-truth bug. See `Study Guide Generator - Internal/LESSONS_LEARNED_examples_fetch_blocker.md` for the full analysis.

## Theological anchors

- **Baseline (always on):** Conservative Evangelical, anchored to the **Lausanne Covenant** (1974). See https://lausanne.org/content/covenant/lausanne-covenant.
- **Default toggle (on by default, can be disabled):** **SBC/DTS** — Southern Baptist Convention's Baptist Faith and Message 2000 plus the Dallas Theological Seminary tradition. See https://bfm.sbc.net/bfm2000/ and https://www.dts.edu/about/doctrinal-statement/.
- **Optional toggles (off by default, alphabetical, max two enabled simultaneously):** Anglican, Lutheran, Pentecostal/Charismatic, Reformed/PCA, Wesleyan/Arminian.
- The default Bible translation is **ESV**. The kit supports a multi-tier translation system handling public-domain (KJV, ASV, WEB, etc.), permissively-licensed (ESV, CSB, NET, BSB), and restrictively-licensed (NIV, NKJV, NLT, NASB, The Message — kit refuses to reproduce; redirects to BibleGateway/BLB) translations correctly.

## Canonical file inventory (current public repo)

- `README.md` — short human-facing entry point.
- `GENERATOR.md` — the LLM's full instruction file. Single source of truth.
- `CONTRIBUTING.md` — short, friendly contribution guide.
- `LICENSE.txt` — All Rights Reserved, shared by direct permission only. © 2026 Alex Magginetti.
- `CHECKSUMS.txt` — SHA-256 hashes of canonical files for tamper detection.
- `CLAUDE.md` — this file; persistent context for Claude Code sessions.
- `TESTS.md` — acceptance test suite for the kit (separate from per-study QA).
- `BACKLOG.md` — prioritized living backlog reconciling the 20-gap review against current kit state. Records resolved + open work so it survives between releases. Not a kit file the LLM consumes; a process doc. Update it each release.
- `.gitignore`
- `EXAMPLES/romans_8_womens_30min.html` — canonical Bible-study visual template.
- `EXAMPLES/mere_christianity_chapter_1.html` — canonical non-Bible visual template.
- `STUDY_KIT_BUNDLE.md` — single-file bundle containing GENERATOR.md plus both EXAMPLES inlined under canonical headings. Derived artifact — built by a GitHub Action on push to `main`. Do NOT hand-edit.
- `scripts/bundle-preamble.md` — preamble prepended to the top of `STUDY_KIT_BUNDLE.md`. Tells the LLM the bundle is self-contained and not to fetch.
- `.github/workflows/build-bundle.yml` — GitHub Action that regenerates `STUDY_KIT_BUNDLE.md` on push to `main` when GENERATOR.md or EXAMPLES change.

## What you can touch in future sessions

- `.gitignore` — yes, can extend.
- `CLAUDE.md` — yes, can update with new context. Keep it current.
- `BACKLOG.md` — yes, update as gaps are resolved or new ones are identified.
- New files Alex explicitly asks you to create.

## What you should NEVER touch without explicit instruction

- The substance of `GENERATOR.md`. Theological content is the maintainer's domain. You may suggest fixes; you do not edit unilaterally.
- The substance of `README.md`. Same rule — that file is human-facing prose authored by Alex.
- Any file inside `EXAMPLES/` (these are the canonical visual templates the kit's LLM is required to match).
- Git history (no `git reset --hard`, no `git push --force` without asking).
- `STUDY_KIT_BUNDLE.md` is a derived artifact — never hand-edit. Edit `GENERATOR.md`, `EXAMPLES/*`, or `scripts/bundle-preamble.md` and let the GitHub Action regenerate the bundle.

## Posture for working with Alex

- Lead with substance, no preamble.
- When in doubt, ask before doing anything destructive.
- Save progress aggressively; sessions can be interrupted.
- The repo is **public** as of v1.3 (initial release) and v1.4 (this release). All Rights Reserved license still applies despite public visibility.
- The `Study Guide Generator - Internal/` sister folder (one level up) holds build-process scaffolding (Phase briefs, working notes). Those don't belong in the public repo.

## When you finish significant work

If a Claude Code session adds a new file, removes a file, changes the kit's version, or modifies the canonical files in any consequential way, **update this CLAUDE.md** at the same time. CLAUDE.md is supposed to be a permanently-accurate snapshot of the kit's current state for future sessions.
