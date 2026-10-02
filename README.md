# Fossprite

Fossprite is a self-contained, single-file, offline pixel-art editor. The application source is [`index.html`](index.html). It is designed to run directly in a modern browser without a server, CDN, npm runtime, or third-party network connection.

## Licensing scope

This distribution contains both original Fossprite code and third-party software. **Original Fossprite code is offered under the MIT License to the extent that its copyright holder can be established.** The original Fossprite copyright holder is currently **UNVERIFIED** because no copyright-holder identity was supplied with the source.

Third-party code remains under its respective license. The root [`LICENSE`](LICENSE) file must not be read as relicensing the entire `index.html`; see [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) and the complete texts in [`licenses/`](licenses/).

The application already includes the relevant attribution in its About dialog, including DogSprite by systemcrash92 and Simple Pixel Art by comficker. Those notices are intentionally preserved.

## Repository contents

- `index.html` — the Fossprite application and its embedded Base64 vendor sources.
- `LICENSE` — MIT text scoped to original Fossprite code only; the original holder is marked unverified.
- `THIRD-PARTY-NOTICES.md` — provenance, versions, license expressions, evidence, and remaining uncertainties.
- `NOTICE` — distribution notice and scope clarification.
- `licenses/` — full license texts for the licenses identified during the audit.

## Offline architecture

Codec sources are embedded in `window.PF_VENDOR_SRC` as Base64 and decoded into in-memory Blob URLs only when needed. The repository adds no runtime dependency, remote import, CDN, API, or server requirement. The two namespace URLs in the HTML are document-format identifiers (`w3.org` SVG and Apple plist DTD), not runtime network dependencies.

## Audit status

The audit is **PARTIALLY VERIFIED — UNVERIFIED ITEMS REMAIN**. The bundled package headers and official package metadata establish the principal versions and licenses listed in `THIRD-PARTY-NOTICES.md`. Exact versions for the embedded `unenv` buffer shim and its `ieee754` component were not present in the decoded source and are therefore not guessed.

This repository is documentation-ready for review, but the audit status is deliberately not a claim of universal legal compliance.

## Source integrity

The repository copy of `index.html` was made without packaging edits. Its SHA-256 is recorded in the audit working papers and can be reproduced with:

```sh
sha256sum index.html
```

The source remains a single HTML file and retains the embedded vendor source and existing attribution.
