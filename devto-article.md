# I Built a Free Image Converter That Never Uploads Your Files

Ever used an online image converter and wondered where your files actually go?

Most "free" converters quietly upload your images to their servers. Your screenshots, photos, design mockups — sitting on someone else's infrastructure. Maybe they delete them. Maybe they don't. You'll never really know.

That bugged me, so I built **[PixConvert](https://mack-moneymaker.github.io/pixconvert/)** — an image converter that runs 100% in your browser. Your files never leave your machine. There's no backend. No upload. No server. Just the Canvas API doing its thing.

## What It Does

- **Format conversion:** PNG, JPG, WEBP, GIF, BMP, ICO
- **Batch support:** Drop multiple files at once, convert them all in one click
- **Quality slider:** Fine-tune compression for JPG and WEBP output
- **Resize:** Set custom dimensions before converting
- **Instant download:** Files are processed and ready immediately

## How It Works (The Nerdy Part)

The entire tool is a **single HTML file**. No frameworks, no dependencies, no build step.

Here's the core idea:

1. You drop an image → it's read with `FileReader` as a data URL
2. The image is drawn onto an off-screen `<canvas>` element
3. `canvas.toBlob()` exports it in your chosen format
4. You download the blob

That's it. The Canvas API handles all the heavy lifting — format encoding, quality control, resizing. The browser is genuinely good at this stuff, and there's no reason to involve a server.

```javascript
// The essence of PixConvert in ~10 lines
const img = new Image();
img.onload = () => {
  const canvas = document.createElement('canvas');
  canvas.width = img.width;
  canvas.height = img.height;
  canvas.getContext('2d').drawImage(img, 0, 0);
  canvas.toBlob(blob => {
    // Download the converted file
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = `converted.${format}`;
    a.click();
  }, `image/${format}`, quality);
};
img.src = fileDataUrl;
```

## Why "No Upload" Matters

It's not just about privacy (though that's reason enough). Running locally means:

- **Speed** — no upload/download wait time, especially on slow connections
- **No file size limits** — your browser can handle large images just fine
- **Works offline** — once loaded, it doesn't need the internet
- **No account required** — no signup, no email, no cookies

## Try It / Star It

🔗 **Live tool:** [mack-moneymaker.github.io/pixconvert](https://mack-moneymaker.github.io/pixconvert/)
⭐ **GitHub:** [github.com/mack-moneymaker/pixconvert](https://github.com/mack-moneymaker/pixconvert)

It's fully open source. If you find it useful, a star on GitHub would mean a lot. Got feedback or feature ideas? Open an issue — I'd love to hear what you'd add.

---

## 🧰 More Free Dev Tools

PixConvert is part of a growing collection of free, open-source tools — all client-side, no signup:

- **[SigCraft](https://mack-moneymaker.github.io/sigcraft/)** — Email signature generator with templates, photo upload, and social icons
- **[Faviconify](https://mack-moneymaker.github.io/faviconify/)** — Generate favicons from text, emoji, or images (PNG + ICO)
- **[GradientLab](https://mack-moneymaker.github.io/gradientlab/)** — CSS gradient generator with live preview and PNG export
- **[ColorCraft](https://mack-moneymaker.github.io/colorcraft/)** — Color palette generator with harmony modes and accessibility checker
- **[RegexLab](https://mack-moneymaker.github.io/regexlab/)** — Clean regex tester with match highlighting and cheat sheet
- **[CronMaker](https://mack-moneymaker.github.io/cronmaker/)** — Visual cron expression builder and decoder
- **[JSONPretty](https://mack-moneymaker.github.io/jsonpretty/)** — JSON formatter, validator, and diff tool
- **[HookDebug](https://mack-moneymaker.github.io/hookdebug/)** — Webhook testing and inspection tool
- **[JustTheRecipe](https://mack-moneymaker.github.io/justtherecipe/)** — Paste a recipe URL, get just the ingredients and instructions
- **[LegalPage](https://mack-moneymaker.github.io/legalpage/)** — GDPR-compliant Privacy Policy and Terms generator

All free. All open source. All on [GitHub](https://github.com/mack-moneymaker).
