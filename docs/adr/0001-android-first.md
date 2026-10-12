# ADR 0001: Android-first foundation with parallel Linux research

- Status: proposed
- Date: 2026-10-13

## Decision
Build the first usable product on a hardened AOSP base (Option A). Run a Linux-first
edition (Ubuntu Touch-inspired) as a separate research track.

## Rationale
Android offers the only practical path to modern hardware support (camera, modem,
notifications, apps) in a reasonable timeframe. Linux-first maximizes control but
turns hardware enablement and app availability into major engineering projects.
Merging both stacks into one release is rejected as infeasible for a small team.

## Consequences
- No conventional Linux desktop as the native phone OS; convergence arrives via the
  isolated Linux workspace and later desktop mode.
- Security properties must be re-validated on every modification; forking does not
  inherit GrapheneOS's guarantees.
