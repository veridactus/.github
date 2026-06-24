# VERIDACTUS

<p align="center">
  <img src="https://raw.githubusercontent.com/veridactus/.github/main/assets/logo-light.svg" alt="VERIDACTUS Logo" width="480" />
</p>

<p align="center">
  <strong>Open Governance for LLM Inference — deterministic constraints, cryptographic audit, zero‑trust.</strong>
</p>

<p align="center">
  <a href="https://docs.veridactus.ai">Documentation</a> |
  <a href="https://docs.veridactus.ai/specification/latest">Specification</a> |
  <a href="https://github.com/veridactus/docs/discussions">Discussions</a>
</p>

VERIDACTUS is a deterministic control plane for LLM inference. It transforms every LLM invocation into an independently‑auditable, cryptographically‑verifiable engineering event through declarative constraints, state‑machine tracing, and cryptographic audit — all delivered as standard HTTP headers on top of any OpenAI‑compatible API.

## Getting Started

- 📚 Read the [Documentation](https://docs.veridactus.ai) for guides and tutorials
- 🔍 Review the [Protocol Specification v0.2.1](https://docs.veridactus.ai/specification/latest) for technical details
- 🐳 Run `docker run -p 8080:8080 ghcr.io/veridactus/veridactus:latest` to start governing LLM calls
- 🛡️ See the [Security Policy](https://github.com/veridactus/docs/blob/main/SECURITY.md) for responsible disclosure

## Project Structure

- [**veridactus**](https://github.com/veridactus/veridactus) — Core implementation: Rust data plane, Go control plane, React UI, and protocol documentation
- [**docs**](https://github.com/veridactus/docs) — Protocol specification v0.2.1, JSON schemas, OpenAPI, conformance suite, and RFC process

## Contributing

We welcome contributions of all kinds — specification improvements, core development, conformance tests, and documentation. See the [contributing guide](https://github.com/veridactus/docs/blob/main/CONTRIBUTING.md) to get started.

Have questions or ideas? Join the discussion in our [community forum](https://github.com/veridactus/docs/discussions).

## About

VERIDACTUS is an open source project governed by an [Open Meritocracy](https://github.com/veridactus/docs/blob/main/GOVERNANCE.md) model steered by a Technical Steering Committee. Licensed under [Apache 2.0](https://github.com/veridactus/veridactus/blob/main/LICENSE). Copyright 2026 The VERIDACTUS Authors.
