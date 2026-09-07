# structure-svelte

Static marketing site for Structure Fab & Design, built with SvelteKit + `adapter-static`.
Port of the old `structure-react` Create React App.

## Develop

```bash
npm install
npm run dev
```

## Build

```bash
npm run build
```

Outputs a fully static site to `build/` — no server code. Preview it locally with `npm run preview`.

## Deploy (Railway)

Connect this repo to a Railway service. Railway builds with `npm run build` and serves the
static `build/` output; no Procfile or server is needed.

## Notes

- Section backgrounds go through `src/lib/components/BackgroundMedia.svelte` — it switches to
  the mobile GIF at <=768px, and pass it an `.mp4`/`.webm` import instead of a `.gif` and it
  renders an autoplaying looped video. Converting the large GIFs (~80MB desktop / ~30MB mobile)
  to video is the biggest pending optimization.
