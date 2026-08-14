<p align="center">
    <img src="https://github.com/eldritch-theme/eldritch/raw/master/assets/logo/green-transparent.png" width="80" />
    <h2 align="center">Eldritch for lich</h2>
</p>

<p align="center">A community-driven dark theme inspired by Lovecraftian horror, with tones from the dark abyss and an emphasis on green and blue</p>

<p align="center">
    <a href="https://github.com/eldritch-theme/eldritch">
        <img src="https://img.shields.io/badge/community-eldritch-37f499?labelColor=212337&style=for-the-badge" />
    </a>
</p>

## Usage

1. Open lich → **Settings → Appearance → Import**.
2. Paste the repository URL: `https://github.com/omartelo/eldritch-lich`
3. Click **Install**.
4. Pick a variant in the theme picker. The terminal picker defaults to
   **Match app theme**, so one pick dresses both — or choose a different variant
   there if you want the panes to differ.

To take a later release, hit **Update** on the theme's row.

### Local install

An absolute path is an accepted remote, so a clone installs the same way:

```bash
git clone https://github.com/omartelo/eldritch-lich.git
```

Then paste the absolute path of the clone into **Settings → Appearance → Import**.

## Variants

| Theme | Upstream palette | `id` | `scheme` |
|---|---|---|---|
| Eldritch | 🦑 Cthulhu | `eldritch` | dark |
| Eldritch Abyss | 🌀 Abyss | `eldritch-abyss` | dark |
| Eldritch Dusk | 🌅 Dusk | `eldritch-dusk` | light |

## How the palette maps

The upstream [color specification](https://github.com/eldritch-theme/eldritch/blob/master/SPEC.md)
names four background rungs; lich's surface tokens take them as an elevation
ladder, so the chrome stays dark instead of drifting to mid-grey:

| Eldritch | lich |
|---|---|
| `background` | `background` — the app ground |
| `currentline` | `card`, `popover`, `sidebar` — tabs, footer, dock, menus, dialogs |
| `surface` | `accent`, `secondary`, `muted`, `border` — hover and selected fills, hairlines |
| `overlay` | `input` — control edges |
| `comment` | `muted-foreground` — secondary text, paths, resting icons |
| `green` | `primary` — the one high-emphasis fill, per the spec's *focus / active* role |
| `red` | `destructive` |
| `cyan` | `ring` — the focus ring; kept off `primary` so a focused green button still shows one |

Dusk shifts the ladder one rung down (`currentline` is the canvas, `background`
is the chrome), the way lich's own light theme mirrors the depth of its dark one.

The terminal palettes follow the upstream
[Alacritty port](https://github.com/eldritch-theme/alacritty), which carries all
three variants.

### Dusk legibility notes

Neon on near-white is a losing fight, so the light variant swaps a few slots for
their darker siblings from the Abyss palette — same family, readable at body
size:

- `black` / `brightBlack` are dark (`#1e2029`, `#5b5c66`) rather than near-white,
  or every dim TUI line would vanish into the background.
- terminal `red`, `green` and `cyan` take the Abyss values; `destructive` takes
  the Abyss red for the same reason.
- `ring` is purple, which the spec prescribes for Dusk text roles where green and
  cyan are decorative only.

## Thanks to

- [omartelo](https://github.com/omartelo) — port author
- [Eldritch contributors](https://github.com/eldritch-theme) — original palette

## Contributing

Each variant is one lich theme file — `eldritch.json`, `eldritch-abyss.json`,
`eldritch-dusk.json` — beside the `lich-theme.json` manifest that carries the
pack's version. There is no generator: colors are edited directly in the theme
files.

To propose a tweak:

1. Fork the repo.
2. Edit the relevant variant file.
3. Validate the **whole directory** — a repository installs all or nothing:
   `node validate.mjs .` (ships with the lich `theme` skill).
4. Bump `version` in `lich-theme.json` in the same commit. An unbumped version
   ships nothing: **Update** compares only that number.
5. Open a PR.

Palette reference: [eldritch-theme/eldritch](https://github.com/eldritch-theme/eldritch).

## License

[MIT](./LICENSE)
