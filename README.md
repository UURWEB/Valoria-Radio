# Valorianischer Nationalrundfunk — Sender Valor

A 1920s-style wireless radio station website for the Kingdom of Valoria. Fully static — works on GitHub Pages with no build step.

## Deploy to GitHub Pages

1. Create a new repository (e.g. `valor-station`).
2. Upload `index.html`, `flag.png`, and the `songs/` folder to the repository root.
3. Go to **Settings → Pages**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Your station goes on air at `https://<username>.github.io/valor-station/`.

## Adding songs

1. Drop your `.mp3` files into the `songs/` folder.
2. Open `index.html` and find the `SONGS` array near the top of the `<script>`:

```js
const SONGS = [
  { file: "songs/marsch.mp3", title: "Königlicher Marsch — Hoforchester" },
  { file: "songs/walzer.mp3", title: "Walzer Nr. 3 — Kapelle Valor" },
];
```

Songs play in random order with a short pause between them. If the array is empty, the apparatus plays aether static instead.

## Announcements

Two kinds, mixed at random:

**Recorded announcements** — drop audio files into the `announcements/` folder and list them in the `ANNOUNCEMENT_FILES` array (each with `file`, `de`, and `en` — the texts appear in the log while the recording plays).

**Spoken (TTS) announcements** — the entries in the `ANNOUNCEMENTS` array, read aloud in German by the browser.

`RECORDED_CHANCE` (default `0.6`) sets how often a recorded file is chosen over a spoken one. If one list is empty, the other is always used.

### Original announcement notes

Random spoken announcements (German, via the browser's speech synthesis) interrupt the music every 45 seconds to 2.5 minutes, duck the music volume, and are logged under "Letzte Durchsagen". Edit the `ANNOUNCEMENTS` array in `index.html` to add your own — each entry has a `de` and `en` text. Timing is controlled by `ANNOUNCE_MIN` / `ANNOUNCE_MAX`.

## Notes

- The **English** button in the top-right translates the whole page; spoken announcements remain in German (it is Valorian state radio, after all — the log translates).
- The displayed date is always today's date minus 100 years.
- Browsers block autoplay, so the listener must turn the power knob — which fits a 1926 receiver anyway.
