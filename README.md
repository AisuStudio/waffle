# waffle

Shared design tokens for Aisu.Studio projects — the base every new build starts from.

Waffle is the foundation every ice cream (aisu 🍦) sits on.

## What's in here

- [`tokens.css`](./tokens.css) — color tokens, spacing scale, and `@font-face` declarations
- [`fonts/`](./fonts) — Public Sans and iA Writer Mono, self-hosted
- [`index.html`](./index.html) — a reference page showing every token in use

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
| `--color-hazelnut` | `#9e9c95` | muted text |
| `--color-cappuccino` | `#d9d7ce` | surface / card background |
| `--color-vanilla` | `#eae8e0` | page background |

Spacing scale: `--sp-xs` (4px) through `--sp-4xl` (96px). See `tokens.css` for the full scale.
