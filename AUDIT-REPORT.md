# Fossprite Audit Report

## A. Repository structure

```text
Fossprite/
├── index.html
├── README.md
├── LICENSE
├── NOTICE
├── THIRD-PARTY-NOTICES.md
└── licenses/
    ├── Apache-2.0.txt
    ├── BSD-3-Clause.txt
    ├── MIT.txt
    ├── MS-PL.txt
    └── Zlib.txt
```

## B. Source inventory

- Input/source: `index.html`
- Size: 1,194,619 bytes
- Lines: 13,249
- Inline script tags: 8
- Style tags: 4
- `window.PF_VENDOR_SRC`: present
- Base64 markers: 15 occurrences
- Runtime URL markers: only SVG and Apple plist document identifiers; no remote script, stylesheet, fetch, WebSocket, or CDN runtime dependency was added.
- Baseline SHA-256: `36feb50ed01d35b1ecc685abb0eb9d00f5526bf90cd59e1ce6c6ca173942e00c`

## C. Vendor extraction

`window.PF_VENDOR_SRC` was evaluated in a restricted Node VM and each Base64 array was decoded to an audit-only file. The decoded component hashes and sizes are recorded in the audit working papers. The six direct vendor entries are `fflate`, `agPsd`, `aseprite`, `xcf`, `nrbf`, and `buffer`.

The decoded source contains bundled-license markers for `pako 2.1.0` in the Aseprite bundle with the expression `MIT AND Zlib`, and for `ieee754` / `unenv` in the buffer shim. No version marker for the latter two was found.

## D. Provenance and license result

The detailed component matrix and evidence URLs are in `THIRD-PARTY-NOTICES.md`. Verified principal package facts come from the official npm registry metadata, official upstream repositories, official license texts, and the decoded bundle headers. Adaptation boundaries and exact byte-for-byte upstream matches remain unverified.

## E. Source changes

Repository packaging copied the current supplied Fossprite `index.html` without functional or dependency changes. No source, Base64 bundle, attribution, or license header was removed. The current source already reflects prior user-requested branding and limit changes made before this audit. Those prior changes are not silently represented as packaging changes.

## F. Offline check

The repository remains `single-file + offline + self-contained`. Vendor sources remain embedded as Base64. No CDN, npm runtime, external API, remote vendor source, or server-side requirement was introduced.

## G. Double audit checklist

### Audit A — source

- [x] Whole HTML and inline scripts scanned.
- [x] Base64 vendor assignment extracted and decoded.
- [x] Package/version/license markers checked.
- [x] Nested `pako`, `unenv`, and `ieee754` markers checked.
- [x] Existing DogSprite and Simple Pixel Art attribution retained.
- [ ] Exact upstream source diff for every generated bundle — **UNVERIFIED**.
- [ ] Exact `unenv` and `ieee754` versions — **UNVERIFIED**.

### Audit B — repository

- [x] `index.html` present and hash recorded.
- [x] Root license scope is explicit and does not claim third-party code.
- [x] Full license files included for identified license families.
- [x] Provenance and evidence documented.
- [x] Remaining uncertainties disclosed.
- [x] Offline characteristics preserved.

## H. Final compliance status

`PARTIALLY VERIFIED — UNVERIFIED ITEMS REMAIN`

This is not a claim of `100% license compliant`, legal advice, or a guarantee. It is the strongest status supported by the available source and authoritative evidence.
