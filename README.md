# Spatial Transcriptomics Viewer

Single-file web app to view a DAPI image, optional segmentation mask, transcript points, and polygon ROIs.

**Open the app:** https://sedzinski-lab.github.io/spatial-transcriptomics-viewer/

---

## What it does
- Load **DAPI** (`.tif/.tiff`, `.png`, `.jpg`)
- Optional **mask** (`.tif/.tiff` or `.png`; label image or RGB-coded)
- Load **transcripts** (`x,y,z,gene[,score]` as TXT/TSV/CSV)
- Add multiple **gene layers** (color, size, opacity)
- **Pan / zoom / rotate** view (rotation is visual only)
- Draw **polygon ROIs**, set **cell types** (dropdown + “Other…”)
- **Export JSON** and **Export CSV (wide)** for analysis

> Coordinates and ROI testing are always in the **unrotated image space**.

---

## Quick start
1. Open: https://sedzinski-lab.github.io/spatial-transcriptomics-viewer/
2. Load **DAPI** → optional **mask** → **transcripts**.
3. Pick a gene → **Add Gene Layer**.
4. **Draw** ROI: click points → **double-click** to finish.
5. Select ROI in the list → set **Cell type**.
6. Export with **Export JSON** or **Export CSV**.

---

## Buttons & controls (what everything does)

### Files
- **DAPI image**: loads background image. 16-bit TIFFs are auto contrast-stretched (2–98%).
- **Segmentation mask**: overlays colored regions (fill and/or edges). Must share the same pixel grid as DAPI.
- **Transcripts**: loads points. Delimiters can be comma or tab; header optional.

### Gene layers
- **Select gene**: choose a gene from the loaded transcripts.
- **Add Gene Layer**: creates a layer for the selected gene with its own color/size/opacity.
- **Default size / Default opacity**: sliders that set defaults for newly added layers.
- Per-layer row:
  - **Color swatch**: changes the layer color (stored as `#RRGGBB`).
  - **Hide/Show**: toggles layer visibility.
  - **Size**: point radius in pixels (scales with zoom).
  - **Opacity**: layer alpha.

### Mask overlay
- **Show fill**: toggle filled colored regions.
- **Show edges**: toggle white label boundaries.
- **Mask opacity**: slider for fill transparency.

### Annotations (ROIs)
- **Draw**: enter/exit polygon-draw mode.
- **Complete**: closes the current polygon (enabled after 3+ vertices).
- **Cancel**: cancels the current polygon.
- **ROI list (per row)**:
  - **Cell type**: dropdown of presets (`MCC, Goblet, IC, Basal, SSC`) plus **Other…** to enter a custom type.
  - **Rename**: set a friendly ROI name.
  - **Delete**: remove ROI.
  - Row click: selects the ROI. Selected ROI is highlighted on the image.
 
### View
- **Reset View**: fits the image to the canvas and sets rotation to 0° (rotation is visual only).

---

## Mouse & keyboard

- **Zoom**: mouse wheel (zooms at cursor position).
- **Pan**: click-drag on the image (when not drawing).
- **Rotate**: hold **R** and drag; rotation is around the image center.  
  Counts and ROI tests ignore rotation (purely visual).
- **Draw ROI**: click points; **double-click** to finish.
- **Select ROI**: click ROI on the image or click its row.
- **Esc**: cancel drawing.
- **Delete/Backspace**: delete selected ROI.
- **T**: focus the cell-type dropdown for the selected ROI.
