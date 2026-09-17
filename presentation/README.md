# Presentation sources

Two decks, ten slides each, 16:9.

| File | Use |
|---|---|
| `slides.pdf` | Dark. For the room and a dark projector |
| `slides-bright.pdf` | Bright. For print or a light projector |
| `slides.html` | **Editable source** for the dark deck |
| `slides-bright.html` | **Editable source** for the bright deck |

## Editing

Open either `.html` in any editor. Each slide is one `<section class="slide">`. The palette is the
token block at the top of the `<style>` element; changing the four values there restyles the whole
deck.

The typefaces are Newsreader and Libre Franklin, embedded as base64 inside the file, which is why the
sources are around 1.8 MB. That is deliberate: it means the deck renders identically on any machine
with no font installation and no network.

## Re-rendering to PDF

```bash
google-chrome --headless=new --disable-gpu --no-pdf-header-footer \
  --virtual-time-budget=20000 \
  --print-to-pdf=presentation/slides.pdf \
  "file://$PWD/presentation/slides.html"
```

Repeat with `slides-bright.html` for the bright variant. Any Chromium build works. Check the result
with `pdfinfo slides.pdf`, which should report ten pages at 960 by 540 points.

## Keeping the two in step

Edit `slides.html` first, then copy the change into `slides-bright.html`. Only four things differ
between them: the four palette tokens, the dashed-ring opacity, the footer colour and the tinted
panel background.

## The logo

Vector assets are in `logo/`, with the specification in `logo/README.txt`. The mark is drawn inline
as SVG in the deck sources, so it needs no external file.
