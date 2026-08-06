# waffle

Shared design tokens for Aisu.Studio projects — the base every new build starts from.

Waffle is the foundation every ice cream (aisu 🍦) sits on.

## What's in here

- [`tokens.css`](./tokens.css) — colors (incl. dark mode), spacing, radius, shadow, motion, and `@font-face` declarations
- [`components.css`](./components.css) — real, shippable component classes (`wf-*` prefixed), distilled from `patterns.html`
- [`fonts/`](./fonts) — Public Sans and iA Writer Mono, self-hosted
- [`index.html`](./index.html) — a live, editable reference page for every token, with an Export button
- [`components.html`](./components.html) — every `components.css` class rendered live, one example each
- [`patterns.html`](./patterns.html) — the source quarry `components.css` was distilled from (lab.aisu.studio, fontane.studio, AisuStudio/FullerHome, AisuStudio/spiritsprint) — kept for provenance, not for direct use anymore

## Usage

New projects link `tokens.css` + `components.css` (and copy `fonts/`) directly.
Existing projects (FullerHome, the AisuKurimu site) already carry their own
copies of this same palette — they can be refactored to consume this repo
directly, one at a time, whenever there's a reason to touch them.

```html
<link rel="stylesheet" href="tokens.css">
<link rel="stylesheet" href="components.css">
```

## Tokens

### Primary & secondary colors

| Token | Value | Use |
|---|---|---|
| `--color-blueberry` | `#1f1934` | ink, primary text |
| `--color-grape` | `#5100ff` | accent, links |
| `--color-lemon` | `#d8ff01` | highlight |
| `--color-hazelnut` | `#9e9c95` | borders, dividers, disabled |
| `--color-cappuccino` | `#d9d7ce` | surface / card background |
| `--color-vanilla` | `#eae8e0` | page background |

### Tertiary colors — flavor ramps

The third tier, and a functional one. Above it sit **primary**
(blueberry, grape, lemon — brand and interaction) and **secondary**
(hazelnut, cappuccino, vanilla — surfaces). The flavors carry neither: they
encode meaning in *content* — sequential scales, heatmaps, intensity or
priority coding, categorical series. Don't reach for a flavor to style chrome
(a button, a link, a border); that's what the tiers above are for.

Five flavors × five juicyness levels — level 5 is full juice (most saturated /
darkest), level 1 the most diluted. One level read across flavors gives a
categorical series; one flavor read 1 → 5 gives a sequential scale.

| Flavor | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| `--color-pistachio-*` | `#c4ddb6` | `#a6cd93` | `#92c982` | `#57a03a` | `#3e7c1f` |
| `--color-mango-*` | `#f0d9a3` | `#efcc81` | `#f2b63c` | `#f0921a` | `#ec6608` |
| `--color-strawberry-*` | `#f0aaa0` | `#e9887b` | `#e9634f` | `#ee3d28` | `#d80b0b` |
| `--color-raspberry-*` | `#f5b3d6` | `#f192c7` | `#ee72b6` | `#ea4e9f` | `#e6187c` |
| `--color-chocolate-*` | `#c2b3a5` | `#9f8c7c` | `#7a6250` | `#4b3225` | `#2b1611` |

The bare `--color-<flavor>` (no number) is an alias for level 5, for the
common "just give me the color" case. Like the core swatches these are raw
values — they do **not** repoint in dark mode.

**Text on a flavor fill:** ink (`--color-blueberry`) clears WCAG AA on
pistachio 1–4, mango 1–5, strawberry 1–3, raspberry 1–4, chocolate 1–2;
`--color-vanilla` clears it on chocolate 3–5. Four levels land between 3:1 and
4.5:1 — pistachio 5, strawberry 4 and 5, raspberry 5 — so those take large
text (≥24px, or ≥18.7px bold) or no text at all; for body copy step one level
down or put the label outside the fill.

Semantic aliases worth knowing about (see `tokens.css`):

- `--color-bg` / `--color-surface` / `--color-surface-2` / `--color-text` / `--color-muted` / `--color-accent` / `--color-highlight` / `--color-on-accent` / `--color-border` — the layer components.css is actually built on. Use these instead of the raw `--color-*` swatches whenever you're describing a *role* (background, muted text, accent) rather than a literal color.
- `--color-muted: #66655f` — **not** hazelnut. Hazelnut on vanilla is only 2.6:1 contrast; muted text uses this darker value instead (≥4.5:1, WCAG AA). Fix carried over from FullerHome's production `globals.css`.
- `--color-on-accent: var(--color-blueberry)` — the text/icon color to use on top of `--color-accent` or `--color-highlight` surfaces (active tabs, selected badges, total rows). Always pair `accent-bg` with `on-accent` text, never accent as a text color on its own.

**Dark mode** is built into the semantic layer — via `prefers-color-scheme`, or force it with `<html data-theme="dark">` / `data-theme="light">`. Values are the ones already proven in production by [AisuStudio/spiritsprint](https://github.com/AisuStudio/spiritsprint), not a new invention. The raw `--color-*` swatches never change; only the aliases repoint. Shadows raise their opacity automatically in dark mode so they still read.

Other scales, all in `tokens.css`:

- **Spacing**: `--sp-xs` (4px) through `--sp-4xl` (96px)
- **Radius**: `--radius-xs` (3px, tags/badges) → `--radius-sm` (6px, buttons/inputs) → `--radius-md` (10px, cards/modals) → `--radius-lg` (16px, glass cards) → `--radius-full` (pills)
- **Shadow**: `--shadow-sm/md/lg` — no horizontal shift by default
- **Motion**: `--duration-fast/base/slow` + `--ease-standard/out/in`
- **Breakpoints**: `--bp-sm/md/lg/xl` (30/48/64/80rem) — reference values only; a media query can't read a custom property, so copy the raw rem value into your own `@media` rule

## Components

`components.css` classes are prefixed `wf-` to stay collision-safe in a
project that already has its own `.card`/`.modal`/`.table`. A few components
(`.wf-rail`, `.wf-kpi-row`, `.wf-nav-text`, `.wf-sticky-header`,
`.wf-collapsible`, `.wf-export-card`, `.wf-btn-toolbar`) are deliberately
fixed blueberry/vanilla regardless of the page's own theme — they're dark
app-shell chrome or shareable artifacts, not page content, matching how
FullerHome and spiritsprint actually built them. See `components.html` for
every class rendered live.

This is a v0 first pass, not a finished v1 — expect additions as more
projects migrate onto it (CNSL, Fontane, FullerHome still carry their own
older copies of parts of this system).
