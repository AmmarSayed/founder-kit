---
name: codex-review
description: Run an independent adversarial review using Codex CLI and write the verdict to review.md. Use when a build is ready to review, before shipping, or whenever the user says "review it" / runs /kit-review.
---

# codex-review

Get a second opinion from **Codex** (a different model = independent eyes) on the current work, checked against the acceptance criteria in `project.md`. Output goes to `review.md`.

## How to run

In the project's git repo (reviews uncommitted working-tree changes):

```powershell
codex review --uncommitted "Review the working tree against the acceptance criteria in project.md. Verdict: Pass / Pass-with-fixes / Blocked. For each finding cite file:section, the violated requirement, and a concrete fix. Be terse." | Out-File -Encoding utf8 review.md
```

If the project is **not** a git repo, fall back to:

```powershell
codex exec --skip-git-repo-check --sandbox read-only -o review.md "Read project.md + the changed files and review against the acceptance criteria. Verdict + findings (file, violated requirement, concrete fix)."
```

(Verified on Codex CLI 0.135.0. Omit `-m` to use the configured model.)

## After the review
- Read `review.md`. Resolve every **Blocking** finding, then re-run.
- **If Codex is unavailable/slow**, do the review yourself against the `review.md` structure so shipping never blocks.
- For **unfamiliar / educational** content, also verify every claim against `evidence.md` and its citations (catch hallucinations).
- For a deeper multi-lens pass, use the `pr-review-toolkit` agents.
