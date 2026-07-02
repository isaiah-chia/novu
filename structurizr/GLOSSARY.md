# Domain Glossary

Vocabulary for the `<SYSTEM_NAME>` maps. Every term below should appear in
`01-<system>/workspace.dsl`. Use this to understand what an element *is* before modelling
or editing it. Authoring rules live in [`CONVENTIONS.md`](CONVENTIONS.md); DSL syntax in
[`SYNTAX.md`](SYNTAX.md).

This file is a **glossary, not a doc dump**. Each entry is one row in a table — a term +
one-line meaning. If a term needs prose to explain, the prose lives in an attached
`!docs` page; the glossary just gives the reader enough to recognise what the element is.

Sections below are the suggested shape — add/remove/rename to fit the system. Keep the
table form throughout.

---

## Systems & integrations

The in-focus system + every external system it talks to. One row per system.

| Term | What it is |
| --- | --- |
| **`<SYSTEM_NAME>`** | The in-focus system. `<one-line description: full name, owner, what it does>`. |
| **`<EXTERNAL_SYSTEM_1>`** | `<who owns it · what role it plays · how it talks to <SYSTEM> (e.g. MQ / SFTP / HTTP)>` |
| **`<EXTERNAL_SYSTEM_2>`** | `...` |

## Actors / roles

People who interact with the system. One row per role. Match the names used in the
`person` elements in `01-<system>/workspace.dsl`.

| Term | Role |
| --- | --- |
| **`<ROLE_1>`** | `<one-line description of what they do in the system>` |
| **`<ROLE_2>`** | `...` |

## Domain concepts

The nouns of the business: the entities, states, and journey concepts that show up in
table names, descriptions, and view labels.

| Term | Meaning |
| --- | --- |
| **`<CONCEPT_1>`** | `<one-line definition. If there's a code/table backing it, name it here.>` |
| **`<CONCEPT_2>`** | `...` |

## Codes / enums

Domain codes that appear verbatim in the maps (rejection codes, status flags, letter
codes, lookup-table values…). One row per code or tight code family.

| Code | Meaning |
| --- | --- |
| **`<CODE_1>`** | `<what the code means + which table/column it lives in>` |
| **`<CODE_2>`** | `...` |

## Naming legend (artifact prefixes)

The real-world naming scheme of the source system, kept verbatim in the maps so an
element traces back to source (see [`CONVENTIONS.md`](CONVENTIONS.md) → *Naming*).

| Prefix | Kind |
| --- | --- |
| **`<PREFIX_1>`** | `<kind of artifact — e.g. Oracle table, PL/SQL procedure, batch script>` |
| **`<PREFIX_2>`** | `...` |
