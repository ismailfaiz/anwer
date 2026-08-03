# Anwer

**Anwer** (أنور, "more luminous") is an open-source **semantic profiler**
for LLM inference systems.

"Semantic" here refers to inference-execution semantics — scheduler
decisions, KV cache behavior, expert routing, prefill/decode phase
boundaries — not text or content semantics. Anwer's core idea is to join
that semantic control-plane with the hardware data-plane (kernel timelines,
CUPTI / torch.profiler traces) on a shared timeline, so a latency spike can
be attributed to *what the engine was doing* (e.g. "MoE expert dispatch
for request X"), not just *which kernel ran*.

Modern inference stacks — vLLM, SGLang, TensorRT-LLM, NVIDIA Dynamo, and
others — each expose their own metrics, logs, and tracing conventions, if
they expose deep visibility at all, and existing tools sit at one end or
the other: hardware profilers (Nsight, Proton) see kernels with no
execution context, and request-level observability tools (Langfuse) see
requests with no hardware detail. Anwer aims to sit in between, providing
a single, engine-agnostic layer for understanding *where time and memory
actually go* during inference, and *why*.

## Status

Early / pre-alpha. This repository currently contains project scaffolding
only. Design docs, architecture notes, and the first working profiler
hooks will land in subsequent commits.

## Goals

- Engine-agnostic instrumentation (starting with vLLM and SGLang)
- Joining semantic control-plane events (scheduling, KV cache ops, expert
  dispatch, prefill/decode phase) with hardware data-plane traces (kernel
  timelines) on a shared timeline
- Roofline-grounded interpretation of bottlenecks — attributions tied to
  a computable hardware number, not a heuristic guess
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
