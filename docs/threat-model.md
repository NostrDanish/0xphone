# Threat model & security architecture (draft)

## Assets

- User messages, files, photos, contacts
- Crypto wallet keys and signing operations (Bitcoin, Monero, Nostr keys)
- OS signing keys, OTA keys, verified-boot keys
- Agent credentials and worker authorization tokens
- Microphone, camera, location, sensors

## Trust boundaries

| Boundary | Rule |
|---|---|
| App ↔ OS | Standard sandboxing; per-app network controls; visible permission prompts |
| Hermes ↔ OS | Hermes **requests**; the OS decides. Narrow, auditable, scoped capabilities only |
| Hermes ↔ keys | Agents never touch private keys or signing operations; transactions require explicit user approval |
| Phone ↔ workers | Authenticated, capability-checked jobs through the secure task gateway |
| Linux userland ↔ Android | Linux apps do not inherit Android privileges; all shared access is mediated |
| External models ↔ data | Only approved payloads, per data classification; visible routing decision |

## Data classification

- **public** — may go anywhere
- **internal** — local devices and authorized workers only
- **confidential** — on-device or explicitly approved endpoints only
- **secret** (keys, tokens, wallet data, private messages) — never leaves the secure enclave / explicit user flow

## Agent permission system

- Scoped, revocable credentials per worker and per task type
- Budget enforcement for paid model calls (deny when disabled or exhausted)
- Durable audit log of every privileged action and routing decision
- Two-person review for security-sensitive OS changes

## Non-goals (initially)

- Defending against a compromised baseband beyond standard isolation
- Protecting rooted/dev-unlocked devices in production configuration
