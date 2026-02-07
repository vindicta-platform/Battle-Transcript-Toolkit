# Feature Proposal: Battle Transcript Export

**Proposal ID**: FEAT-015
**Author**: Unified Product Architect (Autonomous)
**Created**: 2026-02-01
**Status**: Draft
**Priority**: Medium

---

## Part A: Software Design Document (SDD)

### 1. Executive Summary

Add structured export capabilities for battle transcripts in multiple formats (Markdown, PDF, JSON) to enable content creators, tournament organizers, and players to share and archive their game experiences.

### 2. System Architecture

#### 2.1 Current State
- Battle transcripts stored as structured data
- Raw JSON artifacts only
- No formatted export
- No sharing capabilities

#### 2.2 Proposed Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                 Transcript Export Pipeline                      │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │              Transcript Data                            │    │
│  │   Turns | Phases | Dice Rolls | Scoring                │    │
│  └─────────────────────────────────────────────────────────┘    │
│                              │                                  │
│      ┌───────────────────────┼───────────────────────────┐      │
│      ▼                       ▼                       ▼          │
│ ┌──────────┐          ┌──────────┐          ┌──────────┐        │
│ │ Markdown │          │   PDF    │          │   JSON   │        │
│ │ Exporter │          │ Generator│          │ Exporter │        │
│ └──────────┘          └──────────┘          └──────────┘        │
└─────────────────────────────────────────────────────────────────┘
```

#### 2.3 File Changes

```
Battle-Transcript-Toolkit/
├── src/
│   └── transcript/
│       ├── export/
│       │   ├── __init__.py      [NEW]
│       │   ├── markdown.py      [NEW] Markdown formatter
│       │   ├── pdf.py           [NEW] PDF generator
│       │   └── json_schema.py   [NEW] Structured JSON
│       └── templates/
│           ├── battle_report.md [NEW] Markdown template
│           └── tournament.md    [NEW] Tournament format
├── tests/
│   └── test_export.py           [NEW]
└── docs/
    └── export-formats.md        [NEW]
```

### 3. Export Formats

| Format | Use Case | Features |
|--------|----------|----------|
| Markdown | Blog posts, forums | Images, tables, syntax |
| PDF | Print, archive | Styled, charts, professional |
| JSON | Data analysis | Full structured data |
| HTML | Web embedding | Interactive elements |

### 4. Template System

```markdown
# Battle Report: {{player1.name}} vs {{player2.name}}
**Date**: {{date}}
**Mission**: {{mission.name}}
**Points**: {{points_limit}}

## Armies
### {{player1.faction}} - {{player1.name}}
{{player1.list_summary}}

### {{player2.faction}} - {{player2.name}}
{{player2.list_summary}}

## Game Summary
{{#each turns}}
### Turn {{this.number}}
{{this.narrative}}
{{/each}}

## Final Score
| Player | Primary | Secondary | Total |
|--------|---------|-----------|-------|
| {{player1.name}} | {{player1.primary}} | {{player1.secondary}} | {{player1.total}} |
| {{player2.name}} | {{player2.primary}} | {{player2.secondary}} | {{player2.total}} |
```

---

## Part B: Behavior Driven Development (BDD)

### User Stories

#### US-001: Blog Export
**As a** content creator
**I want to** export battles as Markdown
**So that** I can publish battle reports on my blog

#### US-002: Tournament Archive
**As a** tournament organizer
**I want** PDF exports of all games
**So that** I can archive the event

#### US-003: Data Analysis
**As a** competitive player
**I want** JSON exports
**So that** I can analyze my games statistically

### Acceptance Criteria

```gherkin
Feature: Battle Transcript Export

  Scenario: Export battle to Markdown
    Given I have a completed battle transcript
    When I select "Export as Markdown"
    Then a .md file should be generated
    And include army lists, turn summaries, and final scores
    And be ready for blog posting

  Scenario: Generate tournament PDF
    Given a tournament has 5 completed rounds
    When I select "Export Tournament PDF"
    Then a styled PDF should be generated
    And include all matches grouped by round
    And show standings after each round
```

---

## Implementation Estimate

| Phase | Effort | Dependencies |
|-------|--------|--------------|
| Template System | 4 hours | Jinja2 |
| Markdown Export | 3 hours | None |
| PDF Generation | 6 hours | WeasyPrint |
| JSON Schema | 2 hours | None |
| Testing | 3 hours | Sample data |
| **Total** | **18 hours** | |
