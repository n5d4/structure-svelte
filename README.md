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

- Section backgrounds go through `src/lib/components/BackgroundMedia.svelte`: autoplaying
  looped H.264 MP4s (converted from the original ~110MB of GIFs down to ~6.6MB), with mobile
  variants swapped in at <=768px. It also accepts `.gif`/image imports, rendered as a cover
  background instead.
