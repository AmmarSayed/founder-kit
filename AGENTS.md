# AGENTS.md — founder-kit project contract (read first, every session)

Purpose: build & ship ONE artifact, defined in `project.md`. You are the **Lead/orchestrator + Builder**; route work to a skill, a review pass, or an agent. You are **not a persona** — no role-play.

## Flow (modes)
- **Default:** Frame → Spec → Build → Review → Ship
- **Heavy** (unfamiliar topic / big / greenfield): Frame → Research → Decide → Prototype → Spec → Build → Review → Ship

Depth is **proportional**: a tiny change gets a one-line Spec; a real feature gets a fuller one. Never skip the thinking; never add ceremony a task doesn't need.

## Roles (sequential hats — NOT parallel agents)
- **Lead** — brainstorm, frame, route, synthesize. Writes the brief into `project.md`. **Does NOT implement.**
- **Builder** — implements from the Lead's brief, using skills.
- **Reviewer** — Codex (independent). Run via `/kit-review` or the `codex-review` skill.

## Environment (hard — locked-down Windows)
- **NO admin rights.** Portable Git + WinPython only.
- DO: WinPython venvs, `pip install --user`, single-file HTML, portable binaries.
- DON'T: Docker, WSL, global npm installs, registry edits, system-PATH changes. If one seems needed → **STOP and ask.**

## Safety gates — human approval BEFORE:
- deleting/overwriting files you didn't create
- adding a dependency
- `git push`
- touching REAL data (default to **synthetic/sample** data; never commit confidential/client data)

Also: edits stay inside THIS project folder. Research/review tooling (WebSearch, NotebookLM, Codex) is pre-approved; the *built artifact* must not call external services without approval.

## Build rule
Every build ships with a **run/check command** (how to see it work). No "done" without it.

## Version control (git workflow)
- One **git repo per project**.
- **One branch per feature/task** — `git checkout -b feature/<slug>` *before* building.
- Make small, working commits on that branch as you go.
- **Merge to `main` only after Review passes** (Verdict: Pass): `git merge --no-ff feature/<slug>`, then delete the branch.
- `git push` only with explicit approval (see Safety gates).

## The ladder (default to the lowest rung)
1. Always-true rule → put it here in `AGENTS.md`.
2. Reusable know-how → a **skill**.
3. One-time check → a **review pass**.
4. Needs its own context/tools → an **agent** (only the Codex reviewer is named).

## Spec-driven (the method, in our files — no external tool)
constitution = this file · specify/clarify = Frame + `project.md` · plan = the Spec's trade-offs / phased-MVP · analyze = the review gate · tasks = `## Tasks` · implement = Build.

## Review before shipping
Run the Codex review; resolve all **Blocking** findings in `review.md`. For **unfamiliar/educational** content, verify every claim against `evidence.md` and its citations.

## Tools to reach for
explore → `playground` · research → deep-research + NotebookLM (→ `evidence.md`) · build web/UI → `frontend-design` · pptx/xlsx → Codex `presentations`/`spreadsheets` · review → `codex review` (+ `pr-review-toolkit` for deep) · commit → `commit-commands`.
