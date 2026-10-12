# 0xPhone

> One device · Three execution environments · One AI interface.

**0xPhone** is a concept (working name) for an AI-native, privacy-first mobile platform:
**Omarchy Mobile**-style experience, **GrapheneOS-grade security ambitions**, and a
**Ubuntu Touch-inspired** look and feel — without pretending that forking any of those
projects automatically transfers their properties.

```
┌────────────────────────── 0xPhone ──────────────────────────┐
│  Secure Mobile Core                                          │
│  Verified boot · Hardware-backed keys · App sandboxing ·     │
│  Permission enforcement                                      │
├────────────────┬────────────────┬───────────────────────────┤
│  Android apps  │  Linux         │  Hermes                   │
│  (compat +     │  (CLI, dev,    │  (AI agents +             │
│   sandboxing)  │   tools)       │   automation)             │
└────────────────┴────────────────┴───────────────────────────┘
        Distributed personal computing
        Phone ↔ Omarchy PC ↔ Umbrel ↔ RackNerd VPS ↔ workers
```

**The one critical rule:** Hermes can *request* actions, but the operating system
decides what it is allowed to do. No unrestricted AI root access — ever.

Your phone becomes the controller for your personal computing network, rather than
having to perform every expensive AI task locally.

## Status

**Phase 0 — Foundation & feasibility.** This repo currently contains the project
blueprint, architecture, threat model draft, governance, and roadmap. No OS code yet.
See [`docs/roadmap.md`](docs/roadmap.md).

## Docs

| Doc | Contents |
|---|---|
| [docs/architecture.md](docs/architecture.md) | System architecture, execution environments, distributed compute topology |
| [docs/android-or-linux.md](docs/android-or-linux.md) | The foundational decision: hardened Android (A) vs Linux-first (B) |
| [docs/hermes-service.md](docs/hermes-service.md) | Hermes as a restricted OS service; task routing & delegation protocol |
| [docs/linux-convergence.md](docs/linux-convergence.md) | Mobile / Linux workspace / desktop modes |
| [docs/threat-model.md](docs/threat-model.md) | Security architecture, permission model, data classification |
| [docs/mvp.md](docs/mvp.md) | MVP definition + acceptance-test checklist |
| [docs/roadmap.md](docs/roadmap.md) | Phased roadmap + first-30-days plan + build infra requirements |
| [docs/licensing.md](docs/licensing.md) | Licensing & upstream-relationship policy (AOSP, GrapheneOS, Omarchy, Ubuntu Touch…) |
| [GOVERNANCE.md](GOVERNANCE.md) | Governance, review rules, release process |
| [SECURITY.md](SECURITY.md) | Vulnerability disclosure & security support policy |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute |

## The pitch in one paragraph

The strongest version isn't simply GrapheneOS + Omarchy + Ubuntu Touch. It's a secure
mobile platform with Android compatibility, Linux capabilities, and a distributed AI
agent system built into the user experience. The first product is a working,
permission-controlled mobile interface that coordinates your personal compute network —
local-first AI, safe delegation, explicit consent — before we commit to maintaining an
entire operating-system fork.

## Non-negotiables (day one)

- **Security updates first** — a fork is a long-term maintenance commitment, not a one-time build.
- **Free and local models first** — paid AI is an opt-in fallback with explicit spending limits.
- **No unrestricted AI root access** — agents use narrow, auditable tools with scoped permissions.
- **Open, reproducible builds** — source, build instructions, release signatures, advisories.
- **No forced cloud account** — the basic phone works without our servers.
- **One coherent UX** — mobile-first by default, power-user environment on request.

## Naming & affiliation

0xPhone is an independent project. It is **not** an official GrapheneOS, Omarchy, or
Ubuntu Touch product. Those names are used only to describe inspiration and potential
upstream sources; see [docs/licensing.md](docs/licensing.md).
