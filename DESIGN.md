# Design

Uni Studio site: a studio-neutral light world built from the logo's four tile colors, so no single game's palette owns the page. The home page is a level map: each game is a numbered stop on a dotted candy road, the next game a locked level. Everything lives in `index.html` `:root`.

## Tokens

| Token | Value | Use |
|---|---|---|
| `--bg` | `#f4f2fa` | page ground (cool off-white, not pink) |
| `--bg-2` | `#fbfaff` | locked node fill |
| `--panel` | `#fff` | stop panels, nodes, nav pills, road base |
| `--line` | `#d9d3ea` | locked node ring, dashed locked panel, padlock |
| `--soft` / `--soft-hover` | `#eeebf7` / `#e2ddf2` | secondary pill button on white |
| `--plum` | `#2b0d4f` | ink, primary button, contact block |
| `--plum-2` | `#5b3a85` | secondary text |
| `--pink` | `#e8338a` | accent: headline highlight, level chips, focus ring, link underline |
| `--sun` | `#ffc22e` | node rings, Coming soon badge, Play triangle |
| `--t-pink --t-violet --t-mint --t-sun` | `#ff5aa8 #a463f2 #3fd9c2 #ffcc3d` | logo tiles; the road's dots cycle through all four |
| `--on-bg` / `--on-bg-2` | plum / plum-2 | text set directly on the ground |
| `--block` | plum | contact block |
| `--shadow` | `0 18px 40px -24px rgb(43 13 79 / .35)` | white panels |
| `--ease` | `cubic-bezier(.16,1,.3,1)` | all motion |

Game palettes (Kitten Pop pink, Arrow Orbit space navy) appear only inside that game's own art: icon, screenshots. Never as page ground.

## Type

- Display and UI: Fredoka 600 (self-hosted `fonts/Fredoka.woff2`, OFL). h1 `clamp(42px, 5.6vw, 80px)`, game names `clamp(30px, 3vw, 38px)`, h2 `clamp(34px, 3.6vw, 46px)`.
- Body: Nunito 400, 18px / 1.6 (`fonts/Nunito.woff2`, OFL).

## Components

- **Level map** `.map`: SVG `.road` drawn by inline JS through every `.node` center (white 30px base + four 12px dotted paths offset by 26px, one per logo color). Continues 140px past the last node and fades out via mask. Draws once on load; nodes pop as it reaches them; reduced motion shows it drawn.
- **Stop** `article.stop` (alternate with `.flip`): node 168px (136px on phones) white circle, 9px sun ring, app icon, pink level chip; white 32px-radius panel with name, pitch, actions, two tilted screenshots. Hovering the node lifts its panel. Stacks centered below 860px, actions in a column.
- **Locked stop** `.stop.locked`: pale node with drawn padlock SVG, dashed panel, "Level N".
- **Pill button** `.btn`: plum, white Fredoka, yellow Play glyph, lifts on hover. `.btn.soft` on `--soft`. Small text links get 12px padding for tap size.
- **Badge** `.badge`: sun pill next to a game name ("Coming soon").
- **Contact block**: plum 40px-radius panel with white email button.

## Adding a game

1. Put art in `assets/<game>/` (icon.webp 256px, screenshots 540px wide webp).
2. Copy one `<article class="stop">` block in `#games` above the locked stop; toggle `flip` so stops alternate sides; bump level numbers (including the locked one).
3. Put its privacy policy at `<game>/privacy.html` and add it to the footer.
