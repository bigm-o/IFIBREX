# iFibreX — coming soon

Production coming-soon page for **www.ifibrex.com**. Static files only: no build step, no dependencies, no third-party requests.

```
index.html            the page (styles and scripts inline)
assets/
  fonts/              Montserrat 600–700 and Inter 400–500 (Latin, WOFF2, self-hosted)
  ifibre-logo.png     header logo (640 px, 2x its display size)
  favicon.png, apple-touch-icon.png
media/
  intro.webm|mp4      2 s build-up: the map fades in while the cable bundles draw in (plays once)
  hero-loop.webm|mp4  4 s seamless loop of light through the network
  intro-poster.webp   first frame of the intro (preloaded)
  hero-poster.webp    finished scene: shown if video can't autoplay, or with reduced motion
  og-image.jpg        1200x630 social share card
data/overlay.js       cable paths for the interactive pulse layer (hover or tap the map)
robots.txt            keeps /archive/ out of search engines
archive/              earlier design options, kept for reference (noindex)
  option-1/           live three.js junction block
  option-3/           Blender-rendered fibre cables
```

## Behaviour

- The intro plays once, then hands off to the loop on the next frame.
- If autoplay is refused (for example, a phone in battery-saver mode), the finished scene shows as a still. There's never a play button.
- If the intro hasn't started within 3 s on a slow connection, it's skipped.
- With reduced motion enabled, the still shows and the copy appears without animation.

## Page weight

9 requests, about 950 KB in total, all served by this site. Everything before the videos (HTML, fonts, logo and the first frame) is about 130 KB.

## Deploy

Upload the folder as-is to any static host.

- **GitHub Pages:** Settings → Pages → Deploy from a branch → `main` / root.
- **Custom domain:** add a `CNAME` file containing `www.ifibrex.com`, then point the domain's DNS at the host.

The canonical URL and social card URLs in `index.html` assume `https://www.ifibrex.com/`. Update them if the page is served elsewhere.

## Source files

The renders, Blender scripts and encode scripts live outside this repo:

- `coming-soon-v2/`: this page (`intro.py` builds the intro, `encode_v3.sh` encodes it).
- `coming-soon/` and `coming-soon-v3/`: the archived options.
