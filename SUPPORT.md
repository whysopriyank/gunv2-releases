# Alpha support

Use this repository’s [Issues](https://github.com/whysopriyank/gunv2-releases/issues) for sanitized reproduction details. Include the release tag, ZIP filename and SHA-256, platform/runtime, expected behavior and observed error. Remove user data, signing seeds, private keys, credentials, private source paths and raw internal logs before posting.

This is a connected-client, greenfield evaluation alpha. SDK PUT success means sent to the socket, not relay acceptance, commitment or durability; negative PUT ACKs are not surfaced as SDK write errors. Confirmed saves, a durable offline outbox and SDK signing/certificate APIs are outside scope.

Stop load and preserve the configuration and storage log locally when readiness stays zero, recovery-required closes occur, quotas reject writes or resource usage exceeds your evaluation limits. Back up only after the relay exits. Preserve the original log and recover using a known-good offline copy; do not edit corrupt bytes to force startup.

The WebSocket listener binds all interfaces; restrict exposure with a private network, firewall or reverse proxy. Keep unauthenticated metrics on loopback. The macOS TLS package needs your own certificate/key and a restart for rotation. Linux encryption needs an external TLS terminator.

Source code remains private. This repository publishes documentation and artifacts; there are no npm or PyPI releases. No production readiness, maximum throughput, Pi/OpenWrt performance or unsupported-platform guarantees are made.
