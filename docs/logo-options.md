# g2h0 logo candidates

Explored 2026-08-01. **B4 (particles) is currently live** — the others are kept here to try later.
Interactive preview of all options on the site's glass styling: https://claude.ai/code/artifact/48516bde-d731-4879-be7a-5384cf36683d

All ASCII options are drop-in replacements for the logo element in `index.html` (as a `<pre>`).
Wordmark options replace it with a styled `<div>`; CSS snippets below assume the site's
existing palette (`#e8fff8` ink, `#00ffc8` teal, `#00c8ff` cyan).

## A1 — grid caps

Fixed version of the original: every glyph on the same 5×5 grid, double-width pixels
for correct proportions, uniform 3-space gaps.

```
  ████████   ████████     ██      ██     ██████
██                   ██   ██      ██   ██      ██
██    ████     ██████     ██████████   ██      ██
██      ██   ██           ██      ██   ██      ██
  ████████   ██████████   ██      ██     ██████
```

## A2 — lowercase block

Lowercase with a real descender on the g and ascender on the h — distinctive silhouette.

```
               ██████     ██             ██████
  ████████   ██      ██   ██           ██      ██
██      ██         ██     ████████     ██  ██  ██
██      ██       ██       ██      ██   ██      ██
  ████████   ██████████   ██      ██     ██████
        ██
  ██████
```

## A3 — scanline caps

Same grid as A1 with half-height blocks — CRT scanline texture, lighter weight.

```
  ▀▀▀▀▀▀▀▀   ▀▀▀▀▀▀▀▀     ▀▀      ▀▀     ▀▀▀▀▀▀
▀▀                   ▀▀   ▀▀      ▀▀   ▀▀      ▀▀
▀▀    ▀▀▀▀     ▀▀▀▀▀▀     ▀▀▀▀▀▀▀▀▀▀   ▀▀      ▀▀
▀▀      ▀▀   ▀▀           ▀▀      ▀▀   ▀▀      ▀▀
  ▀▀▀▀▀▀▀▀   ▀▀▀▀▀▀▀▀▀▀   ▀▀      ▀▀     ▀▀▀▀▀▀
```

## A4 — slant (figlet smslant)

```
        ___  __   ___
  ___ _|_  |/ /  / _ \
 / _ `/ __// _ \/ // /
 \_, /____/_//_/\___/
/___/
```

## A5 — small (figlet small)

```
      ___ _    __
 __ _|_  ) |_ /  \
/ _` |/ /| ' \ () |
\__, /___|_||_\__/
|___/
```

## A6 — prompt

A shell prompt with a blinking cursor. Minimal, unbreakable on mobile.

```html
<div id="logo">~ $ g2h0 <span class="cursor">▌</span></div>
```

```css
.cursor { color: #00ffc8; animation: blink 1.1s steps(1) infinite; }
@keyframes blink { 50% { opacity: 0; } }
```

## B1 — formula

g₂h₀ set like a chemical formula (the H₂O pun) — numerals as teal subscripts.

```html
<div id="logo" class="wm-formula">g<sub>2</sub>h<sub>0</sub></div>
```

```css
.wm-formula {
    font-size: 4.2rem;
    color: #e8fff8;
    text-shadow: 0 0 10px rgba(0,255,200,0.5), 0 0 30px rgba(0,200,255,0.25);
}
.wm-formula sub {
    font-size: 0.45em;
    color: #00ffc8;
    vertical-align: baseline;
    position: relative;
    top: 0.28em;
}
```

## B2 — neon cursor

Big lowercase wordmark, teal→cyan gradient fill, blinking terminal underscore.

```html
<div id="logo" class="wm-neon">g2h0<span class="cursor">_</span></div>
```

```css
.wm-neon {
    font-size: 4rem;
    font-weight: 700;
    background: linear-gradient(100deg, #00ffc8 20%, #00c8ff 80%);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    filter: drop-shadow(0 0 14px rgba(0,255,200,0.45));
}
.wm-neon .cursor {
    background: none;
    -webkit-background-clip: initial;
    background-clip: initial;
    color: #00ffc8;
    animation: blink 1.1s steps(1) infinite;
}
@keyframes blink { 50% { opacity: 0; } }
```

## B3 — chromatic

Teal and cyan ghost layers offset behind white — chromatic-aberration glitch echoing
the scene's bloom pass.

```html
<div id="logo" class="wm-glitch">g2h0</div>
```

```css
.wm-glitch { position: relative; font-size: 4rem; font-weight: 700; color: #e8fff8; }
.wm-glitch::before, .wm-glitch::after {
    content: 'g2h0';
    position: absolute;
    inset: 0;
    opacity: 0.75;
    mix-blend-mode: screen;
}
.wm-glitch::before { color: #00ffc8; transform: translate(-3px, -2px); }
.wm-glitch::after  { color: #00c8ff; transform: translate(3px, 2px); }
```

## B4 — particles (LIVE)

The lowercase bitmap drawn as glowing, twinkling canvas dots that assemble on load —
see the `PARTICLE LOGO` script in `index.html`. A future upgrade could render the dots
as tetrahedron instances inside the three.js scene itself so the logo lives in the sim.

## B5 — tag

Self-closing tag treatment. One line, nothing to misalign.

```html
<div id="logo" class="wm-bracket"><span class="b">&lt;</span>g2h0 <span class="b">/&gt;</span></div>
```

```css
.wm-bracket { font-size: 2.6rem; color: #e8fff8; text-shadow: 0 0 8px rgba(0,255,200,0.5); }
.wm-bracket .b { color: #00ffc8; font-weight: 700; }
```

## Combinations worth trying

- B1 formula + A6's blinking cursor after it
- A2 lowercase block rendered in the B2 gradient treatment
