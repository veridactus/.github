# Contributing to VERIDACTUS

Welcome! VERIDACTUS is an open-governance protocol, and we welcome contributions of all kinds — from specification improvements to conformance test vectors.

## Code of Conduct

All participants are expected to adhere to our [Code of Conduct](CODE_OF_CONDUCT.md). Be respectful, constructive, and inclusive.

## How to Contribute

### Reporting Issues

Found a bug, inconsistency, or unclear specification text?
[Open an issue](https://github.com/veridactus/docs/issues/new/choose) using the appropriate template.

### Proposing Changes (RFC Process)

Substantive protocol changes follow the **RFC (Request for Comments)** workflow:

1. **Draft** — Create a new file in `rfcs/` using the RFC template.
2. **Submit** — Open a Pull Request with your RFC.
3. **Review** — The Technical Steering Committee (TSC) performs initial scope review.
4. **Public Comment** — 14–30 day community review period.
5. **Iterate** — Address feedback and refine the proposal.
6. **Final Vote** — TSC holds a final vote (see `GOVERNANCE.md` for thresholds).
7. **Merge** — Approved RFCs are merged and scheduled for the next version.

### Pull Request Requirements

- **DCO Sign-off**: All commits must include a `Signed-off-by:` line (`git commit -s`).
- **One PR per logical change**: Separate specification fixes from documentation edits.
- **Link related issues**: Use `Closes #NN` or `Refs #NN` in the PR description.
- **Pass CI**: The `validate.yml` workflow must succeed.

## Development Environment

```bash
# Clone and set up the docs repository
git clone https://github.com/veridactus/docs.git
cd docs
npm install
npm run dev       # Start local documentation server
npm run validate  # Run all validations
```

## Recognition

All contributors are acknowledged in our [GitHub contributor graph](https://github.com/veridactus/docs/graphs/contributors). Significant contributions may be recognized in specification front matter.

## Questions?

- **Discussions**: [github.com/veridactus/docs/discussions](https://github.com/veridactus/docs/discussions)
- **TSC Contact**: [tsc@veridactus.ai](mailto:tsc@veridactus.ai)
