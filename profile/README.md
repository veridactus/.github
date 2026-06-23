<p align="center">
  <!-- GitHub native dark/light mode image switching -->
  <img alt="VERIDACTUS — The Verifiable Execution Layer for AI Agents" src="https://raw.githubusercontent.com/veridactus/.github/main/assets/logo-light.svg#gh-light-mode-only" width="600">
  <img alt="VERIDACTUS — The Verifiable Execution Layer for AI Agents" src="https://raw.githubusercontent.com/veridactus/.github/main/assets/logo-dark.svg#gh-dark-mode-only" width="600">
</p>

<h3 align="center">The Verifiable Execution Layer for AI Agents</h3>
<p align="center">
  <em>Every LLM invocation becomes a deterministic, cryptographically verifiable engineering event.</em><br>
  <strong>No server. No secret. No trust required.</strong>
</p>

<p align="center">
  <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache%202.0-blue?style=for-the-badge" alt="License"></a>
  <a href="https://docs.veridactus.ai/specification/latest"><img src="https://img.shields.io/badge/spec-v0.2.1-38BDF8?style=for-the-badge" alt="Spec"></a>
  <a href="https://docs.veridactus.ai"><img src="https://img.shields.io/badge/docs-online-0ea5e9?style=for-the-badge" alt="Docs"></a>
</p>

<p align="center">
  <a href="https://github.com/veridactus/veridactus"><img src="https://img.shields.io/badge/Rust-1.75+-orange?style=flat-square&logo=rust" alt="Rust"></a>
  <a href="https://github.com/veridactus/veridactus"><img src="https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat-square&logo=go" alt="Go"></a>
  <a href="https://github.com/veridactus/veridactus"><img src="https://img.shields.io/badge/TypeScript-5.0+-3178C6?style=flat-square&logo=typescript" alt="TypeScript"></a>
  <a href="https://github.com/veridactus/veridactus"><img src="https://img.shields.io/badge/Python-3.11+-3776AB?style=flat-square&logo=python" alt="Python"></a>
  <a href="https://hub.docker.com/u/veridactus"><img src="https://img.shields.io/badge/Docker-ready-2496ED?style=flat-square&logo=docker" alt="Docker"></a>
</p>

<p align="center">
  <a href="#-quick-start">⚡ Quick Start</a> ·
  <a href="#-why-veridactus">🎯 Why</a> ·
  <a href="#-strategic-positioning">🌐 Positioning</a> ·
  <a href="#-architecture">🏗 Architecture</a> ·
  <a href="#-zero-trust-verification">🔒 Trust Model</a> ·
  <a href="#-community">🌐 Community</a>
</p>

---

**VERIDACTUS** is the constitutional blueprint for trustworthy AI governance — a deterministic control plane that layers atop existing OpenAI‑compatible APIs. Through declarative constraints, state‑machine tracing, and cryptographic audit, it transforms probabilistic LLM calls into **verifiable, replayable, and cost‑autonomous engineering events**.

> *"A verdict you can verify — not a black box you must blindly trust."*

---

## 🧭 The Name As a Design Contract

Great protocols are named after the thing they guarantee. `VERIDACTUS` is no exception.

| Root | Origin | Meaning | Protocol Mapping |
|:-----|:-------|:--------|:-----------------|
| **`Verus`** | Latin | *true, real, verified* | Cryptographic integrity — every trace is independently provable via RFC 8785 + SHA‑256 |
| **`Actus`** | Latin | *action, execution, legal deed* | Enforcement backbone — streaming budget cutoffs, privacy masking, deterministic replay |

**Together**: *a verified deed of execution*. The protocol doesn't just observe what an AI did — it cryptographically proves **the contract under which it acted**.

---

## 🌐 Strategic Positioning

The AI agent revolution has solved **connectivity** and **coordination** — but left a foundational gap: **verifiability**.

```
┌─────────────────────────────────────────────────────────┐
│                   AI Agent Applications                  │
├─────────────────────────────────────────────────────────┤
│  Coordination Layer     │  MCP · A2A · mAgent           │
├─────────────────────────────────────────────────────────┤
│  Connectivity Layer     │  REST APIs · gRPC · WebSocket  │
├─────────────────────────────────────────────────────────┤
│  ✅ VERIDACTUS          │  Verifiable Execution Layer    │
├─────────────────────────────────────────────────────────┤
│  LLM Providers          │  OpenAI · Anthropic · etc.     │
└─────────────────────────────────────────────────────────┘
```

VERIDACTUS is **orthogonal, not competitive**. It acts as a transparent governance proxy — no client code changes, no extra network hops.

### Protocol Comparison

| Aspect | MCP (Anthropic) | A2A (Google) | IETF AAT | **VERIDACTUS** |
|:-------|:----------------|:-------------|:---------|:---------------|
| **Purpose** | Tool connectivity | Agent coordination | Audit log format | **Verifiable execution proof** |
| **Core Question** | *Can the agent reach the tool?* | *Can agents talk?* | *What happened?* | ***How, why, and under what rules?*** |
| **Verification** | Out of scope | Out of scope | Trust in logging | **Zero‑trust, offline mathematical proof** |
| **Runtime Enforcement** | None | None | None | **Real‑time budget cutoff, privacy masking** |
| **Cryptographic Integrity** | None | None | None | **JCS + SHA‑256 hash chain** |

> MCP connects tools. A2A coordinates agents. AAT records events. **VERIDACTUS delivers the cryptographic verdict that those events are true.**

---

## 🧠 Core Abstraction: The Execution Contract

Every LLM call is modeled as a verifiable **four‑tuple lifecycle**:

```
  📥 Input ──▶ ⚙️ Constraints ──▶ 📈 Observations ──▶ 🔐 Proofs
  Request        Declared            Runtime             Cryptographic
  snapshot       boundaries          telemetry           verdict
```

| Tuple | Generated When | Protocol Guarantee |
|:------|:---------------|:-------------------|
| **📥 Input** | `INIT` phase | Immutable baseline for diff & replay |
| **⚙️ Constraints** | `CONSTRAINT_EVAL` phase | Violations block upstream *before* tokens consumed |
| **📈 Observations** | `EXECUTING` → `VALIDATION` | Real‑time budget cutoff, degrade strategies |
| **🔐 Proofs** | `FINALIZED` or `FAILED` | Any party can recompute offline — no key, no database |

---

## 🔒 Zero‑Trust Verification

VERIDACTUS operates on a radical assumption: **the network, the proxy, even the storage are all hostile**. Independent verification requires only three public things:

1. The raw Trace JSON
2. The public [RFC 8785 JSON Canonicalization Scheme](https://www.rfc-editor.org/rfc/rfc8785)
3. Any SHA‑256 implementation

```bash
# Offline verification — no proxy, no SDK, no central authority
jq 'del(._*, .observations.internal_metrics)' trace.json | \
  v8s jcs | sha256sum

# Compare against trace.proofs.audit_signature
# ✅ Match → The verdict is intact.
# ❌ Mismatch → Tampering detected.
```

> 🔐 *This is the cryptographic equivalent of a judicial evidence seal. VERIDACTUS seals every single AI action the same way.*

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

| Repository | Purpose |
|:-----------|:--------|
| [**veridactus**](https://github.com/veridactus/veridactus) | Core implementation — Rust data plane, Go control plane, React UI, protocol docs |
| [**docs**](https://github.com/veridactus/docs) | Protocol specification v0.2.1, JSON schemas, OpenAPI, conformance suite, RFCs |

---

## 🎯 Why VERIDACTUS?

| For Auditors | For Engineers | For Business |
|:---|:---|:---|
| Offline‑verifiable SHA‑256 audit proofs | Drop‑in HTTP headers (no custom protocol) | Real‑time streaming budget enforcement |
| Recursive non‑signature field stripping | Compatible with any OpenAI‑compatible API | Micro‑dollar precision cost metering |
| Evidence‑chain lineage via `parent_id` | Sidecar, Gateway, or SDK deployment | Privacy‑tiered storage |

---

## 🔐 Cryptographic Proof Chain

| Level | Type | Mechanism | Status |
|:------|:-----|:----------|:-------|
| **L0** | Hash Chain | SHA‑256 integrity via JCS (RFC 8785) | ✅ Production |
| **L1** | TEE Attestation | Intel TDX · AMD SEV‑SNP · NVIDIA CC | 🟡 Type defs |
| **L2A** | Sampling Verification | Merkle tree random sampling (IMMACULATE) | ✅ Production |
| **L2B** | Zero-Knowledge | NANOZK‑style layered commitment proofs | ✅ Production |

---

## 🛡 Governance Pipeline — 7 Production Plugins

| Plugin | Stage | Capability |
|:-------|:------|:-----------|
| `BudgetGuard` | pre_request | Micro‑dollar budget control ($0.000001 precision) |
| `PiiDetector` | pre_request | PII detection & masking (regex + NER) |
| `InputSanitizer` | pre_request | Prompt injection & jailbreak defense |
| `G1InputFilter` | pre_request | OWASP‑aligned input safety guard |
| `G2OutputFilter` | post_response | Harmful content output guard |
| `G3SemanticGuard` | post_response | Factual consistency & domain rules |
| `ResponseValidator` | post_response | JSON schema validation for structured outputs |

---

## ✨ Capability Matrix

| Capability | Description | Compliance Impact |
|:-----------|:------------|:------------------|
| 🔐 **Cryptographic Verdict** | JCS + SHA‑256 over the full Execution Contract | EU AI Act · HIPAA · SOC 2 |
| 💰 **Streaming Budget** | Real‑time SSE enforcement with atomic hard‑stop | AI FinOps · cost governance |
| 🛡️ **Privacy Grading** | `raw` → `masked` → `hash_only` → TEE‑Private | GDPR · CCPA right‑to‑erasure |
| 🔄 **Deterministic Replay** | RFC 8785 canonicalized reproducible traces | Model regression CI/CD |
| 🔗 **Delegation Chain** | Composite attestation (Ed25519 + TEE + ZK) | Multi‑agent trust chains |
| 🔍 **OWASP ASI Top 10** | Full alignment with ASI01–ASI10 | Agentic AI security |
| 📋 **Auto‑Compliance** | EU AI Act / NIST AI 600‑1 per inference | Regulatory readiness |

---

## 🌍 Standards & Compliance Alignment

| Standard / Framework | VERIDACTUS Mapping |
|:---------------------|:-------------------|
| **NIST AI RMF 1.0** | `constraints` → GOVERN, `observations` → MAP, `audit` → MANAGE |
| **ISO/IEC 42001** | Execution lifecycle + tamper‑evident proofs support AIMS |
| **GDPR / CCPA** | Privacy grading, TTL expiry, deletion audit logs |
| **EU AI Act (Art. 12)** | Cryptographically signed logs for high‑risk AI record‑keeping |
| **W3C PROV** | Lineage via `parent_id` ⇔ `prov:wasDerivedFrom` |
| **OWASP LLM Top 10 v2.0** | Threat model: prompt injection, unbounded consumption, insecure output |

> 🏛️ Your compliance playbook already exists. VERIDACTUS just gives it **cryptographic teeth**.

---

## 🏅 Conformance Certification

Fully automated, objective, no‑gatekeeper. Implementations earn badges by passing public test vectors:

| Tier | Requirements |
|:-----|:-------------|
| 🔵 **Core Compatible** | Schema validation + Proof integrity + Header negotiation |
| 🟢 **Full Compatible** | Core + Budget enforcement + State machine + Error contract |
| 🟡 **Extended Compatible** | Full + ≥2 official extensions |

---

## 🚀 Quick Start

```bash
# 1. Start VERIDACTUS proxy
docker run -p 8080:8080 ghcr.io/veridactus/veridactus:latest

# 2. Send a governed request
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
```

> 📖 [Quickstart Guide](https://docs.veridactus.ai/quickstart) · [Specification v0.2.1](https://docs.veridactus.ai/specification/latest)

---

## 🐳 Docker Images

| Image | Component | Stack |
|:------|:----------|:------|
| `veridactus/veridactus-core` | Data Plane — AI proxy gateway | Rust · Axum · SSE |
| `veridactus/veridactus-cp` | Control Plane — config & auth | Go · SQLite · REST |
| `veridactus/veridactus-ui` | Frontend — admin dashboard | React · ReactFlow |
| `veridactus/veridactus-python-worker` | Worker — PII detection | Python |

---

## ⚖️ Design Tradeoffs

| Tradeoff | VERIDACTUS Stance |
|:---------|:------------------|
| **Real‑time vs. eventual integrity** | Constraints enforced in real time; cryptographic verdict verified offline |
| **Trace fidelity vs. performance** | Spec defines *what must be captured*, never *how heavy the logger must be* |
| **Compliance vs. agility** | Innovation happens in namespace‑isolated extensions |
| **Readability vs. storage** | Audit exports always JSON; internal storage can be Parquet/Protobuf |

---

## 🗓️ Roadmap

| Version | Timeline | Milestone |
|:--------|:---------|:----------|
| **v0.2.1** | Current | Core contract, cryptographic verdict, streaming budget, privacy grading |
| **v1.0.0** | Upcoming | Stable protocol, backward‑compatible, production‑hardened |
| **v1.1.0** | Planned | Batch governance, federated audit chains |
| **v2.0.0** | Vision | Post‑quantum signatures, ZK proofs, TEE attestation |

---

## 📚 Resources

| Resource | Link |
|:---------|:-----|
| **Documentation Site** | [docs.veridactus.ai](https://docs.veridactus.ai) |
| **Specification v0.2.1** | [Full Spec](https://docs.veridactus.ai/specification/latest) |
| **OpenAPI** | [api/openapi.json](https://github.com/veridactus/docs/blob/main/api/openapi.json) |
| **JSON Schemas** | [schemas/v0.2.1](https://github.com/veridactus/docs/tree/main/schemas/v0.2.1) |
| **Conformance Suite** | [conformance/v0.2.1](https://github.com/veridactus/docs/tree/main/conformance/v0.2.1) |
| **RFC Process** | [rfcs/README.md](https://github.com/veridactus/docs/blob/main/rfcs/README.md) |

---

## 🌐 Community & Governance

**Open Meritocracy** model steered by a Technical Steering Committee (TSC).

| Channel | Link |
|:--------|:-----|
| **Discussions** | [github.com/veridactus/docs/discussions](https://github.com/veridactus/docs/discussions) |
| **TSC** | [tsc@veridactus.ai](mailto:tsc@veridactus.ai) |
| **Security** | [security@veridactus.ai](mailto:security@veridactus.ai) |
| **Twitter / X** | [@veridactus](https://twitter.com/veridactus) |
| **Governance** | [GOVERNANCE.md](https://github.com/veridactus/docs/blob/main/GOVERNANCE.md) |
| **Contributing** | [CONTRIBUTING.md](https://github.com/veridactus/docs/blob/main/CONTRIBUTING.md) |
| **Code of Conduct** | [CODE_OF_CONDUCT.md](https://github.com/veridactus/docs/blob/main/CODE_OF_CONDUCT.md) |

---

## 📄 Academic Citation

```bibtex
@misc{veridactus2026,
  title        = {VERIDACTUS: A Verifiable Execution Protocol for AI Agents},
  author       = {Lee, William and the VERIDACTUS Community},
  year         = {2026},
  howpublished = {\url{https://github.com/veridactus/docs}},
  note         = {v0.2.1 Specification}
}
```

---

<p align="center">
  <sub>
    Licensed under <a href="https://github.com/veridactus/veridactus/blob/main/LICENSE">Apache 2.0</a>
    · Copyright 2026 The VERIDACTUS Authors<br>
    "VERIDACTUS" and its logo are marks of the VERIDACTUS Protocol community
  </sub>
</p>
