# Draft alpha qualification manifest

**NO GO. Mandatory six-hour endurance and independent final review remain pending.** This draft identifies fixed candidate artifacts and accepted retained stages; it is not a completed qualification statement.

Private source candidate: `099cf04bfbfe02f93336303b80c26cf0df2f2606`. Public destination: documentation and artifacts only at https://github.com/whysopriyank/gunv2-releases. No private source or Git history is included. The five ZIP identities remain unchanged.

The original 329-file FIN-17 packet and 81-file Linux bigbeast READY addendum are accepted. Exact-candidate CI passes all eight jobs; selected nightly Miri and fuzz jobs pass. Platform-specific macOS evidence retains its actual platform identity.

Independent retained-stage revalidation accepted Linux stages 1–4, verified 184 raw evidence files and exact persisted reopen state hashes, and authorized continuation to stage 5. The original NO GO ledger remains preserved. A separate addendum fixes the comparison to the bounded 4,096-entry reader pool; candidate source, ZIPs and workload are unchanged. This acceptance does not authorize publication.

| Ordered stage | Required duration or check | Observed evidence | Status |
|---|---:|---|---|
| Smoke | 300 seconds | 313.737-second runner lifetime; exact persisted reopen | PASS REVALIDATED |
| Load | 900 seconds | 912.461-second runner lifetime; exact persisted reopen | PASS REVALIDATED |
| Recovery | recovery assertions | readiness at 0.100944 seconds; exact persisted reopen | PASS REVALIDATED |
| Qualification | 3,300 seconds | 3,312.649-second runner lifetime; exact persisted reopen | PASS REVALIDATED |
| Endurance | 21,600 seconds | started 2026-10-02T17:47:09.480926Z | RUNNING |

Runner lifetimes include startup and cleanup; they are not measured loader-active durations.

The earliest endurance duration boundary is 2026-10-02T23:47:09.480926Z, or 05:17 IST on 3 October. It is not a promised GO time: completion assertions, persisted reopens, final evidence sealing and independent final review follow. The optional 24-hour run is not required.

Reads are bounded samples with a reader pool capped at 4,096 entries; not every successful ACK was individually read back. Exact persisted-state reopen checks cover accepted retained stages; the endurance checks remain pending. Apply p95 is **UNEXERCISED**. The profile does not claim maximum throughput or production readiness.

The JSON records the retained result hashes, reopen state hashes, frozen evidence identity and endurance controller/resume-manifest identities. Private evidence paths, raw logs, source files and keys are excluded from these public documents.

The five ZIP SHA-256 values and byte counts match the accepted archive bytes. The installed ZIP/template/TypeScript roundtrip and declarations probe records PASS with example, declaration and relay exits 0. That installation check does not replace endurance or independent final review.
