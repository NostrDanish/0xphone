# Linux convergence design

Android remains the trusted host. Linux applications must not automatically inherit
the phone's system privileges.

## Three modes of operation

### Mobile mode
Normal phone calls, notifications, Android applications, local inference, agent interface.

### Linux workspace mode
A sandboxed Linux userland with shell, Git, compilers, and dev tools. Access to shared
files, networking, USB, and hardware is explicitly mediated.

### Desktop mode (later release)
External display, keyboard, mouse, and an Omarchy-inspired desktop interface. The
initial version can use a dedicated desktop app or remote-desktop session while native
display integration is developed.

## Implementation order

1. Start with an isolated Linux userland that does **not** require custom kernel changes.
2. Evaluate stronger VM isolation on compatible hardware.
3. Add hardware access and desktop integration only after isolation boundaries are tested.
4. Keep the Linux-first OS as a **separate experimental build** — not an alternate boot
   mode sharing the Android system's trust assumptions.
