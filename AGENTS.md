## Alchemist's Orchid Obsidian Theme — Agent Contract

This file defines how coding agents should work with this theme.

### Files you may edit

- `theme.css`
  - You **may**:
    - Adjust or extend `--ao-*` CSS custom properties.
    - Map those `--ao-*` variables onto Obsidian's standard theme variables.
    - Add minimal new rules that consume existing variables.
  - You **should not**:
    - Inline raw hex colors directly into Obsidian variables (`--background-*`, `--text-*`, `--interactive-*`) if a corresponding `--ao-*` variable exists.

- `tokens/semantic.json`, `tokens/component.json`
  - You **may**:
    - Add new tokens following the existing structure.
    - Update descriptions, accessibility notes, and psychology metadata.
  - You **should not**:
    - Remove or rename existing keys without updating `theme.css` comments and mappings.

### Color architecture

1. **Semantic tokens (JSON)**
   - Located under `tokens/`.
   - Provide named, purpose-driven colors (surface, text, accent, success, warning, etc.).
   - Some tokens are mode-specific, e.g. `"color.surface.dark"`, `"color.surface.light"`.

2. **AO CSS variables**
   - Defined in `theme.css` as `--ao-color-*`.
   - Examples:
     - `--ao-color-surface-dark`
     - `--ao-color-text-primary-light`
     - `--ao-color-accent-primary-dark`
   - Each variable includes a comment referencing its token path, e.g.:
     - `/* tokens/semantic.json: color.surface.dark */`
     - `/* tokens/semantic.json: color.text.primary.light */`
   - This makes it easy to trace CSS variables back to their semantic token definitions.

3. **Obsidian theme variables**
   - Also in `theme.css`, e.g.:
     - `--background-primary`
     - `--text-normal`
     - `--interactive-accent`
   - These should be assigned using the `--ao-*` variables, not raw hex codes.

### Mode handling

- **Dark mode**
  - Scoped under `body.theme-dark`.
  - Uses `--ao-color-*-dark` variables.
  - Intended to align with the dark palette from `alchemists-orchid`.

- **Light mode**
  - Scoped under `body.theme-light`.
  - Uses `--ao-color-*-light` variables.
  - Intended to align with the light palette from `alchemists-orchid`.

- **Sepia flavor**
  - Scoped under `body.theme-light[data-ao-flavor="sepia"]`.
  - Overrides the light `--ao-color-*-light` variables with sepia palette values.
  - Future integrations (e.g. Style Settings or a plugin) can toggle this attribute on `<body>`.

### Accessibility guidelines

When modifying colors:

- Prefer foreground/background pairs that preserve at least **WCAG 2.1 AA** contrast.
- Keep:
  - `--text-normal` on `--background-primary` highly legible.
  - Link and accent colors (`--text-accent`, `--interactive-accent`) clearly distinguishable from body text.
- For new semantic tokens, document any known contrast ratios or intended pairings in `tokens/semantic.json` under an `a11y` extension.

### How to extend the theme (example)

To add a new subtle border style for panes:

1. **Add or reuse an AO variable** in `theme.css`:
   - Prefer reusing an existing border token such as `--ao-color-border-subtle-dark` / `--ao-color-border-subtle-light`.

2. **Wire it into an Obsidian selector**:
   - Example (dark + light safe usage):
     - `.workspace-split { border-color: var(--background-modifier-border); }`

3. **If needed, backfill tokens JSON**:
   - In `tokens/semantic.json`, ensure there is a semantically named token that conceptually corresponds to this border role (e.g. `"color.border.subtle.dark"`), and keep its description in sync with the CSS usage.

By following this pipeline—**tokens → `--ao-*` → Obsidian variables → selectors**—you help maintain a coherent, AI-comprehensible color system across the theme.

### Quick reference: Token → CSS variable mapping

| Token path (semantic.json) | CSS variable (theme.css) | Obsidian variable |
|----------------------------|--------------------------|-------------------|
| `color.surface.dark` | `--ao-color-surface-dark` | `--background-primary` |
| `color.text.primary.dark` | `--ao-color-text-primary-dark` | `--text-normal` |
| `color.accent.primary.dark` | `--ao-color-accent-primary-dark` | `--interactive-accent` |
| `color.success.dark` | `--ao-color-success-dark` | Used in callouts, code strings |
| `color.border.subtle.dark` | `--ao-color-border-subtle-dark` | `--background-modifier-border` |

The same pattern applies for `.light` and `.sepia` variants. Always check `theme.css` comments for the exact token path when modifying colors.

