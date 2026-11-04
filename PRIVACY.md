# Privacy and data handling — baseline 0.7.1 candidate R2

R for Android stores scripts, imported data, drafts, recent command history, installed packages and diagnostics in app-private storage. R objects also live in memory and require explicit saving. Android backup is disabled in the current manifest. Uninstalling can remove private data; export important work first.

The reviewed application shell contains no analytics or automatic report-upload implementation. This is not a guarantee about arbitrary R code or third-party packages. Enabling package networking permits repository requests; the repository receives normal connection/request information. Do not treat the network switch as an independently proven security sandbox.

Import and export use Android document selection. Your selected storage provider may have its own cloud/privacy behavior. Reports may contain device/build details, file paths, commands, warnings or reproduction code. Review reports before sharing; automated redaction is incomplete. Exporting is an explicit user action.

Code and packages execute with access to the R session and its files. Avoid running unknown scripts/packages on confidential data. No account or cloud synchronization is required by the application shell. This notice describes the current candidate, not future extensions or upstream services.
