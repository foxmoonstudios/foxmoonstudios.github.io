# foxmoonstudios.com

The Foxmoon Studios website: one static page, served by GitHub Pages at
[foxmoonstudios.com](https://foxmoonstudios.com). No build step. Edit the
files, commit, push, and Pages publishes the change in a minute or two.

| File | What |
|---|---|
| `index.html` | The page: the hero, the games, the links, the contact email. |
| `styles.css` | All the styling. The colours and fonts are at the top. |
| `404.html` | The page GitHub Pages shows for a link that doesn't exist. |
| `CNAME` | The custom domain. Pages reads it; don't delete it. |
| `assets/` | Images, the fox's animation and the fonts (below). |
| `.nojekyll` | Tells Pages to serve the files as they are. |

## Preview it

From this folder:

```
python -m http.server 8000
```

then open <http://localhost:8000>.

## Change the games

Each game is one `<li class="game">` in `index.html`, in the order they show
on the page. Copy one to add a game; delete one to drop it. The prototypes
(Cattitudes) sit in their own smaller list under the released games.

The game art is linked straight from Steam and itch.io (the `capsule_616x353`
image on Steam, the cover on itch.io), so it costs the repo nothing. Steam
gives each new upload a new address, so **when a store page's art changes,
the old link can stop working**. Either paste in the new address (open the
store page, right-click the capsule, copy the image address) or, better,
put the file in `assets/games/` and point the `src` at it.

Cattitudes uses itch.io's small 315x250 cover, because the full one is over
2 MB. A 630x500 export saved as `assets/games/cattitudes.webp` would look
sharper.

## Assets

Everything in `assets/` comes from the Dead Position art package
(`art/logo/kit/` and `art/store/itch/`), resized and converted for the web:

| File | From |
|---|---|
| `fox-loop.webm` | `logo/kit/animated/foxmoon_loop.webm` (as is: VP9 with alpha) |
| `fox-still.webp` | The loop's first frame, 900 px, so the still and the video line up exactly |
| `fox-mark.webp` | `logo/kit/logo/foxmoon_256.png` at 128 px |
| `wordmark.webp` | `logo/kit/wordmark/foxmoon_studios.png` at 1400 px |
| `galaxy.webp`, `galaxy-1280.webp` | `store/itch/foxmoon_galaxy_background.jpg` |
| `og-image.jpg` | `logo/kit/lockup/foxmoon_wide_night.png`, cropped to 1200x630 for link previews |
| `favicon-64.png`, `icon-192.png`, `../favicon.ico` | `logo/kit/logo/foxmoon_512.png` |
| `apple-touch-icon.png` | `logo/kit/logo/foxmoon_avatar_1024.png` at 180 px |
| `fonts/` | Barlow and Barlow Condensed (SIL Open Font License, `fonts/OFL.txt`), the nearest web fonts to the wordmark's Bahnschrift |

The fox animates in Chrome, Edge and Firefox. Safari can't show a WebM
video's transparency, so Safari and every iOS browser get the still, and so
does anyone with reduced motion turned on. The pause button beside the fox
stops it for everyone else.

The platform icons are from [Simple Icons](https://simpleicons.org) (CC0).

## The domain

Pages is set to the custom domain `foxmoonstudios.com` with HTTPS enforced.
The domain is registered through Google Workspace at Squarespace, and its
DNS has these records for the site:

| Type | Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | foxmoonstudios.github.io. |
| TXT | _github-pages-challenge-foxmoonstudios | (GitHub's verification code) |

The TXT record proves to GitHub that the foxmoonstudios org owns the domain
(org Settings > Pages > Verified domains), so no other account can point a
Pages site at it. Keep it.

The MX, SPF (TXT on @) and DKIM (`google._domainkey`) records are for the
studio's email. Leave them alone.
