# R for Android

Run R locally on an Android™ phone or tablet.

R for Android is a free, open-source app for writing scripts, running analyses and viewing results. It is designed to be simple to install and use, including for people coming from desktop RStudio or learning R. R runs on your device through [webR](https://github.com/r-wasm/webr). A remote server or R account is not required.

This is a community project, shared **as-is**. It is not affiliated with Posit, RStudio, the R Foundation or the Android project.

## A community release you can make your own

Students, universities, researchers, educators, open-source communities and individuals are welcome to **use, study, adapt, rename, fork, build and redistribute** this project under its applicable licenses. You may maintain your own version for your needs, independently of this repository.

You do not need the original developer's approval, access to a private service or a commitment to contribute changes back here. There is no requirement for a centrally maintained version, a formal partnership or ongoing coordination. 

No ongoing support or maintenance is promised. The community is free to test and adapt the app to its needs.

The original application code is GPL-3.0-or-later. If you distribute a modified version, preserve the applicable notices and give recipients the required source access and license rights. Private modifications do not have to be published. Upstream components keep their own license terms. These obligations do not require submitting changes to this repository.

## Download and install

Download the APK and accompanying source and notices from this repository's **Releases** page when a release is available. 

1. Export important work from an existing installation.
2. On Android 10 or later, open the APK and allow installation from that source if Android asks.
3. Open **R for Android** and wait for **R ready**. After that, you are ready to go.

The app was previously named **R Tablet**. The new display name does not change its package ID (`org.rtablet.local`) or storage format. Android also requires matching signing keys for an update. 

The complete application source is inside the community-release ZIP. Extract it, then extract RforAndroid-0.7.2-source.zip. 

## What it can do

- Edit and run R scripts, with multiple document tabs.
- Execute R chunks in `.qmd` files and display captured results.
- Show console output, tables and plots.
- Offer editor themes, font settings, bracket helpers and lightweight completion.
- Run diagnostic, performance and stress checks when requested.
- Provide offline guides in English, Brazilian Portuguese, Spanish and Chinese. English is the default.

The QMD tools execute R chunks; they are **not a full Quarto rendering engine**. Completion is lightweight and is not the RStudio completion system.


## Packages and internet access

The included R environment can run locally without a network connection. Package installation and other network operations need a connection. Package availability depends on compatible WebAssembly binaries and their dependencies. Desktop Windows/macOS/Linux binaries cannot simply be installed in this app. Tools that depend on external programs or native desktop toolchains may not work.

See [PACKAGE_COMPATIBILITY.md](PACKAGE_COMPATIBILITY.md). Large analyses can exceed a device's memory or take a long time. Start with smaller workloads and save your work.

## Privacy and safe use

The app has no telemetry. Scripts and session data are processed locally. Package repositories receive network requests when you install packages; your own R code may also access the network.

Run only code and packages you trust. The app is not a sandbox for hostile R code. Exported reports may contain your code, output, device details or data, so review them before sharing. Back up important scripts and results. See [PRIVACY.md](PRIVACY.md), [SECURITY.md](SECURITY.md) and [testing and inspection coverage](TESTING.md).

The refreshed external user guides are in `guides/` (open `index.html` after downloading). The existing APK keeps its original embedded guides.

## Source layout: what is needed and what is guidance

| Files or folders | Role |
|---|---|
| `app/src/main/java/` | Essential Android application code: interface, editing, files and the R bridge. |
| `app/src/main/AndroidManifest.xml` and `app/src/main/res/` | Essential Android settings, app label, icons and resources. |
| `app/src/main/assets/engine.html`, `engine.mjs`, `packages.R` and related R/assets | Essential runtime integration and package handling. |
| `app/src/main/assets/runtime/` | Essential webR runtime in an installed APK. Excluded from the source ZIP; restore it from the matching APK using the supplied tool. |
| Gradle files and `tools/build.sh` | Build configuration and the documented direct build route. Use the route described in DEVELOPMENT.md. |
| `docs/guides-content.py`, `tools/update-guides.py`, `app/src/main/assets/learning/` | Editable guide content, generator and packaged offline guides. Helpful to users; not the R engine. Regenerate guides after editing their source. |
| `LICENSE`, `THIRD_PARTY_NOTICES.md`, `redistribution/`, `vendor/`, runtime source/hash records | Licensing, source access and provenance material. Keep the required notices and source access when sharing binaries. Not application logic. |
| `README.md`, `USING.md`, `DEVELOPMENT.md`, `ARCHITECTURE.md`, `BUILDING.md` | Project guidance added for users and contributors. Editing these does not change the installed app by itself. |
| `AGENTS.md`, `HANDOFF.md`, `CONTRIBUTING.md` | Optional guidance for editors and AI assistants. Not loaded by the Android app or R. Adapt it to your workflow. |
| `guides/` | Updated external guides and their editable prose/generator. Optional documentation; not loaded by the unchanged APK. |
| `tests/`, `tools/check.py`, `TESTING.md` and diagnostics | Test tools and a concise record of what was checked and what remains untested. Historical results are not tests of your new edit. |

The source kit contains original application code plus upstream source archives, build recipes and versioned source links. It does not contain the Android SDK, the original signing key, a user's installed optional packages or their private projects. The 0.7.2 APK uses a different signing key from the earlier 0.7.1 release and cannot update it directly. See RENAME-NOTES.md. Export your work before attempting a migration, and do not uninstall the old app before saving your files. 

## Make a change

Make this project your own: change the interface, add features, test larger workloads or adapt it for teaching and research.

The development notes and AI-assistant instructions are there to help you get started. You are free to adapt them or use your own workflow.

Start with [DEVELOPMENT.md](DEVELOPMENT.md). Make a checkpoint, edit the relevant files and run the smallest useful check. For normal interface, theme or guide changes, you do **not** need to rebuild R, LLVM or Emscripten or rerun every statistical benchmark.

```sh
python3 tools/check.py quick
```

Build instructions explain SDK setup, runtime restoration and signing. Keep private keys outside the project and out of Git. If you change bundled dependencies, revisit their notices and source access. Record what you changed, what you tested and what remains untested.


## License and acknowledgements

Original application source is licensed under **GNU GPL version 3 or later**, without warranty. Upstream components retain their own licenses and credits. See [LICENSE](LICENSE), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) and [SOURCE-ACCESS.md](SOURCE-ACCESS.md).

R provides the statistical language. webR provides R compiled to WebAssembly and its browser/runtime interface. Android and the system WebView provide the platform. The native app interface, editing/file workflows, runtime integration and user materials form this project. No RStudio source was identified in the reviewed project; familiar editor features do not imply that RStudio was ported.

Keep the matching source and notices accessible with a binary release. An open-source license and a limited engineering review are not guarantees of security, device compatibility or scientific correctness. This experimental release is not certified for clinical use.

Android is a trademark of Google LLC
