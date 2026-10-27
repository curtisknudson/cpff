# Flag Football Weekly

Static site for cpff.online. The live edition is the repo root. Older editions stay up in their own folders. Grok reads this file at the start of a session.

## What is live

- `index.html` is the current edition.
- `styles.css` is the current stylesheet. The live page links it as `/styles.css`.
- `og.png` is the current share card, 1200×630.
- `favicon.png` and `apple-touch-icon.png` are site-wide. Do not replace them when publishing an edition.
- `CNAME` is `cpff.online`. Do not change it.

## Archived editions

| Folder | Edition |
| --- | --- |
| `week-3/` | Week 3, the Investigative Edition. Self-contained: styles are inlined in `index.html`. Own `og.png`. |
| `weeks-4-5/` | Weeks 4 & 5, the Doubleheader Edition. Own `index.html`, `styles.css`, and `og.png`. |

The new edition's nav is the source of truth for the archive slug. Week 6 links the doubleheader to `/weeks-4-5/`.

## Publishing a new edition

A new edition arrives as `index copy.html` and sometimes `styles copy.css`. Promote it. Do not rewrite the article.

1. Read the new file's nav and use that path as the archive folder. Create the folder.
2. Move the current `index.html` into that folder. Point `canonical`, `og:url`, `og:image`, and `twitter:image` at the archive URL, including the trailing slash. Point the image URLs at the folder's own `og.png`.
3. Move the current `og.png` into that folder.
4. Copy the current `styles.css` into that folder and point the archived page at `styles.css` (relative). Do this even when the new stylesheet is identical, so a later CSS change does not restyle the archive. Week 3 is the exception: its CSS is already inlined, so leave it that way.
5. Replace root `index.html` with `index copy.html`. If `styles copy.css` differs from `styles.css`, replace `styles.css` with it. Then delete both copy files.
6. Keep the GoatCounter snippet in the new `<head>`. Also keep the site chrome the copy sometimes omits: `theme-color` `#17344b`, the favicon, the apple touch icon, `og:image:width` 1200, `og:image:height` 630, `og:image:alt`, and the `twitter:card` tags. Write the alt text from the new card.
7. On every older edition, change the nav's "Latest" link to the new edition at `/`. Add a link to the edition you just archived. If an older page has an in-body link to `/` that names a specific edition, point that link at the archive. Week 3's "Read the Weeks 4 & 5 Doubleheader Edition" link goes to `/weeks-4-5/`.
8. Build a new root `og.png` (below). Do not commit or push unless asked.

GoatCounter, kept on the live page and on archives:

```html
<script data-goatcounter="https://cpff.goatcounter.com/count"
        async src="//gc.zgo.at/count.js"></script>
```

## Open Graph card

Match the existing cards. Do not use an image model. The words and numbers have to be exact, and image models garble them. Render HTML at 1200×630 and screenshot it.

Colors, same as the site: navy `#17344b`, gold `#b8841e`, rust `#a34f32`, paper `#fbfaf6`, muted `#66717a`, rules `#d9dde0`.

Structure, top to bottom:

- 16px navy bar.
- Rust tracked kicker: `THE LEAGUE'S MOST QUESTIONABLY SERIOUS PUBLICATION`.
- Navy Playfair Display masthead, two lines: `FLAG FOOTBALL` / `WEEKLY`.
- Muted tracked edition line with a gold bullet. Example: `WEEK 6 • THE WEATHER WON`.
- 84×4 gold rule.
- Two- or three-line serif deck. Use a short version of that edition's story, not the whole page deck.
- Hairline, then three equal columns inside 80px side margins. Big navy figure, muted label underneath.
- 58px navy footer. Left: `CPFF.ONLINE`. Right: `WEEK N • SCOREBOARD, STANDINGS, STOCK WATCH`.

Week 6's columns are `5–1 • +103 / COLE WHITE`, `5 TD • 0 INT / GILBERT CAWLEY`, and `34–12 / JOSEPH'S TEAM`. Use real en dashes. Use lining figures so a zero does not look like a letter.

Fonts: Playfair Display for the masthead, deck, and figures. Source Sans 3 for the kicker, edition line, labels, and footer. A headless Firefox screenshot at `--window-size=1200,630` produces the right pixel size. Set `og:image:alt` to a one-sentence description of the card.

## Leave the prose alone

The joke, the investigations, and the numbers belong to the edition. When archiving, change only URLs, the edition nav, the share tags, and the card.
