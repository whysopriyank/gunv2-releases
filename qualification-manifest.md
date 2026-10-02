# Draft alpha qualification manifest

**NO GO. Mandatory qualification and independent final review remain pending.** This draft identifies fixed candidate artifacts; it is not a completed qualification statement.

Private source candidate: `099cf04bfbfe02f93336303b80c26cf0df2f2606`. Public destination: documentation and artifacts only at https://github.com/whysopriyank/gunv2-releases. No private source or Git history is included.

The intended final qualification host is Linux bigbeast. Available macOS cells retain their actual platform identity and require a frozen-packet addendum before acceptance. The final controller hash, exact stage durations, evidence identities, CI/Miri states and independent final review must be sealed before GO. Earlier candidate results are not inherited.

| Ordered stage | Required seconds or check | Status |
|---|---:|---|
| fin18-1-smoke | 300 | PENDING final accepted evidence |
| fin18-2-load | 900 | PENDING final accepted evidence |
| fin18-3-recovery | recovery assertions | PENDING final accepted evidence |
| fin18-4-qualification | 3300 | PENDING final accepted evidence |
| fin18-5-endurance | 21600 | PENDING final accepted evidence |

The mandatory endurance duration is 21,600 seconds; the optional 24-hour run is not required.

Exact-candidate CI passes all eight jobs; the selected nightly Miri and fuzz jobs pass. The server host addendum remains pending.

The five ZIP SHA-256 values and byte counts in qualification-manifest.json match the accepted archive bytes. The installed ZIP/template/TypeScript roundtrip and declarations probe records PASS with example, declaration and relay exits 0. This installation check does not replace the pending long qualification stages.

Acceptance is bounded to the documented connected-client profile and platforms. No maximum-throughput or production-readiness claim is made. Update this document and the JSON together only after reviewing actual sealed evidence.
