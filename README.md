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

## The flow  (one flow that scales — add steps only when needed)

```
Default:  Frame → Spec → Build → Review → Ship
Heavy:    Frame → Research → Decide → Prototype → Spec → Build → Review → Ship
          (same flow + a few extra steps; use it when the topic is unfamiliar, big, or greenfield)
```

- **Frame** — brainstorm + answer one question: *"What's the cheapest way to invalidate this idea before building?"* → fill `project.md`, and start the feature branch: `git checkout -b feature/<slug>`.
- **Research** (Heavy) — gather **cited** sources into `evidence.md` (deep research + NotebookLM). Build only from this.
- **Spec** — in `project.md`: key trade-offs, a phased MVP, edge-cases. Proportional — brief for small work.
- **Build** — implement; **synthetic/sample data first**; always include a run/check command.
- **Review** — `/kit-review` (Codex) → `review.md`; fix Blocking findings.
- **Ship** — once Review passes: **merge the feature branch → `main`** (`git merge --no-ff feature/<slug>`), swap in real data, and push (**with your approval**).

## The team (just talk — these are hats, used in sequence)

- **Lead** — brainstorm, frame, route, synthesize (does **not** implement)
- **Builder** — implements from the brief
- **Reviewer** — Codex, independent check

## Commands (optional — Claude Code shortcuts)

You don't need these — **plain language works** ("frame this…", "build it", "review it with codex") in any AI. They're just one-keystroke shortcuts in Claude Code:

- **`/kit-start <what you want to build>`** — **Frame** a new task (Lead hat): brainstorm, ask the one forcing question, pick Default/Heavy mode, and fill `project.md`. Stops for your GO before building.
- **`/kit-review`** — run the independent **Codex review** of the current work → `review.md`, then report the Verdict + any Blocking findings.

In Codex / Cursor / other AIs (no slash-commands), just say *"frame this…"* or *"review it with codex"* — `AGENTS.md` drives the same flow.

## Files

- **`AGENTS.md`** — the rules every AI reads first (the "constitution"). **Start here.**
- **`project.md`** — this project's contract (problem/output/acceptance + Spec + Status + Tasks).
- **`project-start.md`** — a pre-filled quick-start for a one-page HTML dashboard (`copy project-start.md project.md` to start fast).
- **`review.md`** — the review verdict + findings.
- **`evidence.md`** — cited research ground truth (create in Heavy mode).

## Cross-AI

`AGENTS.md` is the single source of truth. In Claude Code, `CLAUDE.md` imports it. Codex reads the project's `AGENTS.md` directly (optionally mirror to `~/.codex/AGENTS.md`). Cursor/Gemini: point their rules file at `AGENTS.md`.

## Skills it reuses (not bundled — they live in your AI tool)

founder-kit stays tiny on purpose: instead of shipping its own tools, it **leans on skills/plugins you've already installed** in Claude Code and Codex. This repo is just markdown — it authors **no skills of its own**; every capability below already exists in your AI tools and is invoked automatically when a step needs it.

| Step in the flow | Skill / plugin used | What it does | Comes from |
|---|---|---|---|
| **Explore** (Frame) | `playground` | build a single-file interactive explorer to settle a layout/option → copy out a prompt | Claude plugin (Anthropic) |
| **Research** (Heavy) | `deep-research` + **NotebookLM** | gather + verify **cited** sources into `evidence.md` | `deep-research` built-in; NotebookLM in browser |
| **Build** — web/UI | `frontend-design` | build polished HTML/UI (your dashboards) | Claude plugin (Anthropic) |
| **Build** — slides/sheets | Codex `presentations` / `spreadsheets` | generate `.pptx` / `.xlsx` | Codex plugins (OpenAI) |
| **Review** | `codex review` (+ `pr-review-toolkit` for a deep pass) | independent + multi-lens review → `review.md` | Codex CLI; Claude plugin |
| **Ship** | `commit-commands` | commit / push / open a PR | Claude plugin (Anthropic) |
| (make a new skill) | `skill-creator` | author or optimize a skill | Claude plugin (Anthropic) |

**This repo authors *no* skills** — even the review uses Codex's **built-in** `codex review`. (Project-specific skills can be added later with `skill-creator`.)

> ⚠️ **These skills live in your AI tools, not in this repo.** On a new machine, install them in Claude Code (`/plugin install <name>@claude-plugins-official`) and Codex — or the flow still runs on plain prompting, just without the polish. founder-kit's *durable* core (`AGENTS.md` + `project.md`) works regardless.

*Spec-driven, in plain files — the "spec-kit" methodology, with no extra tooling to install.*
