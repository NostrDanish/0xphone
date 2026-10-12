# Roadmap

Proposed sequence for a small community team. Durations are estimates; later
milestones depend on passing earlier security and device-support gates.

## Phase 0 — Foundation & feasibility (weeks 0–4)
**Deliverable: architecture baseline**
- Establish GitHub org, repo layout, governance
- Choose target device; verify bootloader, firmware, recovery constraints
- Write threat model, permission model, data-classification policy
- Inventory upstream code, licenses, build requirements
- Prototype the agent gateway against a test Hermes worker

**Exit gate:** approved architecture, reproducible dev setup, documented device feasibility assessment.

## Phase 1 — AI phone companion (months 1–3)
**Deliverable: working Android prototype**
- Launcher or companion interface
- Secure task gateway connection
- Worker selection, job progress, approvals, audit history
- Local-first model routing; paid-model budget controls
- Disconnection, cancellation, safe-retry testing

**Exit gate:** a daily-usable app can delegate and review tasks without OS-level modifications.

## Phase 2 — Android OS development (months 3–6)
**Deliverable: development image**
- Clean AOSP build and device configuration
- 0xPhone system interface, implemented and reviewed
- Only minimal system hooks genuinely required
- Project-controlled build and update infrastructure
- Verified boot, app isolation, update, and recovery testing

**Exit gate:** repeatable dev builds, working update test, documented security regression suite.

## Phase 3 — Linux workspace (months 6–9)
**Deliverable: isolated development mode**
- Packaged Linux userland and toolchain
- Scoped file sharing and network policies
- Approved build/research tasks to Hermes workers
- Memory, thermal, battery, isolation benchmarks
- Desktop-mode experiments begin

**Exit gate:** Linux tools work reliably without unrestricted access to Android's privileged services.

## Phase 4 — Community alpha (months 9–12+)
**Deliverable: controlled external testing**
- Documented builds; reproducible-build initiative
- Independent security review of custom privileged components
- Signed release and rollback/recovery procedures
- App compatibility and monthly security maintenance testing
- Linux-first track continues on a separate supported device

**Exit gate:** the team can maintain the release, respond to vulnerabilities, recover devices safely.

> A production-grade, independently hardened OS may take substantially longer than a
> year. No public stable release date until device support, security maintenance
> staffing, and the release process are demonstrated.

## Build infrastructure requirements

Per current AOSP documentation: 64-bit Linux host, **≥64 GB RAM**, **~400 GB free
disk** for source and build output. Small VPSs act as coordinators/workers, not the
primary build machine.

## First 30 days — concrete work plan

- **Week 1:** public project skeleton, threat model, licensing inventory, ADRs.
- **Week 2:** Android dev environment; validate target device; gateway API prototype against a simulated worker.
- **Week 3:** first Android interface — task submission, permission prompts, job status.
- **Week 4:** integrate one real Hermes worker; test disconnection/retries; publish first dev milestone with known limitations.

Keep the OS fork and Linux-first experiments out of the critical path until the
mobile companion demonstrates a useful, secure workflow.

## Team roles

| Role | Responsibility |
|---|---|
| Project lead / architect | Scope, architecture decisions, integration |
| Android platform maintainer | AOSP builds, device support, upstream patches |
| Security lead | Threat model, privileged code review, vulnerability response |
| Android UX developer | Launcher, system interface, UX |
| AI integration developer | Hermes adapter, policy engine, model routing |
| Infrastructure maintainer | Build runners, signing pipeline, release automation |
| Linux porting contributors | Linux workspace, Ubuntu Touch research, hardware enablement |

One person may cover several roles initially — but security-sensitive releases get
independent review, never only the author.
