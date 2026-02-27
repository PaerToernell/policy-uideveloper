# policy-uideveloper — UI-Developer Architecture

> See [policy-meta](../policy-meta/CLAUDE.md) for cross-project conventions.
> See [GLOSSARY](GLOSSARY.md) for project-specific terminology.

## Identity

Architecture and design decisions for UI-Developer — the cross-project UI form registry.

## Architecture

UI-Developer stores form-level design conversations and decisions in a persistent database. It integrates into any repo with a UI layer.

### Layers

| Layer | Responsibility | May depend on |
|-------|---------------|---------------|
| **Presentation** | CLI or UI for browsing/editing form records | Service |
| **Service** | Form registry logic, search, linking to repos | Data Access |
| **Data Access** | Persistence of form records and conversations | — |
| **Integration** | Hooks into other repos' UI layers | Service |

### Dependencies

- **basekit** — shared base classes (database, config, UI) from `../../basekit/`

### Key Design Decisions

- Cross-project by nature — must not depend on any single project's code
- Form records are the core entity: one record per form, per project
- Each record captures purpose, design rationale, and conversation history
