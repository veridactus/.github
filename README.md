# .github

**VERIDACTUS** Organization — Community health files, profile, and default governance templates.

This is a [special GitHub repository](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) that provides:

| Purpose | Description |
|:--------|:------------|
| **Organization Profile** | [`profile/README.md`](profile/README.md) — rendered on [github.com/veridactus](https://github.com/veridactus) |
| **Default Community Health Files** | `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`, `SUPPORT.md` — applied to all repos that lack their own copies |
| **Issue & PR Templates** | Standard templates for bug reports, RFCs, and pull requests |
| **Brand Assets** | Official VERIDACTUS logo SVGs in `assets/` |

## Structure

```
.github/
├── README.md                      # You are here
├── profile/
│   └── README.md                  # Organization landing page
├── assets/
│   ├── logo-light.svg             # Light-mode logo
│   ├── logo-dark.svg              # Dark-mode logo
│   └── favicon.svg                # Favicon
├── CODE_OF_CONDUCT.md             # Contributor Covenant v2.0
├── CONTRIBUTING.md                # Contribution guidelines
├── SECURITY.md                    # Vulnerability reporting policy
├── SUPPORT.md                     # Where to get help
├── CODEOWNERS                     # Default code ownership → @veridactus/tsc
├── FUNDING.yml                    # Sponsor configuration
├── ISSUE_TEMPLATE/                # Default issue templates
└── PULL_REQUEST_TEMPLATE.md       # Default PR template
```

## Related Repositories

| Repository | Purpose |
|:-----------|:--------|
| [veridactus/veridactus](https://github.com/veridactus/veridactus) | Core implementation — Rust data plane, Go control plane, React UI |
| [veridactus/docs](https://github.com/veridactus/docs) | Protocol specification v0.2.1, JSON schemas, conformance suite, RFCs |

## License

Apache License 2.0 — Copyright 2026 The VERIDACTUS Authors.
