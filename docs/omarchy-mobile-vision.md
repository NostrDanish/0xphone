# OmarchyMobile: the flexibility thesis

The core product insight: **0xPhone should be as flexible as Omarchy — basically
OmarchyMobile.** Omarchy won people over because it turns any reasonable machine into
an opinionated-but-hackable environment in minutes. 0xPhone should do the same for
phones: not "one blessed device image," but a system that *adapts itself* to whatever
hardware it lands on.

## What "as flexible as Omarchy" means on a phone

- **Opinionated defaults, total hackability** — like Omarchy, ship a coherent UX out of
  the box, but every layer is documented, overridable, and scriptable.
- **Config over fork** — users tailor 0xPhone with config and packages, not by
  maintaining private OS forks.
- **One interface, any hardware** — the same Hermes-driven experience whether the
  device is a Pixel, a Fairphone, a Xiaomi, or a Linux-first device.

## "Any phone should be able to get it"

Universal support is the goal, but honesty about the tiers matters:

| Tier | Devices | What you get |
|---|---|---|
| **Tier 1 — Native** | Reference devices (Pixel-class, unlockable bootloader) | Full 0xPhone OS: verified boot, signed updates, full security model |
| **Tier 2 — Ported** | Any unlockable Android device | AI-assisted port (below); security guarantees depend on what the hardware/bootloader allows |
| **Tier 3 — Companion** | Locked/stock phones | The 0xPhone companion app + Hermes layer on stock Android: task delegation, local-first AI, privacy controls within app sandbox limits |

Tier 3 is the Omarchy-like move: **the experience works everywhere on day one**, and
the OS deepens it where the hardware cooperates.

## AI engines as the porting engine

"The AI engines will make it work somehow" — concretely, that means an
**AI-assisted device adaptation pipeline**:

1. **Device probe** — read chipset, kernel version, vendor blobs, partition layout,
   bootloader state, sensors, modem stack.
2. **Match & generate** — Hermes workers compare the probe against a device-knowledge
   base (LineageOS / postmarketOS / Ubuntu Touch porting data, GSIs, device trees) and
   generate a port plan: device tree patches, kernel config, HAL shims, Treble/GSI
   strategy.
3. **Build & test loop** — build on the Omarchy workstation/build runner, flash on a
   sacrificial device, run automated bring-up tests (boot, radio, camera, sensors),
   feed failures back to the AI for the next iteration.
4. **Human gate** — no AI-generated port ships unsigned or unreviewed. The AI
   *proposes*; maintainers approve. Same rule as everything else: agents request,
   the project decides.

Project Treble GSIs are the pragmatic bridge: on any Treble-compliant phone, a generic
system image can boot without per-device kernels — the AI pipeline then fills the
gaps (vendor quirks, HAL shims, config) per device.

## Consequences for the roadmap

- Phase 1 (companion app) is the universal tier — works on any Android phone.
- Phase 2+ targets one Tier-1 reference device, but the **device-knowledge base and
  porting pipeline get built as first-class components**, not afterthoughts.
- The Linux-first track doubles as the "any Linux phone" tier.
