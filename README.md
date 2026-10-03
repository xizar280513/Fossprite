<p align="center">
  <img src="https://raw.githubusercontent.com/xizar280513/Fossprite/main/Fossprite%20logo.png" alt="Fossprite logo" width="112" align="middle">
  <img src="https://raw.githubusercontent.com/xizar280513/Fossprite/main/Fossprite.png?v=previous-wordmark-20261003" alt="Fossprite wordmark" width="320" align="middle">
</p>

# Fossprite

Fossprite is a self-contained, single-file, offline pixel-art editor. The application source is [`index.html`](index.html). It runs directly in a modern browser without a server, CDN, npm runtime, or third-party network connection.

This README documents the user-facing features implemented in `index.html`, including the core editor, animation and project workflows, Extra Tools, import/export formats, and keyboard shortcuts. Format support is intentionally described with its implemented subset and known limitations rather than implying compatibility with every feature of the external application named by a format.

## Project origin and goals

**Created by Xizar with help from AI.** I started Fossprite after noticing that pixel-art software often offers different features and file formats from one product to another, while some advanced tools are paid and can be very expensive. I wanted to bring a broad set of professional-style pixel-art, animation, and interchange capabilities together in one accessible editor, so more people can use these kinds of tools without having to buy several costly programs. Fossprite aims for broad, practical format support; each format's actual supported subset is listed below.

The project prioritizes **100% client-side, local, offline use**: the app runs in the browser, artwork stays on the user's device, and no server or cloud account is required. The single-file design makes it easy to inspect and run locally. My goal is to keep Fossprite **fully open source** so people can use it, inspect how it works, and help improve it. Third-party components retain their own licenses, and the current license scope and audit caveats are described in [Licensing scope](#licensing-scope).

## Beta status and how to help

**Fossprite is currently in beta.** Features and format compatibility are still evolving, and bugs or rough edges are possible. Please keep backups of important artwork, especially when testing interchange formats. You can help by testing the editor, suggesting improvements, contributing, or reporting bugs in the [Fossprite Discord](https://discord.gg/tD9uVgUu4n). For a useful bug report, include your browser and operating system, steps to reproduce, what you expected, what happened instead, and a sample file or screenshot only when it is safe to share.

## Feature inventory

### Workspace and documents

- **Tabbed, multi-document workspace:** create, open, switch between, rename, and close sprite documents. Each document tracks its own canvas, frames, layers, palette, view, and saved/dirty state.
- **New sprite setup:** set a name, custom pixel width and height, and transparent, white, or foreground-color background. Square presets are 16×16, 32×32, 48×48, 64×64, 96×96, and 128×128.
- **Canvas resize:** change width and height independently and choose an anchor from a 3×3 grid. Existing pixels are repositioned and cropped or padded; resize does **not** scale the artwork.
- **Starter art:** insert a recolorable template into the current document or open it as a separate document. The 16 built-in templates are **Dog, Cat, Heart, Mushroom, Sword, Potion, Ghost, Slime, Ship, Coin, Star, Tree, Flower, Key, Skull,** and **Chest**.
- **Document tabs:** each tab displays its name, canvas dimensions, and unsaved-change indicator. Double-click a tab name to rename it.

### Drawing tools and brush behavior

The tool rail contains ten tools:

| Tool | Shortcut | What it does |
| --- | --- | --- |
| Brush | `B` | Paint pixels with the foreground color. |
| Eraser | `E` | Erase pixels to transparency. |
| Fill | `G` | Flood-fill the current color; respects the active selection. |
| Picker | `I` | Sample a color from the visible composite. |
| Line | `L` | Draw a line; hold Shift to snap to 45° increments. |
| Rectangle | `R` | Draw an outline or filled rectangle; hold Shift to constrain it to a square. |
| Ellipse | `O` | Draw an outline or filled ellipse; hold Shift to constrain it to a circle. |
| Select | `M` | Make a rectangular marquee selection. |
| Move | `V` | Move the selection, or the whole active layer when nothing is selected. |
| Pan | `S` | Pan the canvas view. |

Brush and drawing options include:

- Brush size from 1 to 32 pixels, quick size buttons 1–5, and square or round brush shape.
- Freehand algorithms: **Default**, **Pixel-perfect**, and **Dots**. Dots supports **Accumulate** and **Update last** trace policies.
- A stroke stabilizer, configurable shape size, and filled/outline shape mode.
- Pen-pressure mapping **Off**, **Size**, **Alpha**, or **Both**, with minimum size and alpha controls.
- Foreground/background colors and swap, plus symmetry modes **Off**, **Horizontal**, **Vertical**, or **Both**. The dashed symmetry axes can be dragged to reposition them.
- Contextual tool hints, hover previews, and support for sampling color with `Alt`+click, panning with Space+drag, and constrained drawing with Shift.

### Selection and editing

- Rectangular marquee selection with replace, add, subtract, and intersect modes in Extra Tools. Shift adds, Alt subtracts, and Ctrl intersects while using the Select tool. Selection geometry is rectangular.
- Selection utilities to select opaque content on the active layer, select the full canvas, or deselect.
- Cut, copy, paste, delete, select all, and deselect; standard undo and redo history.
- Flip the active layer horizontally or vertically.
- Move the selected pixels or, when no selection exists, move the active layer.
- Layer, frame, palette, and drawing edits participate in undoable history where implemented.

### Color and palettes

- HSV-style saturation/value and hue controls, a hex color field, a browser color input, foreground/background swatches, and foreground/background swapping.
- Six built-in palettes: **PICO-8**, **Sweetie 16**, **DawnBringer 16**, **Game Boy**, **Endesga 32**, and **NES (54)**.
- Click a palette swatch to set the foreground; right-click a swatch to set the background; Shift-click a swatch to remove it.
- Add the current foreground color to the document palette, or extract a palette from the current frame’s artwork (up to 256 colors).
- Extra Tools adds a color wheel and seven harmony choices: **complementary, analogous, triadic, split, tetradic, square,** and **mono**.

### Layers

- Add, duplicate, merge down, move up/down, and delete layers.
- Select the active layer, rename it, toggle visibility, and adjust opacity.
- Extra Tools adds layer locking and blend modes: **normal, multiply, screen, overlay, darken, lighten,** and **add**. Locking prevents painting on the active layer; blend modes affect the composite and exports.

### Animation timeline

- Multi-frame documents with an editable timeline, per-frame thumbnails, and displayed frame durations.
- Add and clone frames, select a frame, delete a frame, and drag frames to reorder them.
- Set the active frame’s duration or apply an FPS value to the document; the playback controls also provide loop playback.
- Onion-skin preview with adjustable opacity and 1–3 neighboring frames, plus play/stop controls.
- Extra Tools provides named animation tags with start/end frame ranges and **forward, reverse,** or **ping-pong** playback.

### Canvas view and previews

- Zoom from 6.25% to 6400%, zoom to 100%, zoom in/out, and fit the sprite to the viewport. The mouse wheel zooms; pan by dragging with the Pan tool or Space+drag.
- Toggle the transparency checkerboard and pixel grid. The pixel grid is shown at high zoom.
- Toggle the floating preview and timeline panel.
- Extra Tools’ **Seamless tiled canvas** shows a repeating 3×3 viewport preview for checking texture seams. This is a view aid only; it does not change exported pixels.

### Image import and conversion

The Import dialog has three workflows:

1. **Convert image:** import a browser-decodable image, set target dimensions and a color count from 2–128, preview the result, and optionally remove stray pixels with the pixel cleaner. The conversion uses a median-cut palette and preserves sufficiently transparent pixels as transparent. Apply the result as a new document, as a new layer when its dimensions match the active canvas, or as the active document’s palette.
2. **Sprite slicer:** load a spritesheet image, set its column/row grid, preview the slices, and import the slices as animation frames. Aseprite-compatible spritesheet JSON metadata can also be loaded with its associated image.
3. **Project:** open Fossprite project JSON and restore its document content, including layers, frames, durations, palettes, and supported Extra Tools project data.

The format hub accepts multiple files and drag-and-drop. It also routes recognized project formats and common raster images to their appropriate import handlers. Common raster image inputs include PNG, JPEG, GIF, WebP, and BMP, subject to the browser’s image decoder; other browser-decodable `image/*` inputs may work as well.

### Export

The standard Export dialog provides:

- **PNG:** export the current frame with transparency at 1×, 2×, 4×, or 8×.
- **GIF:** export the animation using the timeline’s frame durations and transparent pixels.
- **Sprite sheet:** pack frames from left to right, choose a column count (0 means automatic), and optionally download Aseprite-compatible JSON metadata.
- **SVG:** vector rectangles for the pixels in the current frame.
- **JSON project:** save the full project, including layers, frames, durations, palettes, and supported Extra Tools data.

The Universal Format I/O hub additionally exports **PNG, JPG, WebP, GIF,** and **SVG**. JPG is flattened against white; JPG and WebP encoding depend on browser support. Raster image exports from the hub use the active frame, while GIF is an animation export.

### Saved projects, snapshots, and recovery

- **Save project** stores a project baseline in the browser; the Saved Projects view can reopen or delete saved projects.
- **Session snapshots** can be named, listed, restored, or deleted. Snapshots are available for projects that have first been saved.
- **Autosave and recovery** use browser `localStorage`. The editor schedules a quick save after an edit, an idle save, and a failsafe save; it also attempts to save when the page is hidden or leaving. A recoverable session is offered on the next startup.
- Storage availability is controlled by the browser. If browser storage is full or cleared, autosave or local saved-project data may be unavailable.

### Extra Tools feature pack

Open **Extra → Extra Tools** for these ten additional tools and one bonus:

1. **Animation tags:** create, update, delete, select, and play named frame ranges in forward, reverse, or ping-pong order.
2. **Layer blend and lock:** seven blend modes and protection against painting on the active layer.
3. **Color wheel and harmonies:** choose a hue and generate complementary, analogous, triadic, split, tetradic, square, or monochrome swatches.
4. **Shading ink:** paint through the current palette from the nearest matching color, choosing darker/lighter direction and a 1–4 step increment.
5. **Dither brush:** ordered dithering with Bayer 2×2, Bayer 4×4, Bayer 8×8, or checker pattern and 1–100% coverage.
6. **Advanced selection:** replace/add/subtract/intersect selection modes, plus opaque-content, select-all, and deselect utilities.
7. **Pixel rotate/scale:** apply an angle from −180° to 180° and scale from 10% to 400%; includes 90°, −90°, and 180° presets and nearest-neighbor resampling. The selection stays centered and is cropped if the canvas boundary requires it.
8. **Seamless tiled canvas:** show a repeating 3×3 preview while drawing; it does not alter exported pixels.
9. **Tile stamps / tileset brush:** capture a selection whose width and height are multiples of a tile size from 2–64 pixels, deduplicate identical tiles, choose a tile, and stamp it on the grid.
10. **Palette-lock drawing:** constrain foreground colors to the active document palette, or snap the current foreground color to its nearest palette color. The document remains RGBA.
11. **Bonus custom pattern brushes:** capture a selection as a stamp brush, preserve transparent pixels, and reuse it during the current browser session.

The current implementation persists selected Extra Tools settings in browser storage. Captured custom brushes and tiles are in-memory session data.

### Themes, language, and interface

- Seven themes: **Dark, Light, Game Boy, Arcade, NES, Synthwave,** and **Cozy**.
- Four interface languages: **English, Indonesian, Spanish,** and **Japanese**.
- Theme and language choices are stored in the browser.
- Tooltips and contextual hints describe controls; key controls receive accessible labels where provided by the interface. The Extra Tools panel switches to a single-column layout on narrower screens and is hidden at very narrow viewport widths.

## Keyboard shortcuts

| Shortcut | Action |
| --- | --- |
| `B`, `E`, `G`, `I`, `L`, `R`, `O`, `M`, `V`, `S` | Brush, Eraser, Fill, Picker, Line, Rectangle, Ellipse, Select, Move, Pan. |
| `1`–`5` | Set brush size. |
| `[` / `]` | Decrease/increase brush size. |
| `Alt`+click | Pick a color. |
| `Space`+drag | Pan the canvas. |
| Shift while dragging | Constrain the current drawing gesture where supported. |
| `0` | Zoom to 100%. |
| Mouse wheel, `+` / `−` | Zoom in/out. |
| `F` | Fit canvas to screen. |
| `X` | Swap foreground/background colors. |
| `Ctrl`+`Z`, `Ctrl`+`Y`, `Ctrl`+`Shift`+`Z` | Undo; redo. |
| `Ctrl`+`C`, `Ctrl`+`X`, `Ctrl`+`V` | Copy, cut, paste. |
| `Ctrl`+`A`, `Ctrl`+`D`, `Delete` / `Backspace` | Select all, deselect, delete selection. |
| `Enter` | Toggle animation playback. |
| `,` / `.` | Previous/next frame. |
| `Shift`+`O` | Toggle onion skin. |
| `#` | Toggle pixel grid. |
| `P` | Toggle floating preview. |
| `T` | Toggle timeline panel. |
| `Ctrl`+`N`, `Ctrl`+`O`, `Ctrl`+`E` | New sprite, open project, export. |
| `Ctrl`+`S`, `Ctrl`+`Alt`+`S` | Save project, save session snapshot. |
| `Ctrl`+`Shift`+`I` | Open image import. |
| `?` / `F1` | Show the keyboard-shortcuts dialog. |

## Import/export format reference

The Universal Format I/O registry currently enables both import and export (`rw`) for the following 15 project/interchange entries. “Both” means Fossprite implements a reader and writer for the documented subset below; it does not imply lossless round-tripping of every external-app feature.

| Format | Extensions | Implemented scope and caveats |
| --- | --- | --- |
| Aseprite | `.aseprite`, `.ase` | RGBA8 layered animation and standard pixel layers; tags where represented by the parser. Import uses the embedded Aseprite parser; export uses Fossprite’s writer. |
| Adobe Photoshop | `.psd` | RGB/8-bit compatible layered PSD. Group layers and unsupported color modes are rejected. |
| OpenRaster | `.ora` | RGBA PNG layers, `stack.xml`, layer offsets, visibility, and opacity. |
| Sprite Sheet + JSON | `.png`, `.json` | Aseprite-style JSON hash/array metadata; untrimmed, non-rotated frames. PNG and JSON are paired assets. |
| Godot 4 SpriteFrames | `.tres` | Text SpriteFrames resource with a sibling PNG atlas. Binary `.res` is explicitly rejected. |
| GraphicsGale | `.gal` | GAL v1.03–v1.07, single-frame 32-bpp subset, raw/zlib paths. JPEG-block decoding is rejected. |
| Pixelorama | `.pxo` | ZIP-based PXO v7 and compatible v6 RGBA8 pixel-layer projects; standard pixel layers and common blend modes. |
| Pixilart | `.pixil` | Pixilart 2.x embedded-PNG layer projects; source-over blend subset. |
| Pyxel Edit | `.pyxel` | `docData.json` and layer-PNG package subset used for raster/tile-animation projects. |
| Pixaki | `.pixaki` | Pixaki v2 package subset: `DocumentInfo.plist` and `Layer[GUID].png`. |
| Piskel | `.piskel` | `modelVersion` 2 chunk layout with raster animation frames. |
| Paint.NET | `.pdn` | Classic PDN3 metadata and 32-bpp raster surfaces; animations are reduced to the first frame. |
| Pixel Studio Project | `.psp` | Pixel Studio Pro v2 JSON projects with embedded source-PNG layers. |
| GIMP XCF | `.xcf` | 8-bit RGBA layers; groups and effects outside the supported subset are rejected. |
| VOX / MagicaVoxel | `.vox` | VOX 150 XYZI/RGBA-compatible 2D↔voxel projection; export emits one Z plane. |

The format hub also exports the raster/vector image formats **PNG, JPG, WebP, GIF,** and **SVG**. PNG/JPG/WebP/SVG are current-frame outputs; GIF contains the animation. Other browser-decodable raster images can be imported through the image-conversion workflow.

### Format and storage safeguards

- ZIP-based formats validate archive paths and structure. Archive processing is limited to 512 entries, 64 MiB per entry, and 192 MiB total unpacked data.
- Format parsers validate dimensions, frame/layer structures, and format-specific subsets. Some formats or codecs reject unsupported modes or structures rather than silently claiming full support.
- Large canvases and projects consume browser memory; practical capacity depends on the device and browser. Browser local storage quotas also apply to saved projects and snapshots.

## Offline architecture

Codec sources are embedded in `window.PF_VENDOR_SRC` as Base64 and decoded into in-memory Blob URLs only when needed. The repository adds no runtime dependency, remote import, CDN, API, or server requirement. The two namespace URLs in the HTML are document-format identifiers (W3C SVG and Apple plist DTD), not runtime network dependencies.

The format implementation also exposes internal diagnostic helpers for the format registry and its static checks. These are implementation/testing hooks, not a promise of a stable public JavaScript API.

## Licensing scope

This distribution contains both original Fossprite code and third-party software. **Original Fossprite code is offered under the MIT License to the extent that its copyright holder can be established.** The original Fossprite copyright holder is currently **UNVERIFIED** because no copyright-holder identity was supplied with the source.

Third-party code remains under its respective license. The root [`LICENSE`](LICENSE) file must not be read as relicensing the entire `index.html`; see [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) and the complete texts in [`licenses/`](licenses/).

The application already includes the relevant attribution in its About dialog, including DogSprite by systemcrash92 and Simple Pixel Art by comficker. Those notices are intentionally preserved.

## Repository contents

- `index.html` — the Fossprite application and its embedded Base64 vendor sources.
- `README.md` — project overview and the feature/format inventory above.
- `LICENSE` — MIT text scoped to original Fossprite code only; the original holder is marked unverified.
- `THIRD-PARTY-NOTICES.md` — provenance, versions, license expressions, evidence, and remaining uncertainties.
- `NOTICE` — distribution notice and scope clarification.
- `licenses/` — full license texts for the licenses identified during the audit.

## Audit status

The audit is **PARTIALLY VERIFIED — UNVERIFIED ITEMS REMAIN**. The bundled package headers and official package metadata establish the principal versions and licenses listed in `THIRD-PARTY-NOTICES.md`. Exact versions for the embedded `unenv` buffer shim and its `ieee754` component were not present in the decoded source and are therefore not guessed.

This repository is documentation-ready for review, but the audit status is deliberately not a claim of universal legal compliance.

## Source integrity

`index.html` remains a single HTML file and retains the embedded vendor source and existing attribution. The current working tree includes the requested cleanup to its comments and header branding. Reproduce the SHA-256 of the current file with:

```sh
sha256sum index.html
```

The checksum changes whenever the source changes; it is not a claim that the current file is byte-for-byte identical to an earlier audited copy.
