# gunv2 v0.1.0-alpha.1

This public repository contains release documentation and binary/SDK artifacts only. The implementation source and its Git history remain private. Project artifacts are licensed MIT OR Apache-2.0; each ZIP carries the project licenses and third-party notices.

**Draft release preparation: NO GO.** The source candidate and five ZIP identities remain unchanged. The original FIN-17 packet and Linux bigbeast READY addendum are accepted. Linux smoke, load, recovery and the actual 55-minute qualification stage are accepted after independent retained-stage revalidation. Mandatory six-hour endurance started at 17:47:09 UTC on 2 October 2026 and is running; its earliest duration boundary is 05:17 IST on 3 October, followed by completion checks and independent final review. No public release is claimed by this draft.

Connected-client alpha for greenfield evaluation. When the alpha is published, download the ZIP for your platform from this repository’s Releases page. There are no npm or PyPI releases.

| ZIP | Contents / supported environment |
|---|---|
| `gunv2-relay-linux-x86_64.zip` | Static Linux x86_64 relay, default features; TLS termination is external |
| `gunv2-relay-macos-arm64-tls.zip` | macOS arm64 relay with optional TLS |
| `gunv2-ts-client.zip` | ESM bundle and TypeScript declarations; tested with Bun 1.4.0 |
| `gunv2-wasm.zip` | Browser WebAssembly and JS bindings; tested in headless Chrome |
| `gunv2-python-linux-x86_64-cp312.zip` | CPython 3.12 Linux x86_64 extension; tested on Ubuntu 24.04 |

Each ZIP includes project licenses and dependency notices. Verify ZIPs with `checksums.sha256`. Check the release’s qualification manifest for the exact tested hashes and limits.

## Start a relay

Unzip the relay package, then run inside its directory:

```sh
cp relay.toml.example relay.toml
install -d -m 700 ./data
chmod +x ./gunv2-relay
./gunv2-relay --config ./relay.toml
```

Readiness: `curl http://127.0.0.1:18422/metrics` must show `gunv2_ready 1`. Connect clients to `ws://127.0.0.1:18421`. Stop with Ctrl-C or SIGTERM and wait for the process to exit.

The WebSocket listener binds `0.0.0.0`. Evaluate on a private network or use a host firewall/reverse proxy. Metrics are unauthenticated and the example binds them to `127.0.0.1`.

The example uses a 64 MiB persistent log, 100,000 entries per namespace and `sync_every = 1`. The relay’s accepted PUT ACK has a zero-write crash-loss window with this setting. SDK PUT calls do not expose that ACK guarantee.

## TypeScript / JavaScript

Unzip `gunv2-ts-client.zip`. Save this example beside the extracted `gunv2-ts-client` directory and run it with Bun 1.4.0:

```js
import { GunClient } from './gunv2-ts-client/index.js';
const client = new GunClient('ws://127.0.0.1:18421');
await client.connect();
try {
  await client.get('chat').put({ greeting: 'hello' });
  console.log(await client.get('chat').get('greeting').once());
} finally {
  client.close();
}
```

The bundle requires global `WebSocket` and `Promise.withResolvers`. TypeScript declarations are beside the bundle. Live subscriptions retain their intent across reconnects; pending reads fail when their connection closes.

## Python

Use Linux x86_64 with CPython 3.12. Unzip the Python package and add its directory to `PYTHONPATH`:

```sh
PYTHONPATH=./gunv2-python-linux-x86_64-cp312 python3.12 - <<'PYTHON'
import gunv2
client = gunv2.connect('ws://127.0.0.1:18421', 'chat')
client.put('chat', 'greeting', 'hello')
print(client.get('chat', 'greeting'))
PYTHON
```

## Browser WebAssembly

Serve the unzipped WASM directory over HTTP(S) with your application. Its JS and `.wasm` files must remain together. In a browser module:

```js
import init, { WasmClient } from './gunv2-wasm/gunv2_wasm.js';
await init();
const client = WasmClient.connect('ws://127.0.0.1:18421', 'chat');
client.on_update(entries => console.log(entries));
```

Construction starts the socket asynchronously. Writes require an open socket and can throw while connecting. Use `wss` for an HTTPS page. The generated declarations describe the exported API.

## Alpha limits

Qualification uses bounded sampled reads with a 4,096-entry reader pool and exact persisted-state reopen checks; it does not claim that every successful ACK was individually read back. Apply p95 is UNEXERCISED. Endurance reopen checks remain pending until completion.

Use public-write namespaces with these SDKs. PUT success means sent to the socket; it does not confirm acceptance, commitment or durability. Negative PUT ACKs are not surfaced as SDK write errors. Applications requiring confirmed saves are outside this alpha scope. There is no durable offline outbox or SDK signing/certificate API.

Greenfield only; no gun.js data migration. The retained-data ceiling is 1,000,000 entries, subject to lower configured namespace/storage quotas. Qualification uses a bounded profile and does not claim maximum throughput, Pi/OpenWrt performance or production readiness. Unsupported: Windows, other architectures, native Node bindings, bounded blackhole detection, hot TLS reload and private-CA relay-to-relay TLS.

A mesh requires distinct signing seeds, exact peer keys and matching `auth.trusted_relays` before startup; the example’s mesh sections are commented placeholders. Relay mesh TLS trusts public webpki roots. macOS TLS certificate/key rotation requires restart. The Linux package requires a TLS terminator when encryption is needed. For the macOS TLS package, set both `server.tls_cert_path` and `server.tls_key_path` to your own PEM files, restrict key permissions, and use `wss`. It has no Developer ID signature or notarization; macOS may require explicit local authorization to launch a downloaded binary.

## Backup and recovery

Stop the relay and preserve an untouched copy of `data/gunv2.log`. Copy only after the process exits. Restore into a separate data directory with the relay stopped, point the configuration there, start, verify readiness and read known application records. Preserve the original until validation finishes. An interior-corrupt log refuses startup; preserve it and restore a known-good offline copy. Do not edit bytes to force startup.

When readiness remains zero, recovery-required closes occur, quotas reject writes or resource use exceeds your evaluation limits, stop load and preserve the log/configuration before diagnosing. Publish sanitized reproduction details through this repository’s Issues page; never upload signing seeds, private keys or user data.

## Licenses

Project artifacts are `MIT OR Apache-2.0`. See `LICENSE-MIT`, `LICENSE-APACHE` and `THIRD_PARTY_NOTICES.md`. Dependency inventories describe the packaged normal/build graphs. Tooling-only inventory entries are distinguished from bundled runtime dependencies.
