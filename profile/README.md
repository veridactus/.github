<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/veridactus/.github/main/assets/logo-dark.svg">
    <img alt="VERIDACTUS" src="https://raw.githubusercontent.com/veridactus/.github/main/assets/logo-light.svg" width="560">
  </picture>
</p>

<p align="center">
  <strong>Open Governance for LLM Inference</strong><br>
  <sub>Deterministic constraints · Cryptographic audit · Streaming budget control · Zero‑trust</sub>
</p>

<p align="center">
  <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache%202.0-blue?style=flat-square" alt="License"></a>
  <a href="https://github.com/veridactus/docs"><img src="https://img.shields.io/badge/spec-v0.2.1-38BDF8?style=flat-square" alt="Specification"></a>
  <a href="https://docs.veridactus.ai"><img src="https://img.shields.io/badge/docs-docs.veridactus.ai-0ea5e9?style=flat-square" alt="Documentation"></a>
  <a href="https://github.com/veridactus/veridactus"><img src="https://img.shields.io/badge/Rust-1.75+-orange?style=flat-square&logo=rust" alt="Rust"></a>
  <a href="https://github.com/veridactus/veridactus"><img src="https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat-square&logo=go" alt="Go"></a>
</p>

---

**VERIDACTUS** is the constitutional blueprint for trustworthy AI governance — a deterministic control plane that layers atop existing OpenAI‑compatible APIs. Through declarative constraints, state‑machine tracing, and cryptographic audit, it transforms probabilistic LLM calls into **verifiable, replayable, and cost‑autonomous engineering events**.

> *"A verdict you can verify — not a black box you must blindly trust."*

---

## 🎯 Why VERIDACTUS?

LLM inference is inherently probabilistic — but governance demand is deterministic. Compliance officers need hard budget limits, auditors need offline‑verifiable records, and platform engineers need drop‑in integration that doesn't require a new protocol.

| For Auditors | For Engineers | For Business |
|:---|:---|:---|
| Offline‑verifiable SHA‑256 audit proofs | Drop‑in HTTP headers (no custom protocol) | Real‑time streaming budget enforcement |
| Recursive non‑signature field stripping | Compatible with any OpenAI‑compatible API | Micro‑dollar precision cost metering |
| Evidence‑chain lineage via `parent_id` | Sidecar, Gateway, or SDK deployment | Privacy‑tiered storage (raw/masked/hash_only) |

---

## 🏗 Architecture

```
┌───────────────────┐     ┌──────────────────────┐     ┌───────────────────┐
│   React UI         │────▶│   Go Control Plane    │────▶│   Rust Data Plane  │
│   veridactus-ui    │     │   control-plane       │     │   core             │
│   :3000            │     │   :8081 · REST +      │     │   :8080            │
│   Pipeline Designer│     │   SQLite · Auth       │     │   Pipeline +       │
└───────────────────┘     └──────────────────────┘     │   L0 / L2A / L2B   │
                                                        └─────────┬─────────┘
                                                                  │
                                                        ┌─────────▼─────────┐
                                                        │   Upstream LLM     │
                                                        │   (OpenAI API)     │
                                                        └───────────────────┘
```

---

## 📦 Repositories

| Repository | Purpose | Status |
|:-----------|:--------|:-------|
| [**veridactus**](https://github.com/veridactus/veridactus) | Core implementation — Rust data plane, Go control plane, React UI, protocol docs | ![Active](https://img.shields.io/badge/active-brightgreen?style=flat-square) |
| [**docs**](https://github.com/veridactus/docs) | Protocol specification v0.2.1, JSON schemas, OpenAPI, conformance suite, RFCs | ![Active](https://img.shields.io/badge/active-brightgreen?style=flat-square) |

---

## 🔐 Cryptographic Proof Chain

| Level | Type | Mechanism | Status |
|:------|:-----|:----------|:-------|
| **L0** | Hash Chain | SHA‑256 integrity via JCS (RFC 8785) canonicalization | ✅ Production |
| **L1** | TEE Attestation | Hardware enclave (Intel TDX, AMD SEV‑SNP, NVIDIA CC) | 🟡 Type defs |
| **L2A** | Sampling Verification | Merkle tree random sampling (IMMACULATE framework) | ✅ Production |
| **L2B** | Zero-Knowledge | NANOZK‑style layered commitment proofs | ✅ Production |

---

## 🛡 Governance Pipeline

7 production plugins enforce policy at every stage of the LLM request lifecycle:

| Plugin | Stage | Capability |
|:-------|:------|:-----------|
| `BudgetGuard` | pre_request | Micro‑dollar budget control ($0.000001 precision) |
| `PiiDetector` | pre_request | PII detection & masking (regex + NER patterns) |
| `InputSanitizer` | pre_request | Prompt injection & jailbreak defense |
| `G1InputFilter` | pre_request | OWASP‑aligned input safety guard |
| `G2OutputFilter` | post_response | Harmful content output guard |
| `G3SemanticGuard` | post_response | Factual consistency & domain rules |
| `ResponseValidator` | post_response | JSON schema validation for structured outputs |

---

## ✨ Capability Matrix

| Capability | Description | Compliance Impact |
|:-----------|:------------|:------------------|
| 🔐 **Cryptographic Verdict** | JCS + SHA‑256 hash over the full Execution Contract | EU AI Act, HIPAA, SOC 2 |
| 💰 **Streaming Budget** | Real‑time SSE budget enforcement with atomic hard‑stop | AI FinOps, cost governance |
| 🛡️ **Privacy Grading** | `raw` → `masked` → `hash_only` → TEE‑Private | GDPR, CCPA right‑to‑erasure |
| 🔄 **Deterministic Replay** | RFC 8785 canonicalized reproducible traces | Model regression CI/CD |
| 🔗 **Delegation Chain** | Composite attestation (Ed25519 + TEE + ZK) | Multi‑agent trust chains |
| 🔍 **OWASP ASI Top 10** | Full alignment with ASI01–ASI10 | Agentic AI security compliance |
| 📋 **Auto‑Compliance** | EU AI Act / NIST AI 600‑1 reports per inference | Regulatory audit readiness |

---

## 🚀 Quick Start

```bash
# 1. Start VERIDACTUS proxy (reference implementation)
docker run -p 8080:8080 ghcr.io/veridactus/veridactus:latest

# 2. Send a governed inference request
curl -X POST http://localhost:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "VERIDACTUS-Version: 0.2" \
  -H "VERIDACTUS-Budget-Limit: 0.050000" \
  -H "VERIDACTUS-Privacy-Level: masked" \
  -d '{
    "model": "openai/gpt-4o",
    "messages": [{"role": "user", "content": "Draft a compliance summary."}]
  }'

# 3. Every response carries a cryptographically‑signed VERIDACTUS-Trace-Id
#    Verify it offline — no central database required
```

> 📖 Full guide at [docs.veridactus.ai/quickstart](https://docs.veridactus.ai/quickstart) · [Protocol Specification v0.2.1](https://docs.veridactus.ai/specification/latest)

---

## 🐳 Docker Images

| Image | Component | Stack |
|:------|:----------|:------|
| `veridactus/veridactus-core` | Data Plane — AI proxy gateway | Rust · Axum · SSE |
| `veridactus/veridactus-cp` | Control Plane — config & auth | Go · SQLite · REST |
| `veridactus/veridactus-ui` | Frontend — admin dashboard | React · ReactFlow |
| `veridactus/veridactus-python-worker` | Worker — PII detection | Python |

---

## 📚 Resources

| Resource | Link |
|:---------|:-----|
| **Documentation Site** | [docs.veridactus.ai](https://docs.veridactus.ai) |
| **Protocol Specification v0.2.1** | [Full Spec](https://docs.veridactus.ai/specification/latest) |
| **OpenAPI Specification** | [api/openapi.json](https://github.com/veridactus/docs/blob/main/api/openapi.json) |
| **JSON Schemas** | [schemas/v0.2.1](https://github.com/veridactus/docs/tree/main/schemas/v0.2.1) |
| **Conformance Suite** | [conformance/v0.2.1](https://github.com/veridactus/docs/tree/main/conformance/v0.2.1) |
| **RFC Process** | [rfcs/README.md](https://github.com/veridactus/docs/blob/main/rfcs/README.md) |

---

## 🌐 Community & Governance

VERIDACTUS follows an **Open Meritocracy** governance model. All RFCs and design decisions happen transparently on GitHub.

| Channel | Link |
|:--------|:-----|
| **GitHub Discussions** | [github.com/veridactus/docs/discussions](https://github.com/veridactus/docs/discussions) |
| **TSC Contact** | [tsc@veridactus.ai](mailto:tsc@veridactus.ai) |
| **Security Reporting** | [security@veridactus.ai](mailto:security@veridactus.ai) |
| **Twitter / X** | [@veridactus](https://twitter.com/veridactus) |
| **Governance Model** | [GOVERNANCE.md](https://github.com/veridactus/docs/blob/main/GOVERNANCE.md) |
| **Contributing Guide** | [CONTRIBUTING.md](https://github.com/veridactus/docs/blob/main/CONTRIBUTING.md) |
| **Code of Conduct** | [CODE_OF_CONDUCT.md](https://github.com/veridactus/docs/blob/main/CODE_OF_CONDUCT.md) |

---

<p align="center">
  <sub>Licensed under <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE">Apache License 2.0</a> · Copyright 2026 The VERIDACTUS Authors</sub>
</p>
