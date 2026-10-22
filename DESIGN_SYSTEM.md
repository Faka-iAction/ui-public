# FAKA iAction design system

Mobile first, one centred column, plain words, large touch targets. Components use tokens
only, never literal colours, so light and dark themes come from one set of definitions.

## 1. Colour tokens

Defined once on `:root`. Dark values apply through `@media (prefers-color-scheme: dark)`
(guarded by `:root:not([data-theme="light"])`) and through `:root[data-theme="dark"]`, so a
visitor's own choice wins over the system setting.

| Token | Light | Dark | Use |
|---|---|---|---|
| `--primary` | `#0B4F8A` | `#9CCBFF` | Brand, links, filled buttons, selected states |
| `--on-primary` | `#FFFFFF` | `#002A4F` | Text on primary |
| `--surface` | `#FFFFFF` | `#121416` | App background, bars |
| `--text` | `#14171A` | `#EDEFF1` | Body text |
| `--muted` | `#5A646E` | `#A3ACB5` | Secondary text, labels |
| `--line` | `#E3E8ED` | `#23282D` | Hairlines, input borders |
| `--card` | `#F3F6F9` | `#1A1D21` | Cards, tiles, panels |
| `--tint` | `#E6EFF8` | `#192A3A` | Soft primary background |
| `--ground` | `#EDF0F3` | `#0A0B0C` | Page background around the app on wide screens |
| `--error` / `--err-bg` | `#B3261E` / `#FBEAE8` | `#FFB4AB` / `#3A1D1A` | Errors, destructive actions |
| `--ok` / `--ok-bg` | `#1B6B3A` / `#E1F2E6` | `#8FD6A3` / `#183222` | Success chips |
| `--warn` / `--warn-bg` | `#7A5200` / `#FFEFCC` | `#F0C36A` / `#382B0D` | Pending or attention chips |
| `--neu` / `--neu-bg` | `#47515B` / `#E9ECEF` | `#B2BAC2` / `#262B30` | Neutral chips |

## 2. Type

- Body: **Figtree** 400, 500, 600, 700 at `15px/1.45`. Display: **Bricolage Grotesque** 600,
  700. Fallback: `system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif`. The fonts are
  served from the site itself.
- Page title: 25px/1.15 display 700, letter-spacing −0.015em, `text-wrap: balance`.
- Section title: 17px/1.25 display 700. Small heading: 15px body 700.
- Section label: 11.5px, uppercase, letter-spacing 0.09em, muted.
- Eyebrow: 12px uppercase 0.07em muted. Small text: 13.5px.
- Inputs use **16px** text, which stops iOS zooming into a field.

## 3. Shape, spacing and touch targets

- Side gutter: `max(16px, env(safe-area-inset-*))` on every full-width band.
- Page: a flex column with a 14px gap; stacks inside it use 12px.
- Radii: buttons 14px (small 12px), cards and tiles 16px, panels and notices 14px, chips
  20px, avatars round, large icon tiles 28px, the framed app 24px.
- **Minimum touch target 48 × 48** for buttons, fields and rows. Small buttons 36px, tabs 60px.
- No shadows, except the hairline under the top bar and over the tab bar, and the focus ring.

## 4. Components

| Component | Specification |
|---|---|
| Button | 48px high, 15px/600, 1.5px border of primary at 45%, transparent, primary text. Variants: filled, text-only, destructive outline, destructive filled, small (36px), full width. Disabled at 55% opacity. |
| Icon button | 48 × 48 circle, 24px stroke icon (stroke 2, round caps), always with an accessible name. |
| Tile | Card-coloured row or column, 16px radius, 14 × 16 padding; a bold title and a muted 13.5px line. The horizontal form carries a chip or chevron on the right. |
| Card | Card colour, 16px radius, 14 × 16 padding, 8px gap. |
| Chip | Status pill, 12px/700. Kinds: primary tint, ok, warn, error, neutral, and draft (outlined). Chips always carry text: colour is never the only signal. |
| Notice | Tint box, 14px radius. The error form has the error background and a 1.5px inset error border. |
| Detail rows | Label column of about 30% (muted 600) and the value; hairline separators. |
| Field | Label (600 14px), optional hint (13px muted), control (48px, 1.5px line border, 12px radius, primary border on focus), counter on text areas only, inline error (13.5px error 600). |
| Option row | A radio or checkbox row, 48px, card colour, 14px radius; checked = tint with a 1.5px primary inset. |
| Collapsible | `details` in card colour; a 48px summary with + and – indicators. |
| Search bar | Card-coloured field with a leading search icon, and a 48px filter button. |
| Filter chips | 40px pills with a 1.5px border; pressed = filled primary. |
| Segmented tabs | Card-coloured track with 4px padding; the selected tab is surface-coloured with primary text. |
| Empty state | Centred column: a 64px tint circle with an icon, a message and an optional action. |
| Avatar | 44px circle (64px and 84px variants), tint background, initials in the display font. |
| Dialog | Centred card over a scrim, labelled by its heading. Escape and a click on the scrim close it; the first control takes focus. Buttons: text Cancel, then the primary action. |
| Icons | Inline SVG on a 24 × 24 grid, `stroke: currentColor`, stroke width 2, round caps and joins. |

## 5. App frame and navigation

- One centred column, at most 640px wide. From 720px it gets a 1px border, a 24px radius and
  16px of vertical margin on the ground colour.
- A sticky **top bar** (56px, hairline below) holds the mark or page title and one control on
  the right. A sticky **tab bar** at the bottom holds up to five tabs, each a 22px icon over an
  11px label, with a tint pill behind the current tab's icon.
- Navigation is revealed progressively: a new visitor sees no tabs at all; tabs appear as
  the person takes part, signs in or becomes a creator. Fan and creator modes each have their
  own tabs, with a clear switch between them.

## 6. Accessibility

- One `h1` per screen; `nav` for the tabs with `aria-current="page"` on the current tab.
- Every icon-only control has an accessible name. Toggles use `aria-expanded` or
  `aria-pressed`; segmented tabs use the tab roles with `aria-selected`.
- Every control has a visible label. Hints sit under the label. A failed form shows the
  errors next to their fields and in a summary at the top, which takes focus.
- Status messages (copied, saved, counters) are announced through polite live regions.
- Focus ring: `outline: 3px solid var(--primary); outline-offset: 2px`.
- `prefers-reduced-motion` turns off animation; `prefers-color-scheme` picks the theme.
- No horizontal scrolling at 360px wide.
