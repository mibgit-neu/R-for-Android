# Testing and inspection coverage

This file summarizes the evidence kept with the community release. Historical results are not new tests of a future edit. Physical-device behavior is not established by host or source checks.

## R for Android 0.7.2

The 1 November rename/build verification records:

| Check | Recorded result |
|---|---|
| Source quick checks | Guide generation/local links, manifest settings and required entrypoints passed |
| Java core helper suite | 26 assertions passed |
| APK build, signature, alignment and ZIP checks | Passed |
| Packaged assets versus source | 148 byte matches |
| Runtime versus recorded manifest | All 113 hashes matched; R/webR unchanged |
| Physical Android installation/update, typing and file picker | Not run for this build |
| Full statistical/performance/stress suites | Not rerun for the branding change |

RELEASE.json identifies this APK and its recorded application-input hash. The new signer cannot directly update the old 0.7.1 installation. See RENAME-NOTES.md before migration.

## Historical baseline evidence

The 1 November 0.7.1 handoff checks recorded 148 matching packaged assets, 113 runtime files matching the official webR release, 26 passing core assertions, runtime-restoration fixtures (correct restore and rejection of unsafe/mismatched inputs), privacy-scanner fixtures, guide/link checks and build-shell syntax. Artwork metadata removal preserved RGBA pixels. That pass verified JAR/v1 signing and did not claim a new v2/v3 signature check or Android device execution. BASELINE.json identifies the historical artifact.

## Secret/security inspection and guide revision — 3 November 2026

- Release/source checksums, archive integrity, all 148 APK assets and the recorded application-input hash matched during read-only inspection.
- APK secret scan: 209 scan visits, including decompressed assets; no targeted findings.
- Original source scan: 10,895 visits through nested gzip/tar sources. Three Windows-path candidates occurred in upstream R documentation/foreign test fixtures; they were reviewed as upstream examples/metadata, not project credentials.
- Additional XZ-archive scan: 5,336 source members, no targeted findings. Additional APK token patterns found no candidates.
- Reviewed manifest, WebView/bridge setup, ResourceServer, FileStore, engine CSP, runtime integration and package-installation code. The source-confirmed benchmark-intent concern is retained in SECURITY.md; it was not reproduced on a device or fixed in this APK.
- Refreshed external guides passed generation/link/highlight checks. Example R code and copy-button scripts matched the original bytes. Modified documentation passed targeted secret-pattern checks. The APK and its embedded guides were unchanged.

Scan visits are not unique file counts. Public upstream author/license credits were intentionally preserved. Pattern scans do not prove that every secret format or vulnerability is absent. No penetration test, full dependency-CVE sweep, adversarial fuzzing, APK rebuild or physical-device test was performed in this documentation pass. No independent native-speaker review of every guide translation is claimed.

## Public-material cleanup

Redundant narrative assessments were removed from the public bundle, with their test scope summarized here. Source/notice locations remain in SOURCE-ACCESS.md and THIRD_PARTY_NOTICES.md. No app inputs, APK bytes, tests, assertions or license texts were changed. The cleanup checked retained links, source/APK identity, archive integrity and regenerated checksums; it did not rerun application or statistical suites.

For a future edit, choose the relevant small checks in DEVELOPMENT.md. Record what actually ran and what remains untested rather than carrying these results forward as a new pass.
