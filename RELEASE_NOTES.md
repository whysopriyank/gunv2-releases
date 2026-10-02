# v0.1.0-alpha.1 draft release notes

Status: **NO GO — mandatory six-hour endurance and independent final review pending**. This draft does not announce completed qualification or publication.

The planned release provides a static Linux x86_64 relay, a macOS arm64 relay with optional TLS, a TypeScript ESM bundle with declarations, browser WASM bindings and a CPython 3.12 Linux x86_64 extension. Tested runtime targets in the candidate evidence are Bun 1.4.0, headless Chrome and Ubuntu 24.04 for Python. Source and Git history remain private; the public destination contains documentation and artifacts only.

This connected-client alpha supports greenfield evaluation with public-write namespaces. SDK PUT success is socket-send success, not an accepted or durable save. There is no durable offline outbox or SDK signing/certificate API. Retained data has a 1,000,000-entry upper ceiling, subject to lower configured namespace and storage quotas.

The WebSocket listener binds 0.0.0.0; restrict its exposure. The example metrics listener is loopback and unauthenticated. Linux TLS termination is external. macOS certificate/key rotation requires a restart; the binary is not Developer ID signed or notarized.

The original 329-file FIN-17 packet and 81-file Linux bigbeast READY addendum are accepted. Linux smoke, load, recovery and the actual 55-minute qualification run are accepted by independent retained-stage revalidation. A separate addendum corrects the comparison of the bounded 4,096-entry reader pool; it does not change candidate source, ZIPs or workload.

Qualification checks bounded sampled reads and exact persisted-state reopens, not an individual readback of every successful ACK. Apply p95 is UNEXERCISED. The mandatory six-hour endurance stage started at 17:47:09 UTC on 2 October 2026 and is running. The earliest duration boundary is 05:17 IST on 3 October; completion assertions, final evidence sealing and independent final review must still pass before GO. See qualification-manifest.json and qualification-manifest.md. Verify ZIPs against checksums.sha256 after final GO.
