# Alpha qualification manifest

**GO for the approved bounded connected-client public alpha.** Independent FIN18-7 final review returned GO and the main executor accepts the complete ordered qualification. Production readiness is not claimed.

Private source candidate: `099cf04bfbfe02f93336303b80c26cf0df2f2606`. Public destination: documentation and artifacts only at https://github.com/whysopriyank/gunv2-releases. No private source or Git history is included. The five ZIP identities remain unchanged.

The original 329-file FIN-17 packet and 81-file Linux bigbeast READY addendum are accepted. Exact-candidate CI passes all eight jobs; selected nightly Miri and fuzz jobs pass. Platform-specific macOS evidence retains its actual platform identity.

Independent retained-stage revalidation accepted Linux stages 1–4, verified 184 raw evidence files and exact persisted reopen state hashes, and authorized continuation to stage 5. The original NO GO ledger remains preserved. A separate addendum fixes the comparison to the bounded 4,096-entry reader pool; candidate source, ZIPs and workload are unchanged. The separate final review below accepts completed qualification for the user-authorized artifact-only release.

| Ordered stage | Required duration or check | Observed evidence | Status |
|---|---:|---|---|
| Smoke | 300 seconds | 313.737-second runner lifetime; exact persisted reopen | PASS REVALIDATED |
| Load | 900 seconds | 912.461-second runner lifetime; exact persisted reopen | PASS REVALIDATED |
| Recovery | recovery assertions | readiness at 0.100944 seconds; exact persisted reopen | PASS REVALIDATED |
| Qualification | 3,300 seconds | 3,312.649-second runner lifetime; exact persisted reopen | PASS REVALIDATED |
| Endurance | 21,600 seconds | 21,613.573-second runner lifetime; two identical full LogStore persisted reopens | PASS; independent GO |

Runner lifetimes include startup and cleanup; they are not measured loader-active durations.

Endurance finished at 2026-10-02T23:48:38.041195Z (05:18:38 IST on 3 October). It recorded 85,735 successful memory ACKs and 85,734 successful log ACKs. Memory sampled reads hit 21,409/21,409; log sampled reads hit 21,410/21,410. Both averaged 0.21 ms; maxima were 3.1 ms and 3.6 ms respectively. Read/load errors and observer gaps were zero. Peak RSS was 59,724 KiB for memory and 52,652 KiB for log. Two full LogStore persisted reopens each contained 85,734 entries with identical BLAKE3 state hash `7bb6c0644c7efecd2e438589e022341903880884e464c8a2d9aab85fedc07f71`. The optional 24-hour run is not required.

The final archive contains 61 indexed files, is 4,741,938 bytes and has SHA-256 `06aa012bfc2cb906215fdf9b07ec840928e2f3c533bb89aa47c09b1bb386a6fa`. The endurance result JSON has SHA-256 `203d4be74af3503bbf876d89a59342d4c34371f5dfc1ab26256bb26c9fcb8966`; this result identity is separate from the stage-controller and resume-controller identities in the JSON manifest. Post-run integrity found no changes to 2,955 frozen original files, 184 prior evidence files or four addendum files. The container exited 0 with networking disabled, original inputs read-only and only new evidence output writable.

Independent final review is **GO**, accepted by the main executor. Review report SHA-256: `1764a6d0f385b26bcbb21e0b89d133e6059a95f937743a8f8447e2933a364c45`. The review verifies all mandatory stages, preserved lineage and immutable closure for the approved alpha scope.

Reads are bounded samples with a reader pool capped at 4,096 entries; not every successful ACK was individually read back. Exact LogStore persisted-state reopen checks cover retained stages and both endurance reopen cycles. No memory-store persistence claim is made. Apply p95 is **UNEXERCISED**. The profile does not claim maximum throughput or production readiness.

The JSON records the retained result hashes, reopen state hashes, frozen evidence identity and endurance controller/resume-manifest identities. Private evidence paths, raw logs, source files and keys are excluded from these public documents.

The five ZIP SHA-256 values and byte counts match the accepted archive bytes. The installed ZIP/template/TypeScript roundtrip and declarations probe records PASS with example, declaration and relay exits 0. Both installation and independent final review pass.

Published prerelease: [v0.1.0-alpha.1](https://github.com/whysopriyank/gunv2-releases/releases/tag/v0.1.0-alpha.1) at 2026-10-03T00:08:01Z. Source remains private.
