# Backlog

This is the prioritized, living backlog for the Study Guide Generator. It reconciles an original 20-gap review (first written against kit v1.4) against the current state of the kit, so that identified work is not lost between releases. Bug-class items are cleared as they are encountered and fixed; positioning and design items are recorded with a recommended next action and held until the maintainer makes a direction decision. This file is updated each release.

**Last reconciled: 2026-05-17 against kit v1.6**

---

## Resolved in v1.6

The following bug-class gaps were closed in v1.6:

- **Gap 3** — TESTS.md showed a stale kit version. Updated to v1.6.
- **Gap 4** — CONTRIBUTING.md ended mid-sentence. Completed, with a pointer to the maintainer's GitHub profile for private contact.
- **Gap 15** — GitHub username casing was inconsistent (`Alexmagginetti` vs `alexmagginetti`). Normalized to lowercase across the repository.
- **Gap 18** — The theological toggle-cap wording was ambiguous about whether the default SBC/DTS toggle counted toward the "max 2." Clarified: the Lausanne baseline is always on and does not count toward the cap; SBC/DTS is the default optional toggle and occupies one of the two optional slots unless it is changed or removed.

Two feature changes also shipped in v1.6 (not from the 20-gap review, recorded here for context):

- **F-A — Capability-surfacing gate.** The kit now always reflects the user's request onto the 8-card intake and shows full optionality before generating, even when the user supplies a detailed one-shot request.
- **F-B — QA independence ladder.** Three QA tiers are now defined: same-session self-review (the weakest, mandatory floor); manual external second-opinion review (stronger); and an automated context-isolated reviewer agent, e.g. a Claude Code subagent (strongest, recommended for group studies). **F-B partially closes Gap 5.**

---

## Open — positioning contradictions (maintainer decision)

These are the highest-priority open items: the kit currently makes contradictory claims about what it is and what it supports. They require a maintainer direction decision before implementation.

### Gap 1 — GENERATOR.md reads as Claude-Cowork-only while the kit promises cross-AI portability

**Status:** Open
**Class:** Positioning contradiction
**Detail:** "Before You Begin," Section A, and Section A-1 are still written as if the kit is Claude-Cowork-only ("a Claude account (Pro plan minimum)," "the Claude Desktop app installed," "Use Cowork for everything"), while the README and the cross-AI preamble promise Claude/Gemini/Grok portability. This is the largest internal inconsistency in the kit.
**Recommended next action:** Rewrite the intro, Section A, and Section A-1 to be AI-agnostic, presenting Cowork as one recommended path among several.
**Size:** L

### Gap 2 — Section J still lists ChatGPT/OpenAI as a working paid option

**Status:** Open
**Class:** Positioning contradiction
**Detail:** Section J lists ChatGPT/OpenAI as a working paid option, with pricing and a recommendation, while the README and CONTRIBUTING state that OpenAI is intentionally excluded. The section the README points to as the explanation does not actually contain the exclusion.
**Recommended next action:** Remove ChatGPT from the working-options list in Section J and instead document the exclusion, together with the reason (see Gap 12).
**Size:** M

### Gap 16 — Interactive hand-holding is documented only for Cowork

**Status:** Open
**Class:** Positioning contradiction
**Detail:** Section A-1 gives detailed interactive hand-holding only for Cowork. There is no parallel guidance for Gemini, Grok, or other browser-based AIs, despite the portability claim.
**Recommended next action:** Add a parallel "how the interview works on browser AIs" subsection.
**Size:** M

---

## Open — design / maintainer-judgment

These are design questions and judgment calls. Each carries a recommended direction but needs a maintainer decision.

### Gap 5 — QA pass is LLM-asserted, not third-party-verifiable (residual after F-B)

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** F-B adds a stronger isolated-reviewer ceiling, but the QA pass remains LLM-asserted. A downstream reader still cannot cryptographically verify that the QA actually ran.
**Recommended next action:** Consider an optional loggable QA transcript, or a forced "QA not run" disclaimer.
**Size:** M

### Gap 7 — Section F QA prompt is heavily Bible-specific

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The Section F QA prompt focuses on original-language fidelity, ESV fidelity, and BibleGateway links. For non-Bible Christian-book studies (the Mere Christianity path), those checks barely apply, and there is no parallel QA guidance.
**Recommended next action:** Add a non-Bible QA checklist branch.
**Size:** M

### Gap 8 — "Non-technical user" promise vs. real workflow friction

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The README promises a non-technical user experience, but the real workflow includes attaching files, a checksum verification a layperson cannot perform, and bracket-placeholder filename syntax.
**Recommended next action:** Lower-friction onboarding; explain or auto-handle the technical steps.
**Size:** M

### Gap 9 — Accessibility of generated HTML is unaddressed

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The generated HTML has collapsibles, notes areas, and depth toggles, but nothing addresses screen readers, keyboard navigation, contrast, ARIA, or font scaling. This is notable for a ministry tool.
**Recommended next action:** Add accessibility requirements to the EXAMPLES contract and to QA.
**Size:** M

### Gap 10 — Privacy claim is broader than the workflow supports

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The README's "no data collection / no network connections" claim is true of the HTML output, but the workflow runs through a hosted AI that retains chat logs, including group context. The blanket privacy claim may mislead.
**Recommended next action:** Scope the privacy claim precisely to the output artifact.
**Size:** S

### Gap 11 — License vs. contribution invitation tension

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The license is All Rights Reserved, while CONTRIBUTING invites forks and pull requests. Forking is technically reproduction, which creates a tension for downstream contributors.
**Recommended next action:** Clarify a fork-for-contribution grant, or reconsider the license.
**Size:** S (decision-heavy)

### Gap 12 — OpenAI/ChatGPT exclusion is asserted but not explained

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The OpenAI/ChatGPT exclusion is stated as a maintainer conviction but is never explained. An AI-skeptical audience may want the reasoning. The exclusion itself is not being reopened; only how clearly it is explained is in scope.
**Recommended next action:** Add a short, factual rationale paragraph.
**Size:** S

### Gap 13 — No version-pinning or rollback story

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** There is no guidance for what a user does if a new version regresses. CHECKSUMS covers only the current canonical version.
**Recommended next action:** Document tagged releases and how to pin to a known-good version.
**Size:** S

### Gap 17 — The Daniel proof-of-concept is invisible in the public repo

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The Daniel proof-of-concept — the cautionary tale behind the whole QA loop, and the source of Section F-1's named Hebrew hallucinations — is not present anywhere in the public repo.
**Recommended next action:** Consider shipping it as an inaugural recorded run under `EXAMPLES/test_runs/`.
**Size:** M

### Gap 19 — No kit-level telemetry or aggregate failure-mode learning

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** There is no kit-level telemetry or aggregate failure-mode learning; privacy-respecting telemetry is hard. The kit improves only via manually filed Issues.
**Recommended next action:** Flag as an open research question.
**Size:** L / uncertain

### Gap 20 — No documented succession plan

**Status:** Open
**Class:** Design / maintainer-judgment
**Detail:** The kit is solo-maintained with no documented succession plan. All Rights Reserved becomes a risk if the maintainer is unavailable, for a tool intended to outlast its author.
**Recommended next action:** Add a short succession / stewardship note.
**Size:** S (decision-heavy)

---

## Open — verification tasks (need live web/testing)

These require live testing or web verification before they can be closed.

### Gap 6 — No recorded cross-AI acceptance runs

**Status:** Open
**Class:** Verification task
**Detail:** TESTS.md describes a 10+-test acceptance suite and asks for recorded runs in `EXAMPLES/test_runs/test_run_YYYY-MM-DD_<provider>_<model>.md`, but that folder does not exist and no cross-AI run has ever been recorded. Portability to Claude/Gemini/Grok is claimed with zero recorded evidence.
**Recommended next action:** Record at least one run per named provider.
**Size:** M (ongoing)

### Gap 14 — GitHub Pages URL needs live verification

**Status:** Open
**Class:** Verification task
**Detail:** The README advertises a GitHub Pages URL (`alexmagginetti.github.io/study-guide-generator/GENERATOR.html`). This needs live verification that Pages is deployed and serving as advertised.
**Recommended next action:** Verify, and either fix the URL or fix the claim.
**Size:** S

---

## How to use this backlog

Bug-class items are cleared as they are encountered and fixed, the way Gaps 3, 4, 15, and 18 were in v1.6. Positioning and design items need a maintainer decision on direction before any implementation work begins. Verification tasks need live testing or web access to resolve. This file is reconciled and updated with each release so that the identified work is not lost between versions.
