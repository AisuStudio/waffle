# waffle

Shared design tokens for Aisu.Studio projects — the base every new build starts from.

Waffle is the foundation every ice cream (aisu 🍦) sits on.

## What's in here

- [`tokens.css`](./tokens.css) — color tokens, spacing scale, and `@font-face` declarations
- [`fonts/`](./fonts) — Public Sans and iA Writer Mono, self-hosted
- [`index.html`](./index.html) — a reference page showing every token in use
- [`patterns.html`](./patterns.html) — a quarry of UI patterns (buttons, tags, cards, nav, forms, data display) pulled from lab.aisu.studio, fontane.studio, and the FullerHome design source, sorted by component. Not final — a picking list for what becomes real `components.css`.

## Usage

New projects link `tokens.css` (and copy `fonts/`) directly. Existing projects
(FullerHome, the AisuKurimu site) already carry their own copies of this same
palette — they can be refactored to consume this repo directly, one at a time,
whenever there's a reason to touch them.

## Tokens

| Token | Value | Use |
|---|---|---|
| `--color-blueberry` | `#1f1934` | ink, primary text |
| `--color-grape` | `#5100ff` | accent, links |
| `--color-lemon` | `#d8ff01` | highlight |
| `--color-hazelnut` | `#9e9c95` | borders, dividers, disabled |
| `--color-cappuccino` | `#d9d7ce` | surface / card background |
| `--color-vanilla` | `#eae8e0` | page background |

Semantic aliases worth knowing about (see `tokens.css`):

- `--color-muted: #66655f` — **not** hazelnut. Hazelnut on vanilla is only 2.6:1 contrast; muted text uses this darker value instead (≥4.5:1, WCAG AA). Fix carried over from FullerHome's production `globals.css` — see `patterns.html` for the full writeup.
- `--color-on-accent: var(--color-blueberry)` — the text/icon color to use on top of `--color-accent` or `--color-highlight` surfaces (active tabs, selected badges, total rows). Always pair `accent-bg` with `on-accent` text, never accent as a text color on its own.

Spacing scale: `--sp-xs` (4px) through `--sp-4xl` (96px). See `tokens.css` for the full scale.
