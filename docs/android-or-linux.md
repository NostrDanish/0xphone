# The biggest technical decision: Android or Linux?

This decision determines whether the project is achievable.

## Option A — Hardened Android foundation (recommended start)

Start from AOSP; study or selectively reuse relevant GrapheneOS-compatible security
improvements; provide an Android-compatible app environment plus a carefully isolated
Linux/Hermes layer.

**Advantages:** the most practical route to a usable phone with modern hardware
support — cameras, cellular, notifications, Android apps.

**Trade-off:** no conventional Linux desktop as the *native* phone OS. GrapheneOS
security properties cannot be assumed to survive arbitrary modifications; they must
be maintained and tested.

## Option B — Linux-first phone

Start from Ubuntu Touch (or another mobile Linux base), a custom Omarchy-inspired
interface, and Hermes as a privileged-but-restricted service.

**Advantages:** native Linux userland, deep customization, natural desktop-convergence path.

**Trade-off:** hardware enablement, modem integration, camera quality, app
availability, and long-term security maintenance can each become major engineering
projects. Ubuntu Touch's device-specific image architecture illustrates how much
hardware integration matters.

## Recommendation

**Option A for the first usable product**, with a Linux-native alternative as a
**parallel research track** — not an attempt to merge two incompatible kernels and
application stacks into one release.

## A note on GrapheneOS

GrapheneOS is an independent security-focused project. A production fork must respect
its licensing, upstream development boundaries, and security standards. Copying its
source does not automatically preserve its protections.
