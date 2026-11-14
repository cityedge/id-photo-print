# ID Photo Print — User Manual

**Version:** 1.0.0  
**Recommended environment:** Google Chrome on Windows with a properly configured printer.

## 1. Overview

ID Photo Print converts a photo taken on a phone or camera into an ID-photo-sized crop, adjusts its appearance, lays out copies on a sheet, and opens Chrome's print dialog. It does **not** require a PDF export, account, upload, or installation.

The left panel has three tabs: **Photo / rotate**, **Retouch**, and **Paper / layout**. The middle column contains the crop editor. The right column previews the print sheet. The print button and job status stay in the top header on desktop.

## 2. Open and import a photo

1. Open `index.html` in Chrome, or visit your published GitHub Pages site.
2. Click the upload area or drag and drop a JPG, PNG, WebP, or BMP image (maximum 100MB).
3. Choose a photo size: 30×40mm, 35×45mm, 25×30mm, 40×50mm, 50×50mm, or custom dimensions.
4. Drag the crop preview to move the subject, and adjust zoom using the slider (100–350%) or mouse wheel.
5. Use the 90° rotation buttons or the straightening slider (−15° to +15°) if required. The application automatically compensates for empty corners when rotating.

## 3. Retouch

Use the **Retouch** tab to adjust brightness (midtones), contrast, color temperature, and sharpness. Original image files are not modified. Changes affect both screen previews and printing.

| Setting | Range | Purpose |
| --- | --- | --- |
| Brightness (midtones) | −50 to +50 | Gamma-like control for under- or overexposed faces |
| Contrast | −50 to +50 | Increase or reduce tonal separation |
| Color temperature | −50 to +50 | Move toward cooler blue or warmer red; this is a relative control, not a Kelvin value |
| Sharpness | 0 to 100 | Edge enhancement; avoid excessive sharpening |

The **Reset all adjustments** button restores the four sliders to zero. Official ID and passport photo requirements may limit retouching; check the issuing authority's rules.

## 4. Paper and layout

| Setting | Options / defaults |
| --- | --- |
| Paper | L photo (89×127mm), 2L photo (127×178mm), Postcard (100×148mm), A4 (210×297mm), custom |
| Orientation | Portrait / landscape; portrait by default |
| Application paper margin | **12mm by default** (adjustable 3–30mm) |
| Gap between photos | 3mm by default (adjustable 0–30mm) |
| Auto placement | Enabled by default |
| Maximum copies for auto placement | 4 (default), 9, 16, or Unlimited |
| Manual copies | Available when auto placement is disabled; limited by physical capacity |
| Position | Center, Top center, Top left |
| Cut guides | Corner crop marks, a thin outline, or None |

The application groups photos compactly when possible (e.g., 4 as 2×2 or 9 as 3×3). **Top left** starts after the specified margins, rather than at the absolute edge of the paper.

**Important:** The application's 12mm paper margin is a design margin *inside the sheet*. It is separate from Chrome's print dialog margin setting.

## 5. Print using Chrome

1. Confirm the paper preview and click **Print directly from Chrome**.
2. Select the printer and the physical paper size and orientation matching the application.
3. Set **Scale: 100% / Actual size**; turn off any fit-to-paper scaling.
4. Set **Margins: None** and turn off **Headers and footers**.
5. Disable the printer driver's **borderless enlargement** feature. Use non-borderless printing and cut the photos afterward.
6. Select the appropriate paper media and quality in your printer driver. Confirm that the job is one page, then print.

If the physical dimensions matter, measure a test print with a ruler. The browser and printer driver may introduce scaling errors; the application does not control driver settings or automatically calibrate the printer.

## 6. 600dpi output

The application creates the cropped photo at a **fixed 600dpi-equivalent resolution** for normal ID photo sizes: approximately 709×945 pixels for 30×40mm, or 827×1063 pixels for 35×45mm. A low-resolution source will not gain detail merely by upscaling. Very large custom sizes are subject to a browser-memory safety limit.

## 7. Saved settings and privacy

The application automatically stores preferences in the browser's `localStorage`: language, last selected tab, photo size, paper, orientation, margins, gaps, placement, copy limit/manual count, and cut guides.

For the **last edited photo only**, it also saves a compact file identifier and the crop, zoom, rotation, straightening, and retouch values. **No photo file or photo pixels are persisted.** After reopening the app, reselect the original photo. If it is the same file, the saved editing values are restored; a different photo starts with neutral editing values.

Storage belongs to the browser and site origin. Private mode, clearing site data, switching browsers, or using a different URL can prevent restoration. Storage for local `file://` pages is browser-dependent; a stable GitHub Pages URL is recommended for repeat use. If storage access is blocked, a warning is shown and printing remains available.

All image processing happens locally in the browser. No images are uploaded; no external API or JavaScript library is used.

## 8. Troubleshooting

- **Print button disabled:** Import a valid photo and make sure at least one copy fits the paper.
- **Cannot open photo:** Convert HEIC, TIFF, or RAW images to JPG or PNG; those formats are not supported directly.
- **Print is too large/small:** Check 100% scale, paper size, and printer driver scaling.
- **Photo is clipped or soft:** Adjust crop and zoom; verify source resolution.
- **Settings not restored:** Use the same browser and URL; check site data and private browsing settings.
- **Unexpected extra pages or headers:** Match paper size and orientation, and disable Chrome's headers and footers.

## 9. License

MIT License — Copyright (c) 2026 cityedge. See [LICENSE](LICENSE).
