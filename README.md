# Clip Cutter

A browser tool for cutting videos into clips.

1. Open `index.html` from a web address (GitHub Pages, or a local server such as `python3 -m http.server`). Double-clicking the file won't work, because the video engine only loads over http(s).
2. Drop in a video (MP4, MOV or WebM, up to about 150 MB).
3. Add clips either way:
   - Press **I** where a section starts and **O** where it ends.
   - Type times into **Add clips by time**, for example `1:14-1:28 Intro, 2:16-2:29 Step one`. Use commas or new lines between clips; the name is optional.

   Name, adjust, reorder or delete clips in the list, or drag a clip's edges on the timeline to trim it. Zoom the timeline with + and − (or Ctrl/⌘ + scroll) for fine cuts.
4. Tick the clips you want and export them as separate files or as one joined video.

Cutting runs in your browser with [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm), so videos are never uploaded. The first visit downloads the engine (about 31 MB) from jsDelivr, and the browser caches it after that.

**Stills**

Grab full-resolution images from your video and browse them in the **Stills** tab.

- Press **S** or **Grab frame** to add the frame you're on.
- On the Stills tab, drag any point on the timeline up into the grid to add it as a still. Slide along the timeline first to fine-tune the moment; once you move up, it's locked. Double-clicking the timeline or **+ Add still at** also works.
- **Hide timeline** (or **T**) gives the video or the gallery the full height.
- To grab many at once, tick clips, choose **Stills** under Export as, and pick either a set number per clip or a number per second (up to every frame). Choose PNG (lossless, the default) or JPEG (97% quality, smaller). **Pick the sharpest nearby frame** (on by default) checks up to 3 frames either side of each moment and keeps the least blurry one.
- In the gallery, click a still to view it full size (←/→ to flip through, X to select, D to download, Z or click to toggle 100% zoom). Select stills individually, with Shift-click for a range, or a whole group at once, then download one, the selection, or everything. More than one comes as a ZIP.
- Stills use the same aspect ratio and framing as video exports. They live in the page until you close or reload it, so download the ones you want to keep.

**Aspect ratio**

Export as Original, 9:16, 4:5, 1:1 or 16:9. **Crop to fill** trims the picture; drag the frame on the preview to choose what stays in the shot. **Fit with bars** keeps the whole picture and adds black bars. Either one re-encodes the video.

**Export quality**

- **Original:** copies the video as it is, so it takes seconds with no quality loss. Cuts snap to the nearest keyframe, so a clip can start up to about a second early.
- **High, 1080p, 720p, 480p:** re-encode to H.264/AAC MP4 with frame-accurate cuts. The resolution applies to the short side, so a vertical video at 720p comes out 720×1280. Videos are never upscaled. Re-encoding is much slower than Original.

**Shortcuts:** Space play/pause · ←/→ 1 s · Shift+←/→ 5 s · `,`/`.` one frame · I start · O end · Esc clear start · +/− zoom timeline
