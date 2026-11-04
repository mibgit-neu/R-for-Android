# Editing and building

## Begin from the working version

Use this source archive with the R for Android 0.7.2 APK. The historical 0.7.1 baseline records the same runtime. Read HANDOFF.md before changing anything. Commit your initial checkout or make a copy; keep your new edits separate from the baseline. No test suite runs automatically when opening or editing this project.

The APK already contains the runtime. Restore its recorded files locally:

```sh
python3 tools/restore-runtime.py /absolute/path/RforAndroid-0.7.2.apk
python3 tools/check.py quick
```

Alternatively pass the official `webr-0.5.8.tar.gz` release archive to the same command. The tool checks every recorded SHA256, copies only expected runtime assets and refuses to replace an existing runtime. It never executes archive contents or downloads anything. You do not need to build R, LLVM, Flang or Emscripten to change the app.

## Choose the files and checks for your change

| Change | Edit | Normally sufficient validation |
|---|---|---|
| Root documentation | Markdown files | Read the changed text and check local links |
| Offline user-guide prose | `docs/guides-content.py` | Regenerate with `python3 tools/update-guides.py`; run `python3 tools/check.py docs`; inspect affected guide on a small screen |
| Editor parsing/storage helpers | Relevant Java helper | `python3 tools/check.py core` and a reproduction of the changed behavior |
| Native UI/keyboard | Relevant Java/resources | Build once; exercise affected flow in portrait/landscape on Android; use the focused native harness when useful |
| Engine/package handling | `engine.mjs` / `packages.R` | One affected real-R execution/install/restart case; run smoke if initialization or persistence changed |
| Unchanged upstream runtime | Nothing | Keep the recorded hashes; no rebuild or statistical benchmark required |
| Runtime replacement | Runtime manifest and provenance | Deliberate separate project: initialization, representative statistics/plots/packages, licenses and affected devices |

Do not run performance, stress, endurance or a full statistical suite for a spelling, documentation or unrelated UI edit. Expand checks when an actual failure or shared subsystem warrants it. Record what ran and what did not. Existing tests remain available; this is proportional validation, not permission to remove assertions.

## Build an APK

Use Linux/bash, Python 3, JDK 17, Android SDK platform 35 and build-tools 35. Put the SDK and a signing key outside the project. In your own private environment set:

```sh
export RTABLET_BUILD_TOOLS=/absolute/path/android-sdk/build-tools/35.0.0
export RTABLET_ANDROID_JAR=/absolute/path/android-sdk/platforms/android-35/android.jar
export RTABLET_SIGNING_KEY=/absolute/path/private-signing-key.jks
export RTABLET_SIGNING_ALIAS=your-key-alias
read -rs RTABLET_SIGNING_PASSWORD; export RTABLET_SIGNING_PASSWORD
bash tools/build.sh
unset RTABLET_SIGNING_PASSWORD
```

Use your own key; no original private key or password is supplied. The helper compiles Java, packages current assets, aligns/signs the APK, verifies the signature and compares packaged assets with source. These are packaging checks, not an extensive runtime suite. Outputs go into a new directory under `dist/`; existing APKs are never overwritten. The manifest supplies the application ID and version.

For a new version, update versionCode/versionName in the manifest and app/build.gradle plus VERSION/BUILD in MainActivity; check the engine's build fallback and run_all_tests.R if they contain the old identity. Regenerate embedded guides after changing BUILD. Use a new RTABLET_BUILD_TAG if making another artifact with the same version; increasing versionCode is still necessary for a normal update. Changing the app ID makes a separate app. Changing the signer normally prevents replacing an installed app; plan backup/migration.

The Gradle files are also editable Android project inputs. No Gradle wrapper, SDK or cached dependencies are bundled. The bash helper is the direct documented build route for this kit.

## Host checks beyond quick/core

Existing browser tests use Node, Playwright and JSZip. Install them into your own test environment, set `RTABLET_NODE_MODULES` to its node_modules directory and `CHROME_BIN` to a compatible Chromium executable. Read an individual test before running it; some tests need package fixtures or previous versions not included here. The native framework harness has its own instructions in tests/native-ui/README.md. Neither harness replaces testing a real Android keyboard.

Keep SDKs, node_modules, keystores, datasets and generated reports outside a distributable source archive. Publish the source matching any modified APK and preserve applicable upstream notices. See THIRD_PARTY_NOTICES.md and SOURCE-ACCESS.md for the runtime source/notice records. Routine app edits do not require redoing that review.
