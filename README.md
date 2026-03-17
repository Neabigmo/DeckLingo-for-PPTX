# DeckLingo for PPTX

Translate editable PowerPoint decks into your chosen language while keeping layout, terminology, and editability as stable as possible.

## Why This Exists

Most PPT translation workflows flatten slides, damage layout, or ignore speaker notes and inherited template text. DeckLingo for PPTX works directly on editable PPTX text and is designed for agent workflows, skill marketplaces, and local automation.

## Highlights

- Editable PPTX translation instead of image-based replacement
- Source language and target language are both configurable
- Interaction/output language is configurable separately
- English to Chinese and Chinese to English are both first-class workflows
- Optional translation of notes, layouts, and slide masters
- Glossary support for stable terminology
- Skip-pattern support for URLs, file names, identifiers, and protected text
- Preflight scan script and post-translation verification
- Works as a self-contained skill package for Codex-style and OpenClaw-style runtimes

## Quick Start

Install dependencies:

```bash
pip install -r requirements.txt
```

Scan a deck before translating:

```bash
python scripts/scan_pptx_text.py \
  --input "example.pptx" \
  --source-lang en \
  --include-notes
```

Translate English to Simplified Chinese:

```bash
python scripts/translate_pptx_text.py \
  --input "example.pptx" \
  --output "example.zh-CN.pptx" \
  --source-lang en \
  --target-lang zh-CN \
  --ui-lang zh \
  --include-notes \
  --report-file "translation-report.json"
```

Translate Chinese to English with a glossary:

```bash
python scripts/translate_pptx_text.py \
  --input "example.pptx" \
  --output "example.en.pptx" \
  --source-lang zh \
  --target-lang en \
  --ui-lang en \
  --include-notes \
  --glossary-file "assets/glossary.sample.json"
```

## Runtime Compatibility

- Codex-style skill runtimes
- OpenClaw-style local agent platforms
- Any local agent system that can read `SKILL.md` and execute Python scripts

Platform notes are in [references/platform-compatibility.md](./references/platform-compatibility.md).

## Project Structure

- [SKILL.md](./SKILL.md): primary skill instructions
- [agents/openai.yaml](./agents/openai.yaml): marketplace-style metadata
- [scripts/scan_pptx_text.py](./scripts/scan_pptx_text.py): preflight scan
- [scripts/translate_pptx_text.py](./scripts/translate_pptx_text.py): translation entrypoint
- [assets/glossary.sample.json](./assets/glossary.sample.json): sample glossary
- [assets/skip_patterns.sample.txt](./assets/skip_patterns.sample.txt): sample protected-text rules

## Validation

Validated locally on:

- `4.  Microbial metabolism 2026.pptx`
- Workflow: `English -> zh-CN`
- Result: scan succeeded, translation succeeded, output deck written, verification passed

## Marketplace Copy

Multi-language listing copy is available in [references/market-listing.md](./references/market-listing.md).

## Author

Yang Yiheng  
yangyiheng00711@gmail.com
