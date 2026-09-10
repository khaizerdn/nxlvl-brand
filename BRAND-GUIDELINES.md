# NXLVL brand guidelines

How to use the artwork in [this repository](README.md). Read
[Permissions](README.md#permissions) first if you are outside the NXLVL team.

## Two inks

Black and white, and nothing else. Every file is a single flat fill, so you tint
it by swapping the `fill` — but the only two values that are the brand are
`#000000` and `#FFFFFF`. There is no brand colour, no gradient, and no dark-mode
variant beyond choosing the white file.

Put the white artwork on a dark ground and the black artwork on a light one.
Where a photograph or busy image makes both unreadable, put the logo on a solid
panel rather than adding a shadow or an outline to it.

## Clear space

Keep **375 units clear on every side** — one cap height, and 54% of the
lockup's own height.

Clear space has to outrank every gap inside the artwork. Anything allowed to sit
nearer than the mark sits to the wordmark starts competing to be read as part of
the lockup. The SVG viewBoxes are tight to the ink, so apply clear space as
layout padding — do not expect it inside the file. The `-on-black` and
`-on-white` PNGs are the exception: they already carry it.

## Minimum sizes

| Artwork | Minimum | Why |
| --- | --- | --- |
| Lockup | **120 px** wide | Keeps the 100-unit stroke at 5 px, below which the counters begin to close |
| Stacked | **80 px** wide | The same 5 px stroke — a narrower box reaches it sooner |
| Mark | **16 px** | The smallest icon this repo ships, drawn tighter so it survives |

At or near the mark's floor, take a ready-made file from `png/icon/` rather
than scaling the SVG yourself: the 16 · 32 · 48 px sizes are drawn tighter on
purpose, which buys back stroke that antialiasing would otherwise eat.

## Do not

- Recolour it, or use any ink but black and white.
- Stretch, squash, rotate or skew it.
- Add a shadow, glow, outline, bevel or gradient.
- Rebuild the wordmark in another typeface — it is drawn as outlines, not set in one.
- Take the mark apart and use a piece of it.
- Crowd it. See [Clear space](#clear-space).
- Put the mark alone where a reader has not already seen the name.
- Use an old file. Pull from this repo rather than from a deck or a screenshot.

## Choosing an artwork

**Lockup** is the primary logo. Reach for it unless the space actively fights it.

**Stacked** exists for square and portrait boxes. Both elements keep exactly the
size the lockup gives them and the air between them is the same measure — it is
the same signature rearranged, not a second logo.

**Wordmark** is for places the mark already appears close by, so repeating it
would be noise.

**Mark** is for avatars, favicons and app icons — contexts that are square and
where the name is supplied by something else on screen.

## Icons

`png/icon/` covers the ladder from 16 px to 1024 px, on black and on white, each
size drawn at its own scale rather than downscaled from one master.

Two special purposes sit alongside them, and they are not interchangeable:

- **`nxlvl-icon-maskable-*.png`** — extra air so Android's adaptive mask cannot
  clip the mark. Opaque edge to edge, as a maskable icon must be.
- **`nxlvl-icon-monochrome-*.png`** — the same crop as a silhouette on
  transparency, for the themed icons Android 13+ tints itself.

`favicon.ico` bundles 16, 32 and 48 px in one file.

## The module

Six constants and five widths generate every coordinate; a seventh spaces the
lockup.

| Measure | Value |
| --- | --- |
| Cap height | 375 |
| Stroke (every stem **and** every diagonal) | 100 |
| Cut length (every corner cut, whatever its angle) | 70.710678 |
| Letter spacing, edge-to-edge at closest approach | 37.5 |
| V flat base | 100 |
| Mark-to-wordmark gap, same measure — 5 letter gaps, ½ cap | 187.5 |
| Advance widths | N 330 · X 330 · L 270 · V 375 |

Everything else is solved, not chosen:

| Derived | Value |
| --- | --- |
| N diagonal | 120.217177 wide, 56.29° — measures 100 across |
| X diagonal | 115.238157 wide, 60.20° — measures 100 across |
| V diagonal | 106.510302 wide, 69.86° — measures 100 across |
| Letter offsets | 0 · 367.5 · 735 · 907.441363 · 1298.040247 |
| Wordmark | 1568.040247 × 375 |
| Lockup | 2359.911831 × 700 |

Each diagonal's angle falls out of a width: the N's from its own, the X's from
its own, the V's from what its flat base leaves over. The offsets are solved
rather than tabulated: each letter is placed where its outline comes exactly
37.5 from its neighbour's at closest approach, which is the only spacing rule
that means the same thing for a vertical stem and a leaning diagonal. The lockup
is spaced by that same rule at five times the distance, so the mark reads as a
mark rather than as a sixth glyph, and the ratio holds at every size.

## Cuts

No cut is arbitrary and none is a plain 45°. Each lies on the angle of the edge
it faces across the gap, so a letter pair reads as one channel:

| Cut | Runs with | Angle |
| --- | --- | --- |
| N top-right, and its rotation at the bottom-left | the X's leading edge | 60.20° |
| L top-left, where the L follows the X | the X's trailing edge | 60.20° |
| L top-left, where the L follows the V | the V's right edge | 69.86° |
| Both L foot terminals | the V's left edge | 69.86° |

That is why the two L's are not the same glyph: each is cut to face the letter in
front of it. Every cut is the same 70.710678 long, so only the angle changes.

## The mark

The mark is the approved master, carried verbatim: the lower-right half is an
exact 180° rotation of the upper-left half about the canvas centre. It keeps its
own weight — a heavier bar than stem, where the wordmark uses one stroke for
both — which is why it is not regenerated from the module like the letters are.

Its square canvas leaves a 15% safe area, which is what makes it drop
straight into a favicon or avatar pipeline without further padding.
