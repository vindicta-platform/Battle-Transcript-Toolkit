# Getting Started

```bash
uv pip install git+https://github.com/vindicta-platform/Battle-Transcript-Toolkit.git
```

```python
from battle_transcript import Analyzer

analyzer = Analyzer()
stats = analyzer.from_file("match.transcript")
print(stats.summary())
```
