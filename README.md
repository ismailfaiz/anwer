# Anwer

**Anwer** (أنور, "more luminous") is an open-source profiler and observability
toolkit for LLM inference systems.

Modern inference stacks — vLLM, SGLang, TensorRT-LLM, NVIDIA Dynamo, and
others — each expose their own metrics, logs, and tracing conventions, if
they expose deep visibility at all. Anwer aims to provide a single,
engine-agnostic layer for understanding *where time and memory actually go*
during inference: scheduling, batching, KV cache behavior, decode/prefill
split, and hardware utilization, across engines and hardware backends.

## Status

Early / pre-alpha. This repository currently contains project scaffolding
only. Design docs, architecture notes, and the first working profiler
hooks will land in subsequent commits.

## Goals

- Engine-agnostic instrumentation (starting with vLLM and SGLang)
- Low-overhead tracing suitable for production inference, not just benchmarks
- A common schema for inference-level metrics (prefill/decode timing, KV
  cache occupancy, batching efficiency, queueing delay)
- Tooling to visualize and diff profiler runs across engines/configs

## Why "Anwer"

Anwer is a family name meaning "more luminous" in Arabic. The idea is
straightforward: make what happens inside an inference server visible.

## Contributing

Not yet open for external contributions while the core design settles.
Watch this space.

## License

Apache 2.0 — see [LICENSE](LICENSE).
