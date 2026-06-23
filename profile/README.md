<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/veridactus/docs/main/images/logo/dark.svg">
    <img alt="VERIDACTUS" src="https://raw.githubusercontent.com/veridactus/docs/main/images/logo/light.svg" width="520">
  </picture>
</p>

<p align="center">
  <strong>Trusted AI Execution Governance Infrastructure</strong>
</p>

<p align="center">
  <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License"></a>
  <a href="https://docs.veridactus.ai/specification/latest"><img src="https://img.shields.io/badge/Protocol-v0.2.1-%2338BDF8" alt="Protocol Specification"></a>
  <a href="https://github.com/veridactus/veridactus/actions/workflows/validate.yml"><img src="https://github.com/veridactus/veridactus/actions/workflows/validate.yml/badge.svg" alt="CI"></a>
  <a href="https://docs.veridactus.ai"><img src="https://img.shields.io/badge/Docs-docs.veridactus.ai-%230ea5e9" alt="Documentation"></a>
  <a href="https://github.com/veridactus/docs/discussions"><img src="https://img.shields.io/badge/Discussions-Welcome-%238b5cf6" alt="Discussions"></a>
</p>

---

**VERIDACTUS** is the constitutional blueprint for trustworthy AI governance — a deterministic control plane that layers atop existing OpenAI‑compatible APIs. It transforms probabilistic LLM interactions into **independently‑auditable, replay‑deterministic, and delegation‑traceable engineering events** through a standardized, cryptographically‑verifiable interface.

> Open Governance for LLM Inference. Zero‑trust. Drop‑in. Audit‑ready.

---

## 🏗 Architecture

```
┌─────────────────┐     ┌──────────────────────┐     ┌──────────────────┐
│   React UI       │────▶│   Go Control Plane    │────▶│   Rust Data Plane │
│   (veridactus-ui)│     │   (control-plane)     │     │   (core)          │
│   :3000          │     │   :8081               │     │   :8080           │
│                  │     │   REST API + SQLite    │     │   Pipeline +      │
└─────────────────┘     └──────────────────────┘     │   L0/L2A/L2B      │
                                                      └────────┬─────────┘
                                                               │
                                                      ┌────────▼─────────┐
                                                      │   Upstream LLM    │
                                                      │   (OpenAI API)    │
                                                      └──────────────────┘
```

---

## 📦 Repositories

| Repository | Description | Language | Status |
|:-----------|:------------|:---------|:-------|
| [**veridactus**](https://github.com/veridactus/veridactus) | Core implementation — Rust data plane, Go control plane, React UI | ![Rust](https://img.shields.io/badge/Rust-orange) ![Go](https://img.shields.io/badge/Go-00ADD8) ![TypeScript](https://img.shields.io/badge/TS-3178C6) | ![Active](https://img.shields.io/badge/status-active-brightgreen) |
| [**docs**](https://github.com/veridactus/docs) | Protocol specification v0.2.1, JSON schemas, conformance suite, RFCs | ![MDX](https://img.shields.io/badge/MDX-1A1A1A) | ![Active](https://img.shields.io/badge/status-active-brightgreen) |
| [**audit-cli**](https://github.com/veridactus/audit-cli) | Offline cryptographic audit verification tool | ![TypeScript](https://img.shields.io/badge/TS-3178C6) | ![Planned](https://img.shields.io/badge/status-planned-yellow) |
| [**sdk-python**](https://github.com/veridactus/sdk-python) | Python SDK with native VERIDACTUS header support | ![Python](https://img.shields.io/badge/Python-3776AB) | ![Planned](https://img.shields.io/badge/status-planned-yellow) |
| [**validator-js**](https://github.com/veridactus/validator-js) | JavaScript protocol validator for v0.2.1 | ![TypeScript](https://img.shields.io/badge/TS-3178C6) | ![Planned](https://img.shields.io/badge/status-planned-yellow) |
| [**.github**](https://github.com/veridactus/.github) | Organization profile, community health files, CI templates | — | ![Active](https://img.shields.io/badge/status-active-brightgreen) |

---

## ✨ Key Features

### 🔐 Cryptographic Proof Chain (L0 → L2B)

| Level | Type | Description | Status |
|:------|:-----|:------------|:-------|
| **L0** | Hash Chain | SHA‑256 integrity via JCS canonicalization | ✅ Production |
| **L1** | TEE Attestation | Hardware enclave (Intel TDX, AMD SEV‑SNP, NVIDIA CC) | 🟡 Type defs |
| **L2A** | Sampling Verification | Merkle tree random sampling (IMMACULATE framework) | ✅ Production |
| **L2B** | Zero-Knowledge | NANOZK‑style layered commitment proofs | ✅ Production |

### 🛡 Governance Pipeline

| Plugin | Stage | Capability |
|:-------|:------|:-----------|
| `BudgetGuard` | pre_request | Micro‑dollar budget control ($0.000001 precision) |
| `PiiDetector` | pre_request | PII detection & masking (regex + NER patterns) |
| `InputSanitizer` | pre_request | Prompt injection & jailbreak defense |
| `G1InputFilter` | pre_request | OWASP‑aligned input safety guard |
| `G2OutputFilter` | post_response | Harmful content output guard |
| `G3SemanticGuard` | post_response | Factual consistency & domain rules |
| `ResponseValidator` | post_response | JSON schema validation for structured outputs |

### ⚡ Additional Capabilities

- **Streaming Budget Control** — Real‑time SSE budget enforcement with micro‑dollar precision
- **Active Prevention** — Token‑level constrained decoding via DFA pattern matching
- **Privacy Tiers** — `raw` → `masked` → `hash_only` → TEE‑Private with GDPR right‑to‑erasure
- **Delegation Chain** — Composite attestation (Ed25519 + TEE + ZK) for multi‑agent trust
- **OWASP ASI Top 10** — Full alignment with OWASP Agentic AI Security risks ASI01‑ASI10
- **Compliance Reports** — Auto‑generated EU AI Act / NIST AI 600‑1 compliance per inference

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

# 3. Verify the cryptographic audit signature
# Use the audit-cli to independently verify integrity
```

> 📖 Full guide: [docs.veridactus.ai/quickstart](https://docs.veridactus.ai/quickstart)

---

## 🐳 Docker Images

| Image | Description |
|:------|:------------|
| `veridactus/veridactus-core` | Rust data plane — AI proxy gateway |
| `veridactus/veridactus-cp` | Go control plane — configuration management |
| `veridactus/veridactus-ui` | React frontend — admin dashboard |
| `veridactus/veridactus-python-worker` | Python worker — enhanced PII detection |

```bash
curl -O https://raw.githubusercontent.com/veridactus/veridactus/main/deploy/docker-compose.yml
docker-compose up -d
```

---

## 📚 Resources

| Resource | Link |
|:---------|:-----|
| **Documentation Site** | [docs.veridactus.ai](https://docs.veridactus.ai) |
| **Protocol Specification v0.2.1** | [Full Spec](https://docs.veridactus.ai/specification/latest) |
| **Architecture Guide** | [ARCHITECTURE.md](https://github.com/veridactus/veridactus/blob/main/docs/architecture/ARCHITECTURE.md) |
| **Conformance Suite** | [conformance/v0.2.1](https://github.com/veridactus/docs/tree/main/conformance/v0.2.1) |
| **OpenAPI Spec** | [api/openapi.json](https://github.com/veridactus/docs/blob/main/api/openapi.json) |
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
| **Code of Conduct** | [CODE_OF_CONDUCT.md](https://github.com/veridactus/docs/blob/main/CODE_OF_CONDUCT.md) |

---

## 🤝 Contributing

We welcome contributions across all repositories:

- **Specification improvements** — Open issues or RFC proposals on [veridactus/docs](https://github.com/veridactus/docs)
- **Core development** — Check [CONTRIBUTING.md](https://github.com/veridactus/veridactus/blob/main/CONTRIBUTING.md)
- **Conformance tests** — Expand cross‑implementation coverage
- **Documentation** — Improve clarity, add examples, fix errors

See individual repository contribution guides for language‑specific standards and DCO requirements.

---

<p align="center">
  <sub>Licensed under <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE">Apache License 2.0</a> · Copyright 2026 The VERIDACTUS Authors</sub>
</p>
