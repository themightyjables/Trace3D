# Trace3D

Turn photos of your tools into a custom [Gridfinity](https://gridfinity.xyz/) bin, right in your browser.

Photograph objects on a sheet of paper, trace their outlines, arrange them together, and download a single printable STL or 3MF with a pocket for each one. Everything runs client-side in one HTML file; nothing is uploaded anywhere.

**Live tool:** https://YOUR-SITE-NAME.netlify.app

---

## How it works

1. **Add photos.** Lay one or more objects flat on a sheet of paper (letter, legal, A4 or a custom size) and photograph from above. All four corners of the sheet must be visible. You can add as many photos as you like.
2. **Calibrate.** Click the four corners of the paper, in any order. The tool uses them to compute a perspective correction, so a photo taken slightly off-angle still measures true.
3. **Trace objects.** Click around each object's outline. Every object gets its own pocket. Objects from different photos can all go into the same bin.
4. **Arrange.** Drag and rotate objects on the layout, or use Auto-arrange to pack them into the fewest grid cells. Add thumb holes (standard 25mm circles) wherever you need finger room.
5. **Export.** Preview the bin in 3D, then download it as STL or 3MF.

## Features

- **Paper calibration with perspective correction**, accurate to within about 0.1% in testing
- **Multiple objects per photo and multiple photos per bin**, each object in its own pocket with a divider between them
- **Exact cutouts:** the traced outline is the pocket, with no clearance added
- **Thumb holes:** standard circles you drag into place; overlapping holes merge into one larger cutout
- **Live layout checks:** pockets turn red when closer than the divider thickness
- **Build plate warnings** for Bambu Lab, Prusa and Creality printers (or a custom size), checked live as the bin grows
- **Standard Gridfinity geometry** on every bin:
  - 42mm grid, 42n − 0.5mm footprint, 3.75mm corner radius
  - Spec foot profile on every cell (0.8mm 45° / 1.8mm vertical / 2.15mm 45°, 4.75mm total)
  - Stacking lip inside the footprint, so bins sit side by side in a baseplate
  - Height in standard 7mm units
- **STL and 3MF export**, Z-up and ready for Bambu Studio, OrcaSlicer or PrusaSlicer. The 3MF opens centered on the selected build plate.

## Tips for accurate results

- **Use zoom when clicking.** The zoom buttons above the photo let you place each corner and trace point precisely.
- **Keep the paper flat** on a hard surface, with a dark background so its corners stand out.
- **Shoot from arm's length or farther.** Distance reduces perspective effects on tall objects.
- **Trace tall objects where they meet the paper**, not at their outermost visible edge. The top of a tall object is closer to the camera and photographs larger than it really is.
- **Trace on the edge for an exact fit**, or slightly outside it for a looser one.
- **Print a small test bin first** to check the fit in your baseplate before committing to a large print.

## Known limitations

- Perspective correction applies to the plane of the paper. Tall objects can still photograph slightly larger at their top edge (see tips above).
- All pockets in a bin are cut to the same depth.
- No magnet or screw holes in the base yet.

## Running it

There's nothing to build or install. Open `index.html` in any modern browser, or host it on any static web host. It loads three.js r128 and polyclip-ts from public CDNs, so it needs an internet connection.

## Tech

- [three.js](https://threejs.org/) r128: 3D preview, geometry and STL export
- [polyclip-ts](https://github.com/luizbarboza/polyclip-ts): polygon union and clipping for pockets and thumb holes
- 3MF writer built in, with no extra library
- Single self-contained HTML file, hosted on Netlify
