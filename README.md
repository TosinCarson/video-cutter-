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

**Export quality**

- **Original:** copies the video as it is, so it takes seconds with no quality loss. Cuts snap to the nearest keyframe, so a clip can start up to about a second early.
- **High, 1080p, 720p, 480p:** re-encode to H.264/AAC MP4 with frame-accurate cuts. The resolution applies to the short side, so a vertical video at 720p comes out 720×1280. Videos are never upscaled. Re-encoding is much slower than Original.

**Shortcuts:** Space play/pause · ←/→ 1 s · Shift+←/→ 5 s · `,`/`.` one frame · I start · O end · Esc clear start · +/− zoom timeline
