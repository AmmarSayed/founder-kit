# founder-kit

A simple, personal, **cross-AI** framework for taking an idea → a shipped product, working *with* AI agents.

**It's a template repo: clone (or copy) it into each new project.** The core is plain markdown, so Claude, Codex, Cursor — or any AI that reads `AGENTS.md` — can run it.

## How to use it

Clone it per project, drop your inputs in, then just **talk** to your AI (no special commands needed):

```
git clone <this-repo> MyProject
cd MyProject
# (drop in any data/sources)
claude          # or codex, or open the folder in your AI tool
```

## The flow

```
Default:  Frame → Spec → Build → Review → Ship
Heavy:    Frame → Research → Decide → Prototype → Spec → Build → Review → Ship
          (use Heavy when you don't know the topic, or it's big / greenfield)
```

- **Frame** — brainstorm + answer one question: *"What's the cheapest way to invalidate this idea before building?"* → fill `project.md`.
- **Research** (Heavy) — gather **cited** sources into `evidence.md` (deep research + NotebookLM). Build only from this.
- **Spec** — in `project.md`: key trade-offs, a phased MVP, edge-cases. Proportional — brief for small work.
- **Build** — implement; **synthetic/sample data first**; always include a run/check command.
- **Review** — `/kit-review` (Codex) → `review.md`; fix Blocking findings.
- **Ship** — swap in real data + push (**with your approval**).

## The team (just talk — these are hats, used in sequence)

- **Lead** — brainstorm, frame, route, synthesize (does **not** implement)
- **Builder** — implements from the brief
- **Reviewer** — Codex, independent check

## Files

- **`AGENTS.md`** — the rules every AI reads first (the "constitution"). **Start here.**
- **`project.md`** — this project's contract (problem/output/acceptance + Spec + Status + Tasks).
- **`project-start.md`** — a pre-filled quick-start for a one-page HTML dashboard (`copy project-start.md project.md` to start fast).
- **`review.md`** — the review verdict + findings.
- **`evidence.md`** — cited research ground truth (create in Heavy mode).

## Cross-AI

`AGENTS.md` is the single source of truth. In Claude Code, `CLAUDE.md` imports it. Codex reads the project's `AGENTS.md` directly (optionally mirror to `~/.codex/AGENTS.md`). Cursor/Gemini: point their rules file at `AGENTS.md`.

## Reuses installed skills

`frontend-design` (web/UI) · `playground` (explore) · Codex `presentations`/`spreadsheets` (pptx/xlsx) · `deep-research` + NotebookLM (research) · `pr-review-toolkit` (deep review) · `commit-commands` (ship). The only skill this repo *authors* is `codex-review`.

*Lightweight spec-driven method (the "spec-kit" methodology in plain files — no extra tooling to install).*
