# RoadGate — Sovereign LLM Gateway

> Forked from [TensorZero](https://github.com/tensorzero/tensorzero). Rust-powered LLM routing for BlackRoad OS.

**RoadGate** routes inference requests across your fleet with sub-1ms P99 latency at 10K+ QPS. Zero external API dependencies — everything stays on your hardware.

## Features

- **Sub-1ms routing**: Rust-native, zero-allocation hot path
- **Multi-model**: Route to any Ollama model on any fleet node
- **Load balancing**: Round-robin, least-latency, or sticky sessions
- **Rate limiting**: Per-user, per-model, per-node limits
- **Fallback chains**: If Cecilia is down, try Octavia, then Gematria
- **Metrics**: Prometheus-compatible metrics for RoadWatch

## Quick Start

```bash
cargo build --release
./target/release/roadgate --config config.toml
```

## Fleet Routing

```toml
[[nodes]]
name = "cecilia"
url = "http://192.168.4.96:11434"
models = ["llama3.2", "mistral", "gemma2"]
priority = 1

[[nodes]]
name = "octavia"
url = "http://192.168.4.101:11434"
models = ["qwen2.5:1.5b"]
priority = 2

[[nodes]]
name = "gematria"
url = "http://159.65.43.12:11434"
models = ["llama3.2", "mistral"]
priority = 3
```

---

© 2026 BlackRoad OS, Inc. Fork of TensorZero (Apache 2.0). BlackRoad customizations proprietary.
