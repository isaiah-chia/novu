# CLAUDE.md

## What this repo is

The source of truth for **C4 visual maps of `<SYSTEM_NAME>`** — a `<one-sentence
description of the legacy system being mapped>` — authored in **Structurizr DSL**. Each
top-level numbered folder is **one Structurizr workspace = one context/lens** onto the
system. The maps trace back to real source artifacts (e.g. database tables, stored
procedures, batch jobs, UI files), so **accuracy matters more than completeness**.

## Repo layout

Numbered folders hold workspaces. The conventional split is:

- **`01-<system>/`** — the **reference workspace**. The whole in-focus system: people,
  external systems, all modules, every container/component. All other workspaces extend
  this one, so its identifiers, tags, and styles are the shared vocabulary. Match its
  style; when in doubt, copy from here.
- **`0N-<journey>/` (per-journey lenses)** — focused workspaces that
  `workspace extends ../01-<system>/workspace.dsl` and add only **dynamic views** on top
  (no new model elements; those go upstream in `01-<system>/model/`). Each captures one
  user journey or one cross-cutting concern end-to-end.

| Path | What it is |
| --- | --- |
| `01-<system>/workspace.dsl` | The whole `<SYSTEM_NAME>` system (people, externals, all modules). The **reference model** — match its style. |
| `0N-<journey>/workspace.dsl` | Per-journey workspace. `workspace extends ../01-<system>/workspace.dsl` + dynamic views tracing one journey. |
| `SYNTAX.md` | Authoritative Structurizr DSL **language reference**. |
| `CONVENTIONS.md` | House style for authoring the DSL. |
| `GLOSSARY.md` | Domain vocabulary (system names, actor roles, journey concepts, codes…). |
| `README.md` | How to run Structurizr Lite locally (Docker → localhost:8080). |
| `<folder>/docs/` (per workspace) | Markdown long-form notes attached to elements via `!docs`. Used when a component's detail is too long for its inline description (see `CONVENTIONS.md`). |
| `workspace.json` (per folder) | **Tool-generated** by Structurizr Lite; holds manual layout. Do not hand-edit. |
| `.structurizr/` | Gitignored runtime/index data. |

Each `workspace.dsl`'s top-line `workspace "..." "..."` description states that
workspace's scope — read it first to know which lens you're in.

## Authoring `.dsl` files

1. **Syntax** — consult [`SYNTAX.md`](SYNTAX.md) for all DSL constructs. Do not guess
   syntax and do not fetch external docs; `SYNTAX.md` is self-contained and authoritative
   for this repo.
2. **Style** — follow [`CONVENTIONS.md`](CONVENTIONS.md): C4 leveling, hierarchical
   snake_case identifiers, module grouping, tag/style taxonomy, relationship-description
   format.
3. **Domain** — resolve any unfamiliar term via [`GLOSSARY.md`](GLOSSARY.md) before
   modelling it.

## Running & validating

See [`README.md`](README.md). Structurizr Lite reads `workspace.dsl` and serves the
rendered diagrams at `http://localhost:8080`. A docs-only or model edit should render
without errors; if the DSL is invalid, Lite shows a parse error on load. The workspace
this repo serves is controlled by `structurizr.properties`.

## Guardrails

- **Accuracy over completeness** — don't invent code artifacts, tables, or integrations.
  If you didn't read it in source, mark it inferred.
- **Preserve provenance markers** — `[?]` (inferred/unconfirmed) and
  `"NOT FOUND in <SYSTEM> code"` / `"???"` (known gap) encode trust level. Don't silently
  remove them; removing a `[?]` claims you verified the fact against source. See
  [`CONVENTIONS.md`](CONVENTIONS.md) → *Marker discipline*.
- **Keep views in sync** — when you add model elements, make sure they appear in (or are
  intentionally excluded from) the relevant view.
- **One workspace = one context** — don't blend lenses; add a new numbered folder
  instead.
- **Edit `workspace.dsl`, not `workspace.json`.**

## Adding a new workspace

1. Create a new numbered folder (e.g. `0N-<journey>/`) with its own `workspace.dsl`.
2. Set the workspace description to state the lens precisely.
3. Choose diagram types: static C4 (`systemContext` / `container` / `component`) for
   structure, or `dynamic` views for user journeys. Per-journey workspaces are usually
   `workspace extends ../01-<system>/workspace.dsl` + dynamic views only.
4. Reuse the identifier, tag, and style conventions from `01-<system>` so the maps stay
   visually consistent.
