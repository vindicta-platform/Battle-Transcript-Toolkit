# Battle-Transcript-Toolkit

A toolkit for parsing, analyzing, and managing WARScribe battle transcripts.

## Overview

Battle-Transcript-Toolkit provides utilities for working with competitive Warhammer 40k match transcripts in WARScribe format.

## Features

- **Transcript Parsing**: Load and validate WARScribe transcripts
- **Game State Reconstruction**: Rebuild turn-by-turn game state
- **Statistical Analysis**: Extract metrics from match history
- **Export Formats**: Convert to JSON, CSV, or training data

## Installation

Install from source using uv:

```bash
uv pip install git+https://github.com/vindicta-platform/Battle-Transcript-Toolkit.git
```

Or clone and install locally:

```bash
git clone https://github.com/vindicta-platform/Battle-Transcript-Toolkit.git
cd Battle-Transcript-Toolkit
uv pip install -e .
```

## Quick Start

```python
from battle_transcript import Transcript

tx = Transcript.load("match_001.warscribe")
print(f"Winner: {tx.winner}")
print(f"Turns: {len(tx.turns)}")

for turn in tx.turns:
    print(f"  {turn.phase}: {turn.summary}")
```

## Use Cases

- **Training Data**: Generate datasets for AI model training
- **Meta Analysis**: Aggregate statistics across tournaments
- **Replay Validation**: Verify transcript integrity

## Related Repositories

| Repository | Relationship |
|------------|-------------|
| [WARScribe-Parser](https://github.com/vindicta-platform/WARScribe-Parser) | Core parsing logic |
| [Arbiter-Predictor](https://github.com/vindicta-platform/Arbiter-Predictor) | Win prediction |

## Platform Documentation

> **📌 Important:** All cross-cutting decisions, feature proposals, and platform-wide architecture documentation live in [**Platform-Docs**](https://github.com/vindicta-platform/Platform-Docs).
>
> Any decision affecting multiple repos **must** be recorded there before implementation.

- 📋 [Feature Proposals](https://github.com/vindicta-platform/Platform-Docs/tree/main/docs/proposals)
- 🏗️ [Architecture Decisions](https://github.com/vindicta-platform/Platform-Docs/tree/main/docs)
- 📖 [Contributing Guide](https://github.com/vindicta-platform/Platform-Docs/blob/main/CONTRIBUTING.md)

## License

MIT License - See [LICENSE](./LICENSE) for details.
