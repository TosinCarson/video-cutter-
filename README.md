# Stills

A browser tool for grabbing full-resolution stills from videos, and cutting them into clips.

1. Open `index.html` from a web address (GitHub Pages, or a local server such as `python3 -m http.server`). Double-clicking the file won't work, because the video engine only loads over http(s).
2. Drop in a video (MP4, MOV or WebM, up to about 150 MB).
3. Add clips either way:
   - Press **I** where a section starts and **O** where it ends.
   - Type times into **Add clips by time**, for example `1:14-1:28 Intro, 2:16-2:29 Step one`. Use commas or new lines between clips; the name is optional.

   Name, adjust, reorder or delete clips in the list, or drag a clip's edges on the timeline to trim it. Zoom the timeline with + and − (or Ctrl/⌘ + scroll) for fine cuts.
4. Tick the clips you want and export them as separate files or as one joined video.

Your last video, your clip marks and your stills are kept in this browser's own storage, so they come back after a refresh. Close a video with the × next to its name if you don't want it reopened. Nothing is uploaded.

Cutting runs in your browser with [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm), so videos are never uploaded. The first visit downloads the engine (about 31 MB) from jsDelivr, and the browser caches it after that.

**Stills**

Grab full-resolution images from your video and browse them in the **Stills** tab.

- Press **S** or **Grab frame** to add the frame you're on.
- On the Stills tab, drag any point on the timeline up into the grid to add it as a still. Slide along the timeline first to fine-tune the moment; once you move up, it's locked. Double-clicking the timeline or **+ Add still at** also works.
- **Stills card** (bottom of the left panel): pick PNG or JPEG and whether to use the sharpest nearby frame; these apply to every still. Then set how many and whether to look at the whole video or the ticked clips.
  - **Random** grabs that many random moments, skipping black, blank, blurry or badly exposed frames. Select the ones you like and press **Shuffle again**: your selected ones stay and the rest are swapped for new moments.
  - **Best moments** picks the best few frames for you, from the whole video or just the ticked clips. It samples up to a few hundred frames, scores each for sharpness, steadiness, exposure, contrast and colour, keeps only the top-scoring ones, spreads them out in time and saves them full size in a "Best moments" group.
- Drag the inner edge of the Clips or Export panel to make it wider or narrower (double-click the edge to reset). Widths are remembered.
- Hide or show the Clips panel with the button next to the name (or **[**). Export settings open from **Export** in the top bar (or **]**). The **?** button lists every keyboard shortcut.
- **Hide timeline** (or **T**) gives the video or the gallery the full height.
- To grab many at once, tick clips, choose **Stills** under Export as, and pick either a set number per clip or a number per second (up to every frame). Choose PNG (lossless, the default) or JPEG (97% quality, smaller). **Pick the sharpest nearby frame** (on by default) checks up to 3 frames either side of each moment and keeps the least blurry one.
- In the gallery, click a still to view it full size (←/→ to flip through, X to select, D to download, Z or click to toggle 100% zoom). Select stills individually, with Shift-click for a range, or a whole group at once, then download one, the selection, or everything. More than one comes as a ZIP.
- Stills use the same aspect ratio and framing as video exports.

**Grade**

Give a set of images the same colour grade.

- Add stills (select them in the Stills tab and press **Grade**) or upload your own photos with **Upload images**, or drop image files onto the page.
- Start from a preset (Clean, Warm, Cool, Bright & airy, Moody, Film, Black & white) and adjust Light (exposure, contrast, highlights, shadows, whites, blacks), Colour (temperature, tint, vibrance, saturation), Split toning and Effects (fade, vignette, grain, sharpen). Double-click a slider's name to reset it.
- The look applies to every image in the set, including ones you add later. Hold **Hold to compare** (or **\\**) to see the original.
- **Even out exposure first** brings each image to a similar brightness before the look, which helps mixed lighting match.
- Save looks by name and reuse them later. Download one image, the selected ones, or all of them at full resolution (PNG or JPEG, from the Stills card setting). Originals are never changed.
- Grading runs on the graphics card (WebGL), so sliders update live. Images and looks are kept across refreshes.

**Remove captions**

For burned-in captions (ones you can't turn off). In the Stills card, press **Set area** and drag a box around where the captions appear on the video, then **Done**; **Remove captions** turns on. Every still you grab from then on is cleaned: the page finds the caption letters (near-white and brighter than the area around the box), fills them from moments up to 4 seconds away when that spot is uncovered, and fills anything left from the surrounding pixels. It works best on a still camera with captions over plain areas; each cleaned still takes a few seconds. In the viewer, hold **Hold: before** (or **O**) to compare with the captioned frame.

**Aspect ratio**

Export as Original, 9:16, 4:5, 1:1 or 16:9. **Crop to fill** trims the picture; drag the frame on the preview to choose what stays in the shot. **Fit with bars** keeps the whole picture and adds black bars. Either one re-encodes the video.

**Export quality**

- **Original:** copies the video as it is, so it takes seconds with no quality loss. Cuts snap to the nearest keyframe, so a clip can start up to about a second early.
- **High, 1080p, 720p, 480p:** re-encode to H.264/AAC MP4 with frame-accurate cuts. The resolution applies to the short side, so a vertical video at 720p comes out 720×1280. Videos are never upscaled. Re-encoding is much slower than Original.

**Shortcuts:** Space play/pause · ←/→ 1 s · Shift+←/→ 5 s · `,`/`.` one frame · I start · O end · Esc clear start · +/− zoom timeline
