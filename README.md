## Alchemist's Orchid for Obsidian

An accessibility-focused Obsidian theme based on the **Alchemist's Orchid** color system:

- **Core palette & accessibility research**: [`alchemists-orchid`](https://github.com/Rynaro/alchemists-orchid)
- **Design tokens & AI metadata**: [`alchemists-orchid-papyrus`](https://github.com/Rynaro/alchemists-orchid-papyrus)

This theme ships:

- **Dark**, **Light**, and **Sepia-flavored light** modes
- A small, AI-friendly layer of **`--ao-*` CSS variables** that map back to Papyrus-style semantic tokens

---

### Installation

1. In Obsidian, open **Settings → Appearance → Themes → Manage**.
2. Click **\"Open themes folder\"**.
3. Create a folder named `alchemists-orchid`.
4. Copy these files into that folder:
   - `manifest.json`
   - `theme.css`
5. Back in Obsidian, select **Alchemist's Orchid** from the theme list.

#### Enabling the Sepia flavor

The theme exposes a sepia variant as a **CSS hook**:

- When Obsidian is in **light** mode, adding `data-ao-flavor="sepia"` to the `body` element will switch to Sepia palette values for backgrounds, text, and accents.
- Today, you can enable this via a small CSS snippet or a future Style Settings integration that toggles this attribute.

---

### Palette overview

From [`alchemists-orchid`](https://github.com/Rynaro/alchemists-orchid):

- **Dark**: background `#2E3440`, foreground `#E5E9F0`, pastel accents (pink, purple, blue, cyan, green, yellow) tuned for reduced halation.
- **Light**: background `#FAFBFC`, foreground `#2E3440`, higher-saturation accents for good contrast on light surfaces.
- **Sepia**: background `#F5F0E6`, foreground `#3B3228`, warm accent set for extended reading and reduced blue light.

The theme focuses on:

- Comfortable reading surfaces
- High-contrast text
- Gentle but distinct accent colors for links, selections, and callouts

---

### For AI agents

This repo is intentionally **AI-friendly**:

- **Semantic tokens** are vendored in `tokens/semantic.json` and `tokens/component.json` (curated subset aligned with Papyrus concepts).
- Color intent is captured via **`--ao-*` CSS variables** in `theme.css`, with inline comments referencing token paths (e.g. `/* tokens/semantic.json: color.surface.dark */`).
- These `--ao-*` variables correspond to Papyrus-style **semantic tokens** (e.g. surface, text-primary, accent-primary, success, warning).
- Obsidian's own theme variables (e.g. `--background-primary`, `--text-normal`, `--interactive-accent`) are expressed in terms of those `--ao-*` variables.

See [`AGENTS.md`](AGENTS.md) for a compact, machine-optimized contract describing:

- Which files to edit when changing colors
- How to stay aligned with the Papyrus token concepts
- How to safely extend the theme while preserving accessibility guarantees
- Quick reference table mapping tokens → CSS variables → Obsidian variables

