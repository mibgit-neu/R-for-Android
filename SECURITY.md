# Security and safe use

This application executes trusted R code and packages with access to its session/project files. It is not a hostile-code isolation service. Do not run unknown analyses on confidential data. Keep Android/WebView updated. Review exported diagnostics: they can include commands, paths, output and device information; redaction is incomplete.

Native storage restricts paths, quotas and file writes. WebView file/content access and cleartext traffic are disabled. These controls do not certify every runtime or package as safe. Repository access uses HTTPS; compatible archives currently check recorded MD5, which is not a modern authenticity mechanism. General package verification delegates to upstream. The network control is a convenience/consent control, not a proven complete containment boundary.

Interrupted package installation or multi-file synchronization can leave an incomplete library. Back up work before installation/updates. Process termination/restart can lose unsaved R objects. Resource-heavy code can exhaust memory or heat the device. A source/host review has not replaced a penetration test or broad device acceptance. No claim of absence of serious vulnerabilities is made.

When a public repository exists, report suspected vulnerabilities privately through its configured security channel. No email address or ongoing support commitment is invented by this release. Never attach datasets, credentials, original signing keys or unreviewed device reports to public issues.

## Fixed benchmark requests from other apps

The current 0.7.2 main activity accepts fixed benchmark requests through Android intents without asking for confirmation. Another installed app could use this to start a resource-heavy test. This review did not find an arbitrary-code or data-extraction route through those parameters. The APK has not been changed to address this concern. The source path is MainActivity.java: onCreate/onNewIntent → startPendingAutomation → engine.mjs automated. No caller check or confirmation is present on that path. This was not reproduced on a physical device; TESTING.md records inspection coverage.
