# Support

## Getting Help

### Documentation

- **Protocol Specification**: [docs.veridactus.ai](https://docs.veridactus.ai)
- **Quickstart Guide**: [docs.veridactus.ai/quickstart](https://docs.veridactus.ai/quickstart)
- **Architecture Guide**: [ARCHITECTURE.md](https://github.com/veridactus/veridactus/blob/main/docs/architecture/ARCHITECTURE.md)

### Community Channels

| Channel | Purpose |
|:--------|:--------|
| [GitHub Discussions](https://github.com/veridactus/docs/discussions) | Questions, ideas, general discussion |
| [GitHub Issues](https://github.com/veridactus/docs/issues) | Bug reports, specification issues |
| [RFC Process](https://github.com/veridactus/docs/blob/main/rfcs/README.md) | Protocol change proposals |
| [@veridactus](https://twitter.com/veridactus) | Announcements and updates |

### Direct Contact

- **TSC**: [tsc@veridactus.ai](mailto:tsc@veridactus.ai) — governance, RFC questions
- **Security**: [security@veridactus.ai](mailto:security@veridactus.ai) — vulnerability reports only

## Frequently Asked Questions

### What is VERIDACTUS?

VERIDACTUS is an open governance protocol for LLM inference. It provides declarative constraints, cryptographic audit, and streaming budget control as a drop-in layer atop OpenAI-compatible APIs.

### How do I get started?

```bash
docker run -p 8080:8080 ghcr.io/veridactus/veridactus:latest
```

Then follow the [Quickstart Guide](https://docs.veridactus.ai/quickstart).

### Is VERIDACTUS production-ready?

VERIDACTUS is at **v0.2.1** (Working Draft). The L0 hash chain, L2A Merkle sampling, and L2B ZK proofs are production-grade. TEE attestation (L1) is in type definitions. See the [specification status](https://docs.veridactus.ai/specification/latest) for details.

### Can I use VERIDACTUS commercially?

Yes. The protocol specification is licensed under **Apache License 2.0**. Implementations may be proprietary or open source, but must pass the conformance suite to claim `VERIDACTUS‑Compatible` status.

### How do I become a contributor?

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines. All contributors must follow the [Code of Conduct](CODE_OF_CONDUCT.md) and sign off commits with DCO.
