# Runtime sources and notices

The APK contains webR 0.5.8 / R 4.5.1. Original app source/build scripts are in this project. Upstream components keep their own licenses; see LICENSE and THIRD_PARTY_NOTICES.md. Preserve required notices and provide corresponding source access when distributing binaries. Keep source access available while offering downloads.

## Included sources

- vendor/webr-source.tar.gz: webR 0.5.8 source, patches and build recipes.
- vendor/R-4.5.1.tar.gz: R 4.5.1 sources and bundled component notices.
- vendor/pcre2-10.39.tar.gz: PCRE2 sources/license.
- vendor/flang-wasm-a896e8b.tar.gz: compiler/runtime build wrapper, including its Nix source pin.
- redistribution/: Cairo 1.14.12, Pixman 0.38.4 and Fontconfig 2.15.0 source archives, component notices and Emscripten port recipes.

## Versioned upstream sources

| Component | Source location |
|---|---|
| webR 0.5.8 | https://github.com/r-wasm/webr/tree/v0.5.8 ; release https://github.com/r-wasm/webr/releases/tag/v0.5.8 |
| LLVM/Flang | https://github.com/r-wasm/llvm-project/tree/5892855d8a10e3d0bcce9b3b05513b4f2324c275 |
| Emscripten | https://github.com/emscripten-core/emscripten/tree/70404efec4458b60b953bc8f1529f2fa112cdfd1 |
| FreeType | https://github.com/freetype/freetype/tree/VER-2-13-3 |
| libpng | https://github.com/pnggroup/libpng/tree/v1.6.38 |
| zlib | https://github.com/madler/zlib/tree/v1.3.1 |
| bzip2 port | https://github.com/emscripten-ports/bzip2/tree/1.0.6 |
| Expat | https://github.com/libexpat/libexpat/tree/R_2_5_0 |
| XZ/liblzma | https://github.com/tukaani-project/xz/tree/v5.2.5 |
| GDAL data | https://github.com/OSGeo/gdal/tree/v3.8.1 |
| PROJ data | https://github.com/OSGeo/PROJ/tree/9.2.0 |
| UDUNITS data | https://github.com/Unidata/UDUNITS-2/tree/v2.2.28 |

The compiler revisions are recorded in R.wasm. Some supporting library versions follow the upstream recipes rather than independent binary attestation. RUNTIME-COMPONENTS.json lists recipe versions and source URL templates; a recipe's presence does not prove an optional library is included. See TESTING.md for the actual inspection coverage.

RUNTIME_SHA256SUMS.txt and tools/runtime-hashes.json identify the unchanged runtime. RELEASE.json identifies the current APK; BASELINE.json records the historical 0.7.1 baseline. Runtime binaries are deliberately excluded from the source ZIP. Restore them from the matching APK with tools/restore-runtime.py, as described in DEVELOPMENT.md. Routine app edits do not require rebuilding R or its compilers.
