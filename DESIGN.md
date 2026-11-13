# Design

Uni Studio site: bright candy-pink casual-studio look (category standard, layout B). Everything lives in `index.html` `:root`.

## Tokens

| Token | Value | Use |
|---|---|---|
| `--bg` | `#ffe6f2` | page ground |
| `--bg-2` | `#fff4fa` | games band |
| `--panel` | `#fff` | cards, nav pills, soft button |
| `--line` | `#f3c6dd` | dashed "more games" outline |
| `--plum` | `#2b0d4f` | ink, primary button, contact block |
| `--plum-2` | `#5b3a85` | secondary text |
| `--pink` | `#e8338a` | accent: headline highlight, selection, focus ring, link underline |
| `--sun` | `#ffc22e` | Play triangle on primary button |
| logo tiles | `#ff5aa8 #a463f2 #3fd9c2 #ffcc3d` | brand mark SVG only |
| `--shadow` | `0 18px 40px -24px rgb(43 13 79 / .35)` | white panels |
| `--ease` | `cubic-bezier(.16,1,.3,1)` | all motion |

## Type

- Display and UI: Fredoka 600 (self-hosted `fonts/Fredoka.woff2`, OFL). h1 `clamp(46px, 6.4vw, 92px)`, h2 `clamp(34px, 3.6vw, 46px)`, h3 36px.
- Body: Nunito 400, 18px / 1.6 (`fonts/Nunito.woff2`, OFL).

## Components

- **Pill button** `.btn`: plum, white Fredoka 20px, yellow Play glyph, lifts 2px on hover. `.btn.soft` = white variant on plum.
- **Nav pills**: white pills, invert to plum on hover. Stack under brand below 600px.
- **Screenshot fan** `.fan`: five 9:16 captioned store screenshots, rotated -9..9deg; deals open once on load (reduced-motion: static); hover straightens and lifts. Phones show the middle three.
- **Game row** `.game`: white 32px-radius panel; icon 140px, name, one-paragraph pitch, tag pills, Play button + privacy link. Stacks on narrow screens.
- **Contact block**: plum 40px-radius panel with soft email button.

## Adding a game

1. Put art in `assets/<game>/` (icon.webp 256px, screenshots 540px wide webp).
2. Copy the `<article class="game">` block in `#games`, swap name, copy, links.
3. Put its privacy policy at `<game>/privacy.html`.
4. Remove the "More games are on the way" line when it stops being true.
