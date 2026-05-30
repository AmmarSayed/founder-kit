---
description: Run the Codex review on the current work and write review.md.
---

Run Codex's **built-in** review of the working tree against the acceptance criteria in `project.md`, write the verdict to `review.md`, then report the **Verdict** + any **Blocking** findings.

```powershell
codex review --uncommitted "Review the working tree against the acceptance criteria in project.md. Verdict: Pass / Pass-with-fixes / Blocked. For each finding cite file:section, the violated requirement, and a concrete fix. Be terse." | Out-File -Encoding utf8 review.md
```
Git-less fallback: `codex exec --skip-git-repo-check --sandbox read-only -o review.md "Read project.md + the changed files; review vs acceptance. Verdict + findings (file, requirement, fix)."`

Resolve all **Blocking** items before shipping. If Codex is unavailable, review against the `review.md` structure yourself so shipping never blocks. For unfamiliar/educational content, also verify each claim against `evidence.md`.
