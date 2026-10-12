# Hermes as a restricted operating-system service

This is where 0xPhone becomes more than another privacy-focused Android fork.

The phone is the user's control surface. Compute-intensive tasks can run elsewhere,
and the phone must remain useful when every remote worker is offline.

## Task routing policy (default order)

1. **On-device** when the task is small, the local model is capable enough, and local
   execution meets privacy/latency requirements.
2. **Delegate** to an authorized local machine or free model.
3. **Approved remote worker** if local resources are insufficient.
4. **Paid model fallback** only when authorized, within the configured budget, and
   when the task's data classification permits external processing.

**Never** silently send private messages, wallet data, authentication tokens, or
confidential project files to an external model.

## Reliable delegation protocol

Every job has:

- a unique job ID and authenticated requester;
- a declared task type, data classification, and requested capabilities;
- an explicit resource budget and execution deadline;
- a durable status record: `queued · running · awaiting_approval · completed · failed · cancelled`;
- heartbeat, timeout policy, and safe retry mechanism;
- a result artifact, execution log, and independent validation where appropriate.

**Do not** rely on unrestricted agent-to-agent chat as the primary delegation protocol.
Use structured jobs and narrow worker APIs. A worker must never be able to grant itself
extra permissions by editing its task description.

## First implementation

Expose a single mobile interface to the existing Hermes infrastructure through a small
**gateway adapter**. Do not rewrite Hermes or build a new distributed agent framework
until the prototype demonstrates a real limitation in the existing tools.
