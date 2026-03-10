# Changelog

All notable changes to Claw Compactor will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-03-09

### Added
- **5-layer deterministic token compression pipeline** — rule engine, dictionary encoding, observation compression, RLE patterns, and compressed context protocol
- **Engram (Layer 6)** — real-time LLM-driven Observational Memory with Observer/Reflector architecture
- **Auto-compress hook** (v7.0+) — compress on every file change with zero config
- **Full CJK support** — Chinese/Japanese/Korean token estimation and punctuation normalization
- **Benchmark suite** — ROUGE-L and IR-F1 evaluation against LLMLingua-2 and other baselines
- **OpenClaw skill integration** — native skill with triggers and auto-activation
- **Dictionary encoding** — auto-learned codebook with `$XX` substitution and lossless roundtrip
- **RLE patterns** — path shorthand (`$WS`), IP prefix compression, enum compaction
- **Tiered summaries** — L0 (~200 tokens), L1 (~500 tokens), L2 (full) progressive loading
- **Cross-file deduplication** — shingle-based similarity detection with auto-merge
- **Engram daemon mode** — real-time streaming via stdin JSONL
- **Engram auto-mode** — concurrent multi-thread processing (4 workers)
- **CLI interface** — 11 commands: full, benchmark, compress, dict, observe, tiers, dedup, estimate, audit, optimize, auto
- **848 tests passing** across all compression layers

### Benchmarks
- ROUGE-L **0.653** at rate=0.3 (vs LLMLingua-2 0.346, **+88.2%**)
- ROUGE-L **0.723** at rate=0.5 (vs LLMLingua-2 0.570, **+26.8%**)
- Up to **97% token reduction** on session transcripts
- **50–70% token savings** on first run across unoptimized workspaces

[1.0.0]: https://github.com/aeromomo/claw-compactor/releases/tag/v1.0.0
