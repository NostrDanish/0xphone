# Contributing

0xPhone is in Phase 0. The most useful contributions right now:

1. Review the threat model and permission architecture (`docs/threat-model.md`).
2. Help with the licensing/SBOM inventory (`docs/licensing.md`).
3. Prototype feedback on the MVP spec (`docs/mvp.md`).
4. Device feasibility notes for candidate target hardware.

Rules of the road:

- Security-sensitive changes require two-person review.
- No agent-facing code may request broader capabilities than its task declaration.
- Keep the OS fork and Linux-first experiments out of the companion app's critical path.
