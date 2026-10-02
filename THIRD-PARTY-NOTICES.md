# Third-Party Notices and Provenance Audit

**Status:** `PARTIALLY VERIFIED — UNVERIFIED ITEMS REMAIN`

This file covers third-party source that is actually present in the supplied `index.html`, including decoded Base64 vendor source. It does not claim that every line of the single-file application has one common license.

## Component matrix

| Name | Version bundled | License / expression | Role | Direct / nested | Bundled location | Source status / modification | Copyright / attribution | NOTICE | Verification |
|---|---:|---|---|---|---|---|---|---|---|
| DogSprite | VERSION UNVERIFIED | MIT | Source of adapted drawing engine, stabilizer, symmetry, pressure, timeline, and session recovery concepts/code as stated by the app | Direct attribution / adapted source | About dialog and Fossprite core comments/UI | Adapted; exact diff and upstream boundary are not established by this audit | systemcrash92 attribution in app; upstream LICENSE identifies copyright as SETO (2026) | No separate NOTICE identified | Partially verified |
| Simple Pixel Art | VERSION UNVERIFIED | MIT | Source of adapted themes, design language, and palette tools as stated by the app | Direct attribution / adapted source | About dialog and Fossprite UI/palette code | Adapted; exact diff and upstream boundary are not established by this audit | comficker attribution in app; upstream LICENSE identifies SimplePixelArt.com (2026) | No separate NOTICE identified | Partially verified |
| `fflate` | 0.8.3 | MIT | ZIP/DEFLATE/GZIP | Direct bundled codec | `window.PF_VENDOR_SRC.fflate` (Base64), decoded to `vendor-fflate.js` during audit | Bundled generated ESM build; exact local modifications not established | Upstream package/repository: 101arrowz; license text retains generic copyright placeholder in SPDX text, while upstream license page gives 2026 Arjun Barrett | No separate NOTICE identified | Verified for version/license; source diff unverified |
| `ag-psd` | 31.0.2 | MIT | PSD import/export | Direct bundled codec | `window.PF_VENDOR_SRC.agPsd` (Base64), decoded to `vendor-agPsd.js` | Bundled ESM build; Fossprite applies a runtime import-path replacement for its buffer shim | Agamnentzar | No separate NOTICE identified; upstream LICENSE notes image/brush files have separate copyright scope | Verified for package/version/license; adaptation documented |
| `@pixelation/aseprite` | 1.2.7 | Apache-2.0 | Aseprite import | Direct bundled codec | `window.PF_VENDOR_SRC.aseprite` (Base64), decoded to `vendor-aseprite.js` | Bundled ESM build; exact local modifications not established | Jake Hamilton; npm metadata | No separate NOTICE identified in reviewed package metadata | Verified for package/version/license |
| `pako` | 2.1.0 in Aseprite bundle; VERSION UNVERIFIED in ag-psd bundle | MIT AND Zlib | Deflate/inflate nested code | Nested in `aseprite`; also identifiable inside `ag-psd` | Decoded `vendor-aseprite.js` and `vendor-agPsd.js` bundled-license markers | Bundled/generated nested source | Nodeca project attribution in bundled marker | No separate NOTICE identified | Partially verified; exact ag-psd nested version unverified |
| `@theprogrammingiantpanda/xcfreader` | 1.1.0 | MIT | XCF import | Direct bundled codec | `window.PF_VENDOR_SRC.xcf` (Base64), decoded to `vendor-xcf.js` | Bundled ESM build; exact local modifications not established | npm metadata: xcfreader contributors; upstream repository linked to `andimclean/xcfreader` | No separate NOTICE identified | Verified for package/version/license |
| `@wieslawsoltes/quikgraphweb` (`nrbf`) | 0.2.0 | Ms-PL / MS-PL | MS-NRBF decoder for PDN import | Direct bundled subpath | `window.PF_VENDOR_SRC.nrbf` (Base64), decoded to `vendor-nrbf.js` | Bundled package subpath; exact local modifications not established | QuikGraphWeb contributors; npm metadata names Wiesław Šoltés as maintainer/author context | No separate NOTICE identified | Verified for package/version/license |
| `unenv` buffer runtime | VERSION UNVERIFIED | MIT | Browser Node-buffer compatibility shim | Nested/runtime shim for `ag-psd` | `window.PF_VENDOR_SRC.buffer` (Base64), decoded to `vendor-buffer.js` | Bundled generated shim; exact upstream release not stated in source | Bundled marker credits unenv and Feross Aboukhadijeh for the buffer implementation | No separate NOTICE identified | License/provenance verified; version unverified |
| `ieee754` | VERSION UNVERIFIED | BSD-3-Clause | Floating-point helpers inside buffer shim | Nested in `unenv` buffer runtime | `vendor-buffer.js` bundled-license marker | Bundled nested source; exact upstream release not stated | Bundled marker credits Feross Aboukhadijeh and links feross.org/opensource; upstream license credits Fair Oaks Labs, Inc. | No separate NOTICE identified | License/provenance verified; version unverified |

## License obligations addressed

- **MIT:** full text is included in `licenses/MIT.txt`; copyright and license notices are retained in the source and this notice file. The root `LICENSE` is explicitly scoped to original Fossprite code.
- **Apache-2.0:** full text is included in `licenses/Apache-2.0.txt`. The source and this file retain the package attribution. A separate upstream NOTICE was not identified in the reviewed npm metadata or decoded marker; this remains an evidence boundary, not a guarantee.
- **Ms-PL:** full text is included in `licenses/MS-PL.txt`. The component is identified as Ms-PL and is not relicensed as MIT.
- **Zlib:** full text is included in `licenses/Zlib.txt`; the nested pako expression remains recorded as `MIT AND Zlib`, not simplified to MIT.
- **BSD-3-Clause:** full text is included in `licenses/BSD-3-Clause.txt`, including the three conditions and disclaimer. The no-endorsement condition is called out by retaining the upstream attribution rather than using it as a product endorsement.

## Evidence

1. fflate official repository and license: <https://github.com/101arrowz/fflate>, <https://raw.githubusercontent.com/101arrowz/fflate/master/LICENSE>
2. ag-psd official repository and license: <https://github.com/Agamnentzar/ag-psd>, <https://raw.githubusercontent.com/Agamnentzar/ag-psd/master/LICENSE>
3. `@pixelation/aseprite@1.2.7` official npm registry metadata: <https://registry.npmjs.org/@pixelation%2faseprite/1.2.7>; repository: <https://github.com/jakehamilton/pixelation>
4. `@theprogrammingiantpanda/xcfreader@1.1.0` official npm registry metadata: <https://registry.npmjs.org/@theprogrammingiantpanda%2fxcfreader/1.1.0>; repository listed in metadata: <https://github.com/andimclean/xcfreader>
5. `@wieslawsoltes/quikgraphweb@0.2.0` official npm registry metadata: <https://registry.npmjs.org/@wieslawsoltes%2fquikgraphweb/0.2.0>; repository: <https://github.com/wieslawsoltes/QuikGraphWeb>
6. unenv official repository and license: <https://github.com/unjs/unenv>, <https://raw.githubusercontent.com/unjs/unenv/main/LICENSE>
7. ieee754 official repository and license: <https://github.com/feross/ieee754>, <https://raw.githubusercontent.com/feross/ieee754/master/LICENSE>
8. DogSprite upstream and license: <https://github.com/systemcrash92/DogSprite>, <https://raw.githubusercontent.com/systemcrash92/DogSprite/main/LICENSE>
9. Simple Pixel Art upstream and license: <https://github.com/comficker/simplepixelart>, <https://raw.githubusercontent.com/comficker/simplepixelart/main/LICENSE>
10. Apache License 2.0 official text: <https://www.apache.org/licenses/LICENSE-2.0.txt>
11. Microsoft Public License text / SPDX identifier: <https://licenses.nuget.org/MS-PL>
12. Zlib official license page: <https://zlib.net/zlib_license.html>
13. BSD-3-Clause authoritative SPDX text: <https://spdx.org/licenses/BSD-3-Clause.html>

## Unverified and remaining issues

1. The exact upstream release/tag and local diff for each Base64 build were not independently byte-matched to an upstream tarball. The bundled header establishes the principal versions listed above, but not a full source-diff result.
2. The exact versions of `unenv` and `ieee754` are not present in the decoded source and are intentionally not guessed.
3. The exact version of the adapted DogSprite and Simple Pixel Art source is not stated in the application.
4. Copyright ownership of original Fossprite code was not supplied; the root LICENSE marks it `UNVERIFIED`.
5. No separate Apache NOTICE file was found in the reviewed package metadata/source markers. A later upstream-specific NOTICE discovery should be added if required by the exact source release.
6. The source includes format parsers and compatibility code beyond the five named runtime-report packages. Where a component is native Fossprite code or its upstream boundary cannot be separated, this file marks that boundary as unverified rather than assigning a guessed license.

## Audit working papers

The audit extracted the Base64 assignment and decoded component hashes outside the distributable repository. The source baseline hash for the repository copy is:

```text
36feb50ed01d35b1ecc685abb0eb9d00f5526bf90cd59e1ce6c6ca173942e00c  index.html
```

The application source itself retains its existing attribution and embedded vendor source. No vendor source was deleted, replaced by a CDN, or moved to an external runtime dependency during repository packaging.
