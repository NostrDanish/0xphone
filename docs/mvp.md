# MVP definition & acceptance tests

The MVP is an **Android application** integrated with the distributed agent network.
It does not need to replace Android's boot image to deliver meaningful value.

## Acceptance checklist

- [ ] **Core UX** — user can submit a task, see its status, cancel it, inspect the result.
- [ ] **Permissions** — a worker cannot exceed the capabilities granted for its task.
- [ ] **Privacy** — external model requests disclose only approved payloads, with a visible routing decision.
- [ ] **Cost control** — paid model calls are denied when disabled or when the budget is exhausted.
- [ ] **Reliability** — a disconnected worker can reconnect without duplicating a non-idempotent action.
- [ ] **Security** — agent credentials are scoped and revocable; signing keys are not exposed to agents.
- [ ] **Linux** — the prototype can execute a harmless test task in an isolated Linux environment.
- [ ] **Recovery** — a documented rollback/recovery procedure works on the test device.

These are proposed acceptance tests, not results from tests already performed. A full
OS release requires additional device-specific validation: calls, emergency
functionality, encryption, OTA updates, verified boot, app compatibility, and
security regression testing.
