# 0xPhone Architecture

## Concept

One device, three execution environments, one AI interface:

1. **Secure Mobile Core** — verified boot, hardware-backed keys, app sandboxing, permission enforcement.
2. **Android apps** — compatibility layer with sandboxing.
3. **Linux** — CLI, development tools, isolated userland.

Plus **Hermes**, the AI agent and automation layer, integrated as a
*privileged-but-restricted* OS service.

## The critical rule

> Hermes can request actions, but the operating system decides what it is allowed to do.

Agents never hold signing keys, wallet keys, or raw message stores. Every privileged
action passes a policy engine with scoped, auditable capabilities.

## Differentiating features

- **AI-native OS** — natural-language commands, research, coding, automation, task
  delegation. Small local models first; authorized remote workers for heavy jobs;
  paid APIs only as an authorized, budget-capped fallback.
- **Privacy as an enforceable system property** — per-app network controls, separate
  work/personal profiles, isolated AI tools, local-first storage, encrypted backups,
  visible permission prompts. No agent silently gets access to messages, files,
  camera, or crypto keys.
- **Phone-to-desktop convergence** — dock to screen/keyboard/mouse for a full Linux
  dev environment; undock back to mobile. Long-term, hardware-dependent.
- **Private personal server network** — dispatch a build to the Omarchy PC, a research
  job to the RackNerd VPS, a home-server task to Umbrel. One interface, explicit
  authorization per worker and per action.
- **Native privacy & crypto toolkit** — Nostr identity and relay tools, Bitcoin and
  Monero wallet integrations, local signing, self-hosted services. Private keys stay
  isolated from AI agents; transactions require explicit approval.

## Distributed compute topology

```
            ┌────────────────────────────┐
            │           0xPhone          │
            │ UI · Consent · Local models│
            │      · Task submission     │
            └─────────────┬──────────────┘
                          │
            ┌─────────────▼──────────────┐
            │     Secure task gateway    │
            │ Auth · Capability checks · │
            │ Job queue · Budget enforce │
            └──┬───────┬───────┬─────┬───┘
        ┌──────▼─┐ ┌───▼────┐ ┌▼─────┐ ┌▼───────────────┐
        │Omarchy │ │RackNerd│ │Umbrel│ │Optional workers│
        │PC      │ │VPS     │ │      │ │(specialist VPS,│
        │commander│ │always- │ │home  │ │ paid model APIs│
        │+ heavy │ │on coord│ │infra │ │                │
        │local AI│ │        │ │      │ │                │
        └────────┘ └────────┘ └──────┘ └────────────────┘
```

- **Omarchy PC** — main commander and heavy local inference.
- **RackNerd VPS** — always-on coordinator and remote jobs.
- **Umbrel** — home infrastructure and private services.
- **Optional workers** — specialist VPSs and paid model APIs.

The phone is a trusted endpoint — and remains useful when every remote worker is offline.

## Build infrastructure note

Full OS builds are a significant project: current AOSP docs specify a 64-bit Linux
host, **≥64 GB RAM** and **~400 GB free disk**. A small VPS (e.g. 8 GB) is a
coordinator/worker, **not** the primary build machine. Use a workstation that meets
the requirements or a dedicated build runner; the VPS handles CI orchestration,
metadata, issue tracking, and lightweight tests.
