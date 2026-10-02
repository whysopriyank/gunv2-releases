# v0.1.0-alpha.1 draft release notes

Status: **NO GO — qualification pending**. This text is prepared for the final release decision and does not announce a completed qualification or publication.

The planned release provides a static Linux x86_64 relay, a macOS arm64 relay with optional TLS, a TypeScript ESM bundle with declarations, browser WASM bindings and a CPython 3.12 Linux x86_64 extension. Tested runtime targets in the candidate evidence are Bun 1.4.0, headless Chrome and Ubuntu 24.04 for Python. Source and Git history remain private; the public destination contains documentation and artifacts only.

This connected-client alpha supports greenfield evaluation with public-write namespaces. SDK PUT success is socket-send success, not an accepted or durable save. There is no durable offline outbox or SDK signing/certificate API. Retained data has a 1,000,000-entry upper ceiling, subject to lower configured namespace and storage quotas.

The WebSocket listener binds 0.0.0.0; restrict its exposure. The example metrics listener is loopback and unauthenticated. Linux TLS termination is external. macOS certificate/key rotation requires a restart; the binary is not Developer ID signed or notarized.

Before publication, complete and seal all mandatory ordered qualification stages, the frozen evidence packet/addendum and independent final review. The intended final qualification host is Linux bigbeast; accepted macOS cells must retain their actual platform identity. See qualification-manifest.json and qualification-manifest.md for pending gates. Verify downloaded ZIPs against checksums.sha256 after the final GO decision.
