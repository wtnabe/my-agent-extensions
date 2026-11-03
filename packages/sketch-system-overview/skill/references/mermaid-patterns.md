# Mermaid patterns

Use these patterns when the user asks for Mermaid. They follow the same rules as the PlantUML patterns; only the notation changes. Replace placeholders with source-derived names and remove unsupported elements and loops.

Start every diagram with this config so that lines stay curved, boxes have no shadows, and labels are not wrapped narrowly. L2 uses `layout: elk` instead, as in its example:

```yaml
---
config:
  theme: neutral
  layout: dagre  # elk: lines never pass behind boxes, but are right-angled
  look: classic
  flowchart:
    wrappingWidth: 420
---
```

| PlantUML | Mermaid |
| --- | --- |
| frame `rectangle` | `systemBoundary` in the people map, `subgraph` elsewhere |
| boundary object `rectangle` | `Id["..."]` |
| `actor` | `actor` (people map only) |
| `component` | a rectangle outside the boundary (people map only) |
| `process` | `Id("...")` |
| `artifact` | `Id@{ shape: doc, label: "..." }` |
| `skinparam` palette section | `classDef` and `style` lines between `%% BEGIN COLOR PALETTE` and `%% END COLOR PALETTE` |

## L1

Draw two diagrams with the same frame and the same objects. Give each object a stable name.

### People map

Use a use case diagram. Its labels accept no HTML: write the name in bold and the synopsis on the next physical line inside a Markdown string.

```mermaid
---
config:
  theme: neutral
  layout: dagre  # elk: lines never pass behind boxes, but are right-angled
  look: classic
  flowchart:
    wrappingWidth: 420
---
usecase-beta
  direction LR
  actor RoleA("Role A")
  actor RoleB("Role B")

  systemBoundary "Business workspace"
    Request["`**Request**
Scope / timing / priority`"]
    Assignment["`**Assignment**
Owner / timing / exceptions`"]
    Observation["`**Observed reality**
Completion / blockers / remaining work`"]
  end

  RoleA -- Request
  RoleB -- Assignment
  RoleB -- Observation
```

### Flow map

```mermaid
---
config:
  theme: neutral
  layout: dagre  # elk: lines never pass behind boxes, but are right-angled
  look: classic
  flowchart:
    wrappingWidth: 420
---
flowchart LR
  subgraph Workspace["Business workspace"]
    direction LR
    Request["Request"]
    Assignment["Assignment"]
    Observation["Observed reality"]

    Request --> Assignment
    Assignment --> Observation
    Observation -.-> Request
  end
```

## L2

Mermaid comments are line comments only, so the palette section is disabled by commenting out each line between its markers.

```mermaid
---
config:
  theme: neutral
  layout: elk  # dagre: curved lines, but the focus frame touches the outer frame name
  look: classic
  flowchart:
    wrappingWidth: 420
---
flowchart LR
  subgraph Workspace["Business workspace"]
    direction LR
    Request["Request"]:::context
    Policy["Source-known policy"]:::knownInput

    subgraph Assignment["Assignment"]
      Choose("Choose the response")
      Result@{ shape: doc, label: "Assigned work<hr>Owner and scope<br>Committed timing<br>Exceptions and next action" }
      Choose --> Result
    end

    Observation["Observed reality"]:::context

    Request --> Choose
    Policy --> Choose
    Result --> Observation
    Observation -.-> Choose
    Observation -.-> Request
  end

  classDef knownInput stroke-dasharray:5 5
  style Assignment stroke-width:3px

  %% BEGIN COLOR PALETTE
  classDef context fill:#F3F4F6,stroke:#9CA3AF
  classDef knownInput fill:#FFF4E5,stroke:#D97706,stroke-dasharray:5 5
  style Assignment fill:#E8F0FE,stroke:#2563EB,stroke-width:3px
  %% END COLOR PALETTE
```

## Constraints

- Default to `layout: dagre` for L1 and `layout: elk` for L2, and keep the comment on that line, so readers can switch the layout themselves.
- In every flowchart, write `direction LR` inside the frame `subgraph`. Without it, the frame's contents are drawn top to bottom.
- Use dashed arrows `-.->` for feedback and `--` for involvement in the people map.
- Keep the thick focus border and dashed input border outside the palette section, and repeat them inside it, so they remain when the palette is commented out.
