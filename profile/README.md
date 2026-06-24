# VERIDACTUS

<p align="center">
  <img src="https://raw.githubusercontent.com/veridactus/.github/main/assets/logo-light.svg" alt="VERIDACTUS" width="400" />
</p>

<p align="center">
  <strong>Open Governance for LLM Inference — deterministic constraints, cryptographic audit, zero‑trust.</strong>
</p>

<p align="center">
  <a href="https://docs.veridactus.ai">Documentation</a> |
  <a href="https://docs.veridactus.ai/specification/latest">Specification</a> |
  <a href="https://github.com/veridactus/docs/discussions">Discussions</a>
</p>

---

**VERIDACTUS** is a deterministic control plane that layers atop existing OpenAI‑compatible APIs, transforming every LLM invocation into an **independently‑auditable, cryptographically‑verifiable engineering event**. No server. No secret. No trust required.

## Getting Started

- 📖 Read the [Documentation](https://docs.veridactus.ai) for guides and tutorials
- 🔍 Review the [Protocol Specification v0.2.1](https://docs.veridactus.ai/specification/latest) for technical details
- 🐳 Run the reference proxy:
  ```bash
  docker run -p 8080:8080 ghcr.io/veridactus/veridactus:latest
  ```
- 🔐 Verify an audit trace offline with the [audit proof guide](https://docs.veridactus.ai/specification/latest)

## Key Features

- 🔐 **Cryptographic Proof Chain (L0 → L2B)** — SHA‑256 hash chain → Merkle tree sampling → Zero‑Knowledge proofs
- 💰 **Streaming Budget Control** — Real‑time SSE budget enforcement with micro‑dollar precision
- 🛡️ **Privacy Grading** — `raw` / `masked` / `hash_only` → TEE‑Private with GDPR right‑to‑erasure
- 🔍 **Active Prevention** — Token‑level constrained decoding against PII, credentials, prompt injection
- 🔗 **Delegation Chain** — Composite attestation (Ed25519 + TEE + ZK) for multi‑agent trust
- 📋 **Compliance Ready** — Auto‑generated EU AI Act / NIST AI 600‑1 reports per inference
- 🌍 **OWASP ASI Top 10** — Full alignment with OWASP Agentic AI Security risks

## Project Structure

- [**veridactus**](https://github.com/veridactus/veridactus) — Core implementation: Rust data plane, Go control plane, React UI
- [**docs**](https://github.com/veridactus/docs) — Protocol specification v0.2.1, JSON schemas, OpenAPI, conformance suite, RFCs
- [**audit-cli**](https://github.com/veridactus/audit-cli) — Offline cryptographic audit verification tool *(upcoming)*
- [**sdk-python**](https://github.com/veridactus/sdk-python) — Python SDK with native VERIDACTUS header support *(upcoming)*
- [**validator-js**](https://github.com/veridactus/validator-js) — JavaScript protocol validator *(upcoming)*

### Docker Images

| Image | Component | Stack |
|:------|:----------|:------|
| `veridactus/veridactus-core` | Data Plane — AI proxy gateway | Rust · Axum · SSE |
| `veridactus/veridactus-cp` | Control Plane — config & auth | Go · SQLite · REST |
| `veridactus/veridactus-ui` | Frontend — admin dashboard | React · ReactFlow |
| `veridactus/veridactus-python-worker` | Worker — PII detection | Python |

## Community & Governance

VERIDACTUS follows an **Open Meritocracy** model steered by a Technical Steering Committee (TSC). All RFCs and design decisions happen transparently on GitHub.

- 💬 [Discussions](https://github.com/veridactus/docs/discussions) — Questions, ideas, community
- 📜 [RFC Process](https://github.com/veridactus/docs/blob/main/rfcs/README.md) — Protocol change proposals
- 🛡️ [Security Reporting](mailto:security@veridactus.ai) — Responsible disclosure
- 🐦 [@veridactus](https://twitter.com/veridactus) — Announcements & updates

## Contributing

We welcome contributions of all kinds — specification improvements, core development, conformance tests, and documentation. See [CONTRIBUTING.md](https://github.com/veridactus/docs/blob/main/CONTRIBUTING.md) to get started.

---

<p align="center">
  <sub>
    Licensed under <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE">Apache 2.0</a>
    · Copyright 2026 The VERIDACTUS Authors
  </sub>
</p>
