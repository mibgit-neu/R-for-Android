# Third-party notices and source access

R for Android is an independent community project. It is not affiliated with Posit, RStudio, the R Foundation or the Android project. Original application code is offered under **GPL-3.0-or-later**, without warranty; see LICENSE. This does not replace the individual licenses of upstream components.

## Included runtime

The APK uses **webR 0.5.8 and R 4.5.1**. Runtime binaries are distributed by webR under GPLv3; webR support/application/build code is generally MIT unless marked otherwise. Preserve vendor/WEBR-LICENSE.md and the corresponding APK notice.

Version-matched upstream release and source:
- https://github.com/r-wasm/webr/releases/tag/v0.5.8
- https://github.com/r-wasm/webr/tree/v0.5.8

## Components and supplied material

| Component | License or terms | Source/notices in this kit |
|---|---|---|
| R 4.5.1 and its base/bundled material | R is available under GPL version 2 or version 3; individual bundled components retain their notices | vendor/R-4.5.1.tar.gz; redistribution/R-COPYING.txt, LAPACK-LICENSE.txt and TRE-LICENSE.txt |
| webR 0.5.8 | GPLv3 runtime; MIT where designated for support code | vendor/webr-source.tar.gz; vendor/WEBR-LICENSE.md; redistribution/WEBR-LICENSE.md |
| PCRE2 10.39 | BSD-style license in its source | vendor/pcre2-10.39.tar.gz |
| LLVM/Flang | Apache-2.0 with LLVM exceptions | redistribution/LLVM-LICENSE.txt and FLANG-LICENSE.txt; exact source links below |
| Emscripten | MIT / University of Illinois-NCSA terms, with upstream component notices | redistribution/EMSCRIPTEN-LICENSE.txt and port recipes; exact source links below |
| Cairo 1.14.12 | LGPL-2.1 / MPL-1.1 alternatives, as specified upstream | redistribution/cairo-1.14.12.tar.xz and COPYING texts; webR source contains build recipes and patches |
| Pixman 0.38.4; Fontconfig 2.15.0 | Permissive component-specific copyright/license terms | Full source archives and COPYING texts in redistribution/ |
| FreeType | FreeType License alternative and upstream component terms | redistribution/FREETYPE-FTL.txt; source/port references in SOURCE-ACCESS.md |
| libpng, zlib, bzip2, Expat | Individual permissive licenses | PNG-LICENSE.txt, ZLIB-LICENSE.txt, BZIP2-LICENSE.txt and EXPAT-LICENSE.txt in redistribution/ |
| XZ/liblzma | Component-specific terms; liblzma is public domain, which does not describe every XZ tool | redistribution/XZ-COPYING.txt and upstream webR recipe |
| Noto fonts | SIL Open Font License 1.1 | redistribution/NOTO-NOTICES.json and SIL-OFL-1.1.txt; APK includes font attribution metadata |
| GDAL, PROJ and UDUNITS data | Upstream component/data notices | redistribution/GDAL-LICENSE.txt, PROJ-LICENSE.txt and UDUNITS-LICENSE.txt; GDAL data also contains its notice |

This is a practical inventory, not a claim that every optional library in webR's recipe catalogue is linked into the APK. SOURCE-ACCESS.md lists versioned sources; TESTING.md records inspection coverage. Original upstream author names, copyright notices and license texts are intentionally preserved.

## Exact compiler/runtime source references

The runtime binary records these compiler source revisions:
- LLVM/Flang: https://github.com/r-wasm/llvm-project/tree/5892855d8a10e3d0bcce9b3b05513b4f2324c275
- Emscripten: https://github.com/emscripten-core/emscripten/tree/70404efec4458b60b953bc8f1529f2fa112cdfd1

See SOURCE-ACCESS.md and RUNTIME-COMPONENTS.json for versioned source locations and recipe details. RUNTIME_SHA256SUMS.txt and tools/runtime-hashes.json identify the retained runtime assets; RELEASE.json identifies the 0.7.2 APK.

The kit contains the original application source/build scripts, webR and R sources, selected dependency source archives, patches/recipes and versioned source links. Runtime binaries are excluded from the source ZIP and can be restored locally from the matching APK. The Android SDK and build/test tools are external development prerequisites, not bundled application dependencies.

## Independent redistribution

You may fork, modify, rename and independently redistribute the project under its applicable licenses. No contribution back to the original repository or original-developer approval is required. When distributing covered binaries, preserve required copyright/attribution/license notices, provide the corresponding source access and retain the rights required by the applicable licenses. Keep source access available while offering binaries; update the source/materials when modifying bundled components.

Optional packages installed by users are not bundled with the initial APK. They have their own licenses and dependencies; this inventory does not grant additional rights over them.
