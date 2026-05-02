# Contributing to the Study Guide Generator

This kit is hand-authored by Alex Magginetti and shared with specific people he trusts. If you have it, you have his permission to use it. Improvements are welcome.

## How to suggest changes

The shortest path: **open a GitHub Issue** at https://github.com/alexmagginetti/study-guide-generator/issues. Describe what you'd change and why. The more concrete the better — point to specific lines in `GENERATOR.md` or to a real example output where the kit fell short.

If you want to write the change yourself: **fork the repo, make your edits, and open a pull request.** Keep pull requests small and focused — one logical change per PR is much easier to review than ten changes bundled together. The maintainer will review, ask questions, and either merge, request changes, or explain why he's going a different direction.

## Bug reports from real study runs

If you ran the kit through an AI and the output had a problem — hallucinated Hebrew, fabricated URL, theological mistake, formatting issue, link that doesn't work — please report it. The bug-report formatter at the end of the Master Prompt (Section D of `GENERATOR.md`) will produce a structured report you can paste directly into a GitHub Issue. Even one well-described bug is more valuable than a generic complaint.

## What kinds of contributions are most welcome

- Catching theological errors or denominational misrepresentations.
- Adding canonical doctrinal source URLs the kit doesn't yet have.
- Improving the QA Agent Prompt (Section F) to catch new categories of LLM failure modes.
- Adding example outputs to `EXAMPLES/` so the kit has more quality calibration material — especially non-Bible Christian works (e.g., a *Mere Christianity* chapter).
- Translation additions — if you can supply the canonical copyright notice for a translation not in the matrix and confirm its license tier, that saves the maintainer a lot of legal-research time.
- Distribution channel suggestions — pastors and small-group networks the kit could reach.

## What kinds of contributions are *not* a good fit

- Sweeping rewrites of the theological framing. The Lausanne Covenant baseline plus the SBC/DTS-default toggle structure is intentional. Adding a new toggle is fine; replacing the baseline is not.
- Changes that weaken the QA loop, the trust mini-script, or any of the six hard rules in the Instructions to the AI Model block.
- Adding ChatGPT/OpenAI to the recommended-providers list. The exclusion is intentional and based on the maintainer's conviction; please don't reopen it.
- Adding any external CDN or remote resource to the HTML template. The output stays self-contained for security and trust reasons.

## Contributor License posture

By submitting a pull request to this repository, you grant Alex Magginetti a perpetual, irrevocable, worldwide, royalty-free, non-exclusive license to incorporate your contribution into the project under whatever license terms the project is currently under or may be released under in the future. You retain copyright on your own contribution; this license simply lets the maintainer integrate your work without having to chase down individual contributors years from now if licensing terms change.

If you cannot agree to those terms, please open a GitHub Issue with your suggestion instead of a pull request, and the maintainer will incorporate the idea separately.

## Code of conduct

Be charitable with each other. Disagree about theology and method without becoming personal. Remember the people on the other side of the screen are reading along too. Keep discussion in Issues and pull-request comments focused on the kit itself, not on participants.

## Questions?

Open an Issue. If you'd rather reach the maintainer privately, the email associated with the GitHub account is the right channel.
