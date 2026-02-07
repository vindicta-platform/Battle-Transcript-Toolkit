# Battle-Transcript-Toolkit Roadmap

> **Vision**: Transform raw transcripts into polished WARScribe battle reports
> **Status**: Active Development
> **Last Updated**: 2026-02-03

---

## v1.0 Target: April 2026

### Mission Statement
Deliver a production-ready toolkit that converts natural language game transcripts into structured WARScribe battle reports, with event extraction, unit resolution, and replay capability.

---

## Milestone Timeline

```
┌─────────────────────────────────────────────────────────────────┐
│  Feb 2026          Mar 2026          Apr 2026                   │
│  ─────────────────────────────────────────────────────────────  │
│  [v0.1.0]          [v0.2.0]          [v0.3.0]      [v1.0.0]     │
│  Data Model        NLP Extraction    Replay        Production   │
│                                                                  │
│  Week 2-3          Week 4-5          Week 6-7      Week 8       │
└─────────────────────────────────────────────────────────────────┘
```

---

## v0.1.0 — Data Model (Target: Feb 17, 2026)

### Deliverables
- [ ] Transcript data model (Pydantic)
- [ ] GameEvent schema
- [ ] BattleReport schema
- [ ] Manual event entry API
- [ ] JSON serialization
- [ ] Integration with WARScribe-Core

### Key Measurable Results
| Metric | Target | Measurement |
|--------|--------|-------------|
| **Schema Coverage** | All action types | Unit tests |
| **Serialization** | Round-trip fidelity | Parse tests |
| **API Usability** | Manual entry works | Integration test |

### Exit Criteria
- [ ] Create battle report programmatically
- [ ] Serialize/deserialize to JSON
- [ ] Compatible with WARScribe-Core format

---

## v0.2.0 — NLP Event Extraction (Target: Mar 3, 2026)

### Deliverables
- [ ] Pattern-based event extraction
- [ ] LLM-powered extraction (Gemini)
- [ ] Unit name resolution
- [ ] Ambiguity flagging
- [ ] Human review queue
- [ ] Agent-Auditor-SDK integration

### Key Measurable Results
| Metric | Target | Measurement |
|--------|--------|-------------|
| **Event Extraction** | 80%+ actions identified | Test transcripts |
| **Unit Resolution** | 90%+ correct matches | Manual audit |
| **Ambiguity Rate** | <20% flagged for review | Queue metrics |

### Exit Criteria
- [ ] Extract events from natural language
- [ ] Resolve "my marines" → specific unit
- [ ] Flag unclear references for human review

---

## v0.3.0 — Replay & Context (Target: Mar 17, 2026)

### Deliverables
- [ ] Replay data model
- [ ] Phase/turn grouping
- [ ] Game state reconstruction
- [ ] Context-aware inference
- [ ] Stats extraction (casualties, VP)

### Key Measurable Results
| Metric | Target | Measurement |
|--------|--------|-------------|
| **Turn Grouping** | 95%+ correct | Test transcripts |
| **State Tracking** | Unit positions tracked | Integration test |
| **Stats Accuracy** | 90%+ correct totals | Comparison test |

### Exit Criteria
- [ ] Replay data model complete
- [ ] Events grouped by turn/phase
- [ ] Game stats extracted

---

## v1.0.0 — Production Release (Target: Apr 21, 2026)

### Deliverables
- [ ] Replay Player UI component
- [ ] Discord bot integration (basic)
- [ ] Batch processing
- [ ] PyPI publication
- [ ] Performance optimization

### Key Measurable Results
| Metric | Target | Measurement |
|--------|--------|-------------|
| **Test Coverage** | >85% | pytest-cov |
| **Processing Speed** | <5 min per transcript | Benchmark |
| **Replay Quality** | Playback matches source | Manual review |
| **PyPI Downloads** | 50+/month | PyPI stats |

### Exit Criteria
- [ ] No critical bugs for 2 weeks
- [ ] Replay Player renders in Logi-Slate
- [ ] Published to PyPI

---

## Event Extraction Pipeline

```
┌─────────────────────────────────────────────────────────────────┐
│  1. Raw Transcript Input                                         │
│     "I'm moving my Captain to the objective..."                  │
├─────────────────────────────────────────────────────────────────┤
│  2. Pattern Matching                                             │
│     MOVE detected: subject="Captain", target="objective"        │
├─────────────────────────────────────────────────────────────────┤
│  3. Unit Resolution                                              │
│     "Captain" → CPT-01 (from army roster)                       │
├─────────────────────────────────────────────────────────────────┤
│  4. Ambiguity Check                                              │
│     Clear? → Proceed | Unclear? → Queue for review              │
├─────────────────────────────────────────────────────────────────┤
│  5. WARScribe Output                                             │
│     [MOVE: CPT-01 -> Zone-A]                                    │
└─────────────────────────────────────────────────────────────────┘
```

---

## Dependencies

| Dependency | Status | Notes |
|------------|--------|-------|
| WARScribe-Core | 🔄 Parallel | Output format |
| WARScribe-Parser | 🔄 Parallel | Input source |
| Agent-Auditor-SDK | 🔄 Parallel | LLM quota |
| Gemini API | ✅ Available | NLP extraction |
| Logi-Slate-UI | 🔄 Parallel | Replay display |

---

## Risks

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| Extraction accuracy | High | Medium | Human review queue |
| Unit name ambiguity | High | Medium | Roster context required |
| LLM costs | Medium | Medium | Pattern matching first |
| Phase detection errors | Medium | Low | Heuristic fallbacks |

---

## Success Criteria for v1

1. **Accuracy**: 80%+ event extraction from natural language
2. **Integration**: Seamless flow from Parser to Toolkit to Core
3. **Replay**: Battle reports playable in Logi-Slate
4. **Adoption**: 50+ transcripts processed per month

---

*Maintained by: Vindicta Platform Team*
</Parameter>
<parameter name="Complexity">4
