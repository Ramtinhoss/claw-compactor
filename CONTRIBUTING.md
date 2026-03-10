# Contributing to Claw Compactor

Thank you for your interest in contributing to Claw Compactor! This guide will help you get started.

## Table of Contents

- [Development Setup](#development-setup)
- [Running Tests](#running-tests)
- [Code Style](#code-style)
- [Compression Layers Overview](#compression-layers-overview)
- [Pull Request Process](#pull-request-process)
- [Reporting Bugs](#reporting-bugs)

## Development Setup

```bash
# Clone the repository
git clone https://github.com/aeromomo/claw-compactor.git
cd claw-compactor

# Install in development mode with all extras
pip install -e ".[dev,accurate]"

# Verify installation
pytest tests/ -v --tb=short
```

**Requirements:**
- Python 3.9+
- `pytest >= 7.0` (included in `[dev]` extras)
- `tiktoken >= 0.5.0` (optional, included in `[accurate]` extras)

## Running Tests

```bash
# Run all tests
pytest tests/ -v

# Run a specific test file
pytest tests/test_pipeline.py -v

# Run with coverage (if installed)
pytest tests/ --cov=scripts --cov-report=term-missing

# Run only fast tests (skip integration)
pytest tests/ -v -k "not integration and not real_workspace"
```

All 848 tests should pass. If any fail, please open an issue.

## Code Style

- **Python 3.9+** compatible — no walrus operators in critical paths
- Use type hints where practical
- Docstrings for public functions (Google style)
- Keep functions focused — single responsibility
- Prefer explicit over clever

## Compression Layers Overview

Understanding the architecture helps you contribute effectively:

| Layer | Module | Type | Purpose |
|-------|--------|------|---------|
| L1 | `scripts/compress_memory.py` | Deterministic | Dedup lines, strip markdown filler, merge sections |
| L2 | `scripts/dictionary_compress.py` | Deterministic | Auto-learned codebook, `$XX` token substitution |
| L3 | `scripts/observation_compressor.py` | Deterministic | Session JSONL to structured summaries |
| L4 | `scripts/lib/rle.py` | Deterministic | Path shorthand, IP prefix, enum compaction |
| L5 | `scripts/compressed_context.py` | Deterministic | Format abbreviation (ultra/medium/light) |
| L6 | `scripts/lib/engram.py` | LLM-powered | Real-time Observational Memory (Engram) |

**Key libraries** in `scripts/lib/`:
- `tokens.py` — Token counting (tiktoken or CJK-aware fallback)
- `markdown.py` — Section parsing and manipulation
- `dedup.py` — Shingle-based similarity detection
- `dictionary.py` — Codebook compression/decompression
- `config.py` — Configuration loading

## Pull Request Process

1. **Fork** the repository and create a feature branch
2. **Write tests** for any new functionality
3. **Run the full test suite** — all tests must pass
4. **Update documentation** if your change affects user-facing behavior
5. **Open a PR** using the PR template
6. **Respond to review feedback** promptly

### PR Guidelines

- Keep PRs focused — one feature or fix per PR
- Include before/after token savings if modifying compression logic
- Add benchmark data if claiming performance improvements
- Reference related issues with `Fixes #123` or `Closes #123`

## Reporting Bugs

Use the [bug report template](https://github.com/aeromomo/claw-compactor/issues/new?template=bug_report.md) and include:

- Python version and OS
- Whether tiktoken is installed
- Minimal reproduction steps
- Expected vs actual behavior

## Questions?

- Join the [OpenClaw Discord](https://discord.com/invite/clawd)
- Check the [documentation](https://docs.openclaw.ai)
- Open a [discussion](https://github.com/aeromomo/claw-compactor/discussions)
