# PixConvert

**Convert images instantly. Free, private, no upload.**

A browser-based image format converter that runs entirely client-side. Your images never leave your device.

🔗 **[Try it live →](https://mack-moneymaker.github.io/pixconvert/)**

## Features

- **6 output formats** — PNG, JPG, WEBP, GIF, BMP, ICO
- **Batch conversion** — Convert up to 10 images at once (unlimited with Pro)
- **ZIP download** — Download all converted files in one click
- **Resize** — Optional width/height with aspect ratio lock
- **Quality control** — Adjustable for JPG and WEBP
- **100% private** — No server, no uploads, no tracking, no analytics
- **Works offline** — Once loaded, no internet needed
- **Open source** — Single HTML file, no build step

## How It Works

PixConvert uses the browser's native Canvas API to decode and re-encode images. Everything happens in-memory on your device. There is no backend.

1. Drop or select images
2. Choose output format, quality, and optional resize
3. Click **Convert All**
4. Download individually or as a ZIP

## Tech Stack

- Vanilla HTML/CSS/JS — single `index.html` file
- Canvas API for image processing
- [JSZip](https://stuk.github.io/jszip/) (lazy-loaded from CDN) for ZIP generation
- GitHub Pages for hosting

## Pro Tier

For power users who need more:

| | Free | Pro ($3/mo) |
|---|---|---|
| Batch size | 10 images | Unlimited |
| HEIC/HEIF input | ❌ | ✅ |
| Branding | PixConvert | Removed |

## Development

No build step required. Just open `index.html` in a browser or serve it:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

## Related Tools

- [Faviconify](https://mack-moneymaker.github.io/faviconify/) — Favicon generator
- [SigCraft](https://sigcraft.dev) — Email signature builder
- [GradientLab](https://mack-moneymaker.github.io/gradientlab/) — CSS gradient generator
- [ColorCraft](https://mack-moneymaker.github.io/colorcraft/) — Color palette tool
- [JSONPretty](https://mack-moneymaker.github.io/jsonpretty/) — JSON formatter
- [CronMaker](https://mack-moneymaker.github.io/cronmaker/) — Cron expression builder
- [RegexLab](https://mack-moneymaker.github.io/regexlab/) — Regex tester

## License

MIT
