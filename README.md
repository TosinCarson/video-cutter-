# Clip Cutter

A browser tool for cutting haircut tutorial videos into clips.

1. Open `index.html` from a web address (GitHub Pages, or a local server such as `python3 -m http.server`). Double-clicking the file won't work, because the video engine only loads over http(s).
2. Drop in a video (MP4, MOV or WebM, up to about 150 MB).
3. Press **I** where a section starts and **O** where it ends to add a clip. Name, adjust, reorder or delete clips in the list.
4. Tick the clips you want and export them as separate files or as one joined video.

Cutting runs in your browser with [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm), so videos are never uploaded. The first visit downloads the engine (about 31 MB) from jsDelivr, and the browser caches it after that.

**Cut quality**

- **Fast:** copies the original video, so it takes seconds and keeps full quality. Cuts snap to the nearest keyframe, so a clip can start up to about a second early.
- **Frame-accurate:** re-encodes to H.264/AAC MP4. Cuts land exactly where you marked, but it's slower.

**Shortcuts:** Space play/pause · ←/→ 1 s · Shift+←/→ 5 s · `,`/`.` one frame · I start · O end · Esc clear start
