---
name: Sketch a System Overview
description: "Turn business descriptions, operating models, workflows, or planning documents into conceptual diagrams of a system: who is involved, how shared information flows, and a zoom on each piece of information. Draws PlantUML by default, or Mermaid on request. Use when asked for a concept diagram or system overview. Not for software architecture."
---

# Sketch a System Overview

Create a readable map of shared domain objects and coordination, not a software architecture. Read `references/plantuml-patterns.md` for notation. When the user asks for Mermaid, read `references/mermaid-patterns.md` instead.

## Deliverable

Deliver one Markdown document with a descriptive title, links to the source documents, an L1 whole view in two diagrams, and one L2 per L1 boundary object unless the user requests a subset. Use the user's language.

- Keep diagrams central. Add a compact key or short local note only to prevent a specific misreading.
- Concision means removing repeated explanation, not removing the information that makes an object understandable. Useful diagram labels are not redundant source-document background.
- Do not include evidence ledgers, candidate comparisons, work logs, validation logs, temporary paths, or task-management records. No task tracker is required.
- Use subject-based headings, not descriptions of drawing operations. Do not show the terms L1 or L2 in headings or reader-facing text. Do not invent version numbers from nearby files or previous diagramming sessions; follow explicit user requests or governing project instructions.
- Disclose material diagram-specific assumptions locally. Do not repeat the source's background, full requirements, or open-question list.

## 1. Understand the coordination problem

Identify the decision or coordination the map must clarify, the participating people and source-established systems, their shared information, relevant time horizons, and explicit exclusions.

Distinguish what the source states, what you infer, and what remains unknown. Resolve duplicate terminology and contradictions before drawing. Do not turn an assumption into an established fact, invent human approval for automated work, or invent automation for human work.

## 2. Select boundary objects

A boundary object crosses a responsibility boundary and is used to coordinate a distinct job or decision. Prefer shared, handed-off, reviewed, or updated domain nouns with identifiable producers and consumers. Do not substitute software functions, screens, APIs, database tables, or every source field for these objects.

Choose the smallest set that preserves materially different ownership, meaning, lifecycle, and use:

- Keep intention, chosen response, observed reality, and learned standards distinct where the source gives them different jobs.
- Distinguish a decision from an execution-facing board or commitment when they serve different users or jobs.
- A different horizon or granularity alone does not justify a separate L1 object. Keep a registered intention at L1 and its calculated load or projection inside the receiving L2 unless both are independently shared and acted on.

Do not merge objects just to shorten the diagram, or promote every information facet into a new object.

Compare plausible alternatives during analysis. Ask one targeted question only when the unresolved choice materially changes responsibility or meaning. Otherwise choose the best-supported structure without publishing a decomposition workshop.

When revising an existing map's presentation, preserve its established objects, names, and relationships unless the user requests structural changes or source evidence requires a correction. A labeling or styling change is not a reason to select a new domain model.

## 3. Draw L1: names, meaning, and relationships

Keep boundary objects and their forward/feedback relationships as the main reading path. Make the initiating demand and the outcome easy to find. Enclose the boundary objects in one rectangle named for what they coordinate, in every diagram.

Draw L1 as two diagrams with the same frame and objects:

- People map: actors, systems, and objects with synopses. Use only undirected involvement lines; no arrows between objects. Keep actors and systems outside the frame.
- Flow map: objects by name only, without actors or systems. Follow the overall flow the source describes.

Use:

- `rectangle` for a boundary object;
- `actor` for a person, human role, or organization;
- `component` for a functional system or equipment only when the source names it and divides responsibility among such parts. Do not draw a single system that supports the whole; state its role in a short note if needed.

**Give each L1 object a stable name and a minimal orienting synopsis beneath it.** Use a line break or divider to distinguish identity from the synopsis. The synopsis helps readers recognize what the object is for and distinguish it from neighboring objects; it is not an inventory of its contents or a description of the producing process.

Apply a deletion test: if removing a term still leaves the object's role and distinguishing meaning clear, leave that detail to L2. Do not target a fixed number of concepts. L2 may introduce useful detail that L1 does not preview; do not expand L1 merely to advertise everything shown in L2. Field names can be good orienting cues when they identify the object's role, so do not mechanically classify all fields as L2 detail.

The synopsis is part of understanding L1; it is not a separate object or a required label to repeat everywhere. For example, a plan may summarize timing and scope, while its observed state summarizes completion and blockers.

Use unlabelled relationships:

- solid arrows for forward coordination relationships;
- dashed arrows for observation or learning feedback;
- undirected lines for actor or system involvement in creating, using, or acting on an object.

These are conceptual relationships, not claims that information executes itself. Show a directed system request/action only when that relationship itself matters. Do not insert an executor between every object pair, replace shared objects with components, or turn L1 into an inventory of systems.

Draw only the feedback the source states: what changes current work and, separately, what accumulated evidence changes for future work. Keep planned work and observed reality distinct.

## 4. Draw L2: compact context, visible information detail

Focus exactly one L1 boundary object in each L2. Keep its stable name and rectangle boundary. The L1 synopsis is not part of the object's identifier and need not be repeated verbatim in the focus heading.

Inside the focus show:

- one or a few `process` elements describing how the shared information is produced or updated;
- an `artifact` showing the resulting information or agreement.

Outside the focus:

- show direct source-known inputs as rectangles;
- keep other L1 objects as context, using their stable names only by default;
- retain a short qualifier only when needed to understand this focus or avoid ambiguity;

Do not copy every L1 synopsis into every L2. Shortened context labels still refer to the same objects; simplifying labels must not change their meaning or remove necessary relationships.

Choose context by the object's place in the coordination loop. A true starting object may need only inputs and its direct downstream object. For a focus within a loop, keep the object-level cycle skeleton by default: displayed feedback needs a visible forward origin and return destination. Crop only where these remain understandable. This does not require repeating every participant or every synopsis.

## 5. Apply notation and review

Distinguish the focus, its context, and source-known inputs omitted from L1 as the notation reference shows. Use the reference palette by default; omit or disable it when the user requests neutral rendering.

Review the set for source fidelity, stable names, clear L1 synopses, compact context labels, consistent relationship directions, feedback provenance, and one obvious focus per L2. Check that decisions and execution views remain distinct and no unsupported human or automated responsibility has appeared.

When a renderer for the chosen notation is readily available, check syntax and the intended delivery view for unreadable labels, crossings, weak focus, or excessive width. No particular script or image-opening tool is required. Do not claim checks you did not perform; if rendering could not be checked, mention it briefly in the delivery message.
