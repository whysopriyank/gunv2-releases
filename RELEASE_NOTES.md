# v0.1.0-alpha.1 release notes

Status: **GO — independent FIN18-7 final review accepted by the main executor for the approved bounded public alpha**.

This release provides a static Linux x86_64 relay, a macOS arm64 relay with optional TLS, a TypeScript ESM bundle with declarations, browser WASM bindings and a CPython 3.12 Linux x86_64 extension. Tested runtime targets in the candidate evidence are Bun 1.4.0, headless Chrome and Ubuntu 24.04 for Python. Source and Git history remain private; the public destination contains documentation and artifacts only.

This connected-client alpha supports greenfield evaluation with public-write namespaces. SDK PUT success is socket-send success, not an accepted or durable save. There is no durable offline outbox or SDK signing/certificate API. Retained data has a 1,000,000-entry upper ceiling, subject to lower configured namespace and storage quotas.

The WebSocket listener binds 0.0.0.0; restrict its exposure. The example metrics listener is loopback and unauthenticated. Linux TLS termination is external. macOS certificate/key rotation requires a restart; the binary is not Developer ID signed or notarized.

The original 329-file FIN-17 packet and 81-file Linux bigbeast READY addendum are accepted. Linux smoke, load, recovery and the actual 55-minute qualification run are accepted by independent retained-stage revalidation. A separate addendum corrects the comparison of the bounded 4,096-entry reader pool; it does not change candidate source, ZIPs or workload.

Qualification checks bounded sampled reads and exact LogStore persisted-state reopens, not an individual readback of every successful ACK. Apply p95 is UNEXERCISED. The six-hour endurance stage reports PASS and finished at 23:48:38 UTC on 2 October 2026 (05:18:38 IST on 3 October): 85,735 successful memory ACKs and 85,734 successful log ACKs, 21,409/21,409 sampled-read hits for memory and 21,410/21,410 for log, zero read/load errors or observer gaps, and two full persisted reopens with identical state hashes. Sampled-read averages were 0.21 ms for both stores; maxima were 3.1 ms for memory and 3.6 ms for log. Peak RSS was 59,724 KiB for memory and 52,652 KiB for log. These are sampled-read measurements, not apply latency or maximum-throughput claims.

The requested duration was 21,600 seconds. Observed runner lifetime was 21,613.573 seconds including startup and cleanup; measured loader-active duration is not claimed. The final packet is captured and immutable inputs remain unchanged. Independent FIN18-7 final review returned GO and root FIN-18 GO acceptance is recorded. See qualification-manifest.json and qualification-manifest.md. Verify ZIPs against checksums.sha256 before use.
