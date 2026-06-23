<div align="center">

# VERIDACTUS

### The Constitutional Blueprint for Trustworthy AI Governance

[![License](https://img.shields.io/badge/License-Apache%202.0-blue?style=flat-square)](https://github.com/veridactus/veridactus/blob/main/LICENSE)
[![Rust](https://img.shields.io/badge/Rust-1.75+-orange?style=flat-square&logo=rust)](https://github.com/veridactus/veridactus)
[![Go](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat-square&logo=go)](https://github.com/veridactus/veridactus)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-3178C6?style=flat-square&logo=typescript)](https://github.com/veridactus/veridactus)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat-square&logo=docker)](https://hub.docker.com/u/veridactus)

</div>

---

**VERIDACTUS** transforms probabilistic LLM interactions into **independently-auditable, replay-deterministic, and delegation-traceable engineering events** through a standardized, cryptographically-verifiable interface.

> *"A verdict you can verify — not a black box you must blindly trust."*

---

## 🎯 The Problem

LLM inference is inherently probabilistic — but governance demand is deterministic.

| Auditors Need | Engineers Need | Business Needs |
|:---|:---|:---|
| Offline-verifiable proof | Drop-in integration | Real-time cost control |
| Tamper-evident records | No custom protocol | Privacy compliance |
| Chain of custody | Any OpenAI-compatible API | Audit-ready reports |

**VERIDACTUS delivers all three.** Through declarative constraints, state-machine tracing, and cryptographic audit — all as standard HTTP headers.

---

## 🏗 Architecture

```
┌─────────────────┐     ┌──────────────────────┐     ┌──────────────────┐
│   React UI       │────▶│   Go Control Plane    │────▶│   Rust Data Plane │
│   veridactus-ui  │     │   control-plane       │     │   core            │
│   :3000          │     │   :8081               │     │   :8080           │
│                  │     │   REST API + SQLite    │     │   Pipeline +      │
└─────────────────┘     └──────────────────────┘     │   L0 / L2A / L2B  │
                                                      └────────┬─────────┘
                                                               │
                                                      ┌────────▼─────────┐
                                                      │   Upstream LLM    │
                                                      │   (OpenAI API)    │
                                                      └──────────────────┘
```

---

## 🔐 Cryptographic Proof Chain

| Level | Type | Mechanism | Status |
|:------|:-----|:----------|:-------|
| **L0** | Hash Chain | SHA‑256 integrity via JCS canonicalization | ✅ Production |
| **L1** | TEE Attestation | Hardware enclave (Intel TDX, AMD SEV‑SNP, NVIDIA CC) | 🟡 Type defs |
| **L2A** | Sampling Verification | Merkle tree random sampling (IMMACULATE framework) | ✅ Production |
| **L2B** | Zero-Knowledge | NANOZK-style layered commitment proofs | ✅ Production |

---

## 🛡 Governance Pipeline — 7 Production Plugins

| Plugin | Stage | Capability |
|:-------|:------|:-----------|
| `BudgetGuard` | pre_request | Micro-dollar budget control ($0.000001 precision) |
| `PiiDetector` | pre_request | PII detection & masking (regex + NER patterns) |
| `InputSanitizer` | pre_request | Prompt injection & jailbreak defense |
| `G1InputFilter` | pre_request | OWASP-aligned input safety guard |
| `G2OutputFilter` | post_response | Harmful content output guard |
| `G3SemanticGuard` | post_response | Factual consistency & domain rules |
| `ResponseValidator` | post_response | JSON schema validation for structured outputs |

---

## ✨ Full Capability Matrix

| Capability | Description | Compliance Impact |
|:-----------|:------------|:------------------|
| 🔐 **Cryptographic Verdict** | JCS + SHA‑256 hash over the full Execution Contract | EU AI Act, HIPAA, SOC 2 |
| 💰 **Streaming Budget Control** | Real-time SSE budget enforcement with atomic hard-stop | AI FinOps, cost governance |
| 🛡️ **Privacy Grading** | `raw` / `masked` / `hash_only` → TEE-Private | GDPR, CCPA right-to-erasure |
| 🔄 **Deterministic Replay** | RFC 8785 canonicalization for reproducible traces | Model regression testing |
| 🔗 **Delegation Chain** | Composite attestation (Ed25519 + TEE + ZK) | Multi-agent trust chains |
| 🔍 **OWASP ASI Top 10** | Full alignment with ASI01–ASI10 | Agentic AI security compliance |
| 📋 **Compliance Reports** | Auto-generated EU AI Act / NIST AI 600-1 per inference | Regulatory audit readiness |

---

## 🚀 Quick Start

```bash
# 1. Start infrastructure
docker-compose -f scripts/docker-compose.yml up -d

# 2. Start VERIDACTUS proxy
docker run -p 8080:8080 ghcr.io/veridactus/veridactus:latest

# 3. Send a governed request
curl -X POST http://localhost:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "VERIDACTUS-Version: 0.2" \
  -H "VERIDACTUS-Budget-Limit: 0.050000" \
  -H "VERIDACTUS-Privacy-Level: masked" \
  -d '{
    "model": "openai/gpt-4o",
    "messages": [{"role": "user", "content": "Draft a compliance summary."}]
  }'

# 4. Every response carries a cryptographically-signed VERIDACTUS-Trace-Id.
#    Audit it independently — no central database required.
```

> 📖 Full documentation and protocol specification in the [main repository](https://github.com/veridactus/veridactus).

---

## 🐳 Docker Images

| Image | Component | Technology |
|:------|:----------|:-----------|
| `veridactus/veridactus-core` | Data Plane — AI proxy gateway | Rust |
| `veridactus/veridactus-cp` | Control Plane — configuration management | Go |
| `veridactus/veridactus-ui` | Frontend — admin dashboard | React / TypeScript |
| `veridactus/veridactus-python-worker` | Worker — enhanced PII detection | Python |

```bash
curl -O https://raw.githubusercontent.com/veridactus/veridactus/main/deploy/docker-compose.yml
docker-compose up -d
```

---

## 📦 Repository

| Repository | Description | Language |
|:-----------|:------------|:---------|
| [**veridactus**](https://github.com/veridactus/veridactus) | Core implementation — data plane, control plane, UI, protocol specification | Rust · Go · TypeScript · Python |

> 🏗️ Additional repositories for SDKs, audit tools, and conformance suites are in development.

---

## 🌐 Community

VERIDACTUS follows an **Open Meritocracy** governance model steered by a Technical Steering Committee (TSC).

| Channel | Link |
|:--------|:-----|
| **GitHub Issues** | [Report bugs or request features](https://github.com/veridactus/veridactus/issues) |
| **Security Reporting** | [security@veridactus.ai](mailto:security@veridactus.ai) |
| **Twitter / X** | [@veridactus](https://twitter.com/veridactus) |
| **Governance** | [GOVERNANCE.md](https://github.com/veridactus/veridactus/blob/main/GOVERNANCE.md) |
| **Contributing** | [CONTRIBUTING.md](https://github.com/veridactus/veridactus/blob/main/CONTRIBUTING.md) |

---

<div align="center">
  <sub>
    Licensed under <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE">Apache License 2.0</a>
    · Copyright 2026 The VERIDACTUS Authors
  </sub>
</div>
