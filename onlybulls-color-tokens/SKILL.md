---
name: onlybulls-color-tokens
description: The OnlyBulls 2.0 color token contract — CDS canonical token names bound to OnlyBulls values, dark mode only. Use this skill whenever you are designing, mocking up, prototyping, or writing code for OnlyBulls — any screen, component, button, card, chart, state, or spec — even if the request never mentions color or tokens. Also use it when reviewing OnlyBulls work for contrast or token misuse, when asked what color something should be, and when producing anything that will be handed to OnlyBulls developers. If the surface is OnlyBulls, load this first.
---

# OnlyBulls color tokens

OnlyBulls is a crypto trading and portfolio app built on the Coinbase Design System (CDS). CDS components accept **token names, never hex** — passing a raw hex is a type error. This skill is the binding between CDS canonical token names and OnlyBulls values.

**Dark mode only.** There is no light theme. Do not invent one.

## Rules

1. **Write CDS token names, not hex.** `background="bgTertiary"`, not `background="#263A36"`. Hex appears in exactly one place: the theme config.
2. **Bind the semantic layer, never the primitives.** Primitive names (`lime-300`, `neutral-800`) are provenance only — they are not an API and must not appear in component code.
3. **One lime CTA per screen.** `bgPrimary` is the single most important action. Nothing else on the screen is lime — not the gain figure, not the selected row, not a secondary button.
4. **Lime means "move your money." Aqua means "information about your money."** CTAs and value emphasis are lime. AI analysis, links, network and wallet identity, chart series are aqua. Keeping these separate is what makes lime read as action.
5. **Gains are `fgPositive` (#68D391), never lime.** If gain figures were lime, the CTA would stop reading as the action.
6. **Focus rings offset by 2px.** `bgAccent` against `bgPrimary` is 1.12:1 — an inline ring on a primary button is invisible. Always `outline-offset: 2px` so the ring sits on the surface behind.
7. **Never use `fgSubtle` for body text inside a card.** On `bgTertiary` it computes to 4.49:1, just under AA. Large text and metadata only; step up to `fgMuted` otherwise.
8. **Aim for roughly 70 / 20 / 7 / 3.** 70% neutral surfaces, 20% neutral type, 7% lime, 3% aqua.

## Tokens

### Surfaces
| Token | Value | Use |
|---|---|---|
| `bg` | `#050B0A` | Level 0 — app canvas |
| `bgSecondary` | `#111F1D` | Level 1 — primary sections |
| `bgTertiary` | `#263A36` | Level 2 — cards, panels, toasts |
| `bgElevation2` | `#112424` | Level 3 — modals, sheets, selected rows, active tabs |
| `bgHover` | `#0F2926` | Hover and emphasis only. Not a fifth layer. |
| `bgAlternate` | `#071D1A` | Alternate section surface |
| `bgOverlay` | `rgba(5,11,10,0.72)` | Scrim behind modals and sheets |

`bgElevation2` is authored as `rgba(105,216,230,0.12)` over `#050B0A`; `#112424` is its composite, used wherever a solid value is required.

### Primary actions
| Token | Value | Use |
|---|---|---|
| `bgPrimary` | `#C9FFA4` | Primary CTA fill, selected chip |
| `bgPrimaryHover` | `#B3FB84` | CTA hover |
| `bgAccent` | `#E8FFD8` | Focus ring — 2px offset, never inline on `bgPrimary` |
| `bgPrimaryWash` | `rgba(201,255,164,0.12)` | Subtle brand container |

### Foreground
| Token | Value | Use |
|---|---|---|
| `fg` | `#F5F8F7` | Balances, headings, body |
| `fgMuted` | `#C6D0CD` | Supporting copy, list metadata |
| `fgSubtle` | `#8FA29D` | Timestamps, captions, placeholders |
| `fgDisabled` | `#455B56` | Disabled text and icons |
| `fgInverse` | `#071D1A` | Label on a lime CTA |
| `fgPrimary` | `#C9FFA4` | Value emphasis. Never body copy, never links. |
| `fgInfo` | `#69D8E6` | Links, AI analysis attribution |
| `fgPositive` | `#68D391` | Gains, confirmed transactions |
| `fgNegative` | `#FF716C` | Losses, failures |
| `fgWarning` | `#F4C95D` | Pending, caution |

### Lines
| Token | Value | Use |
|---|---|---|
| `bgLine` | `rgba(198,208,205,0.12)` | Hairline dividers, card edges |
| `bgLineHeavy` | `rgba(198,208,205,0.20)` | Input borders, prominent edges |
| `bgLinePrimary` | `#70B84F` | Selected and active borders |
| `bgLinePrimarySubtle` | `rgba(104,211,145,0.12)` | Active input border |
| `borderWarning` | `#F4C95D` | Warning toast border |

### Accent pairs — tags, badges, charts
| Token | Value |
|---|---|
| `accentBoldGreen` | `#68D391` |
| `accentSubtleGreen` | `rgba(104,211,145,0.12)` |
| `accentBoldRed` | `#FF716C` |
| `accentSubtleRed` | `rgba(255,113,108,0.12)` |
| `accentBoldBlue` | `#46BEC7` |
| `accentSubtleBlue` | `rgba(105,216,230,0.12)` |
| `accentBoldYellow` | `#F4C95D` |
| `accentSubtleYellow` | `rgba(244,201,93,0.12)` |
| `accentBoldGray` | `#C6D0CD` |
| `accentSubtleGray` | `rgba(198,208,205,0.12)` |

## Contrast

Ratios are computed, not estimated. AA body 4.5:1 · AA large and UI components 3:1 · AAA 7:1.

Safe pairings: `fg` passes AAA on every surface. `fgMuted` passes AAA on `bg` through `bgTertiary` and AA on `bgElevation2` and `bgHover`. `fgPrimary`, `fgInfo`, `fgPositive` and `fgWarning` pass AAA on `bg` through `bgTertiary`.

Watch: `fgSubtle` on `bgTertiary` is 4.49:1 (see rule 7). `fgDisabled` fails everywhere by design — disabled states are exempt under WCAG 1.4.3.

Surface depth is shallow: `bgSecondary` → `bgTertiary` is 1.41:1 and `bgTertiary` → `bgElevation2` is 1.34:1. Do not rely on value alone to separate layers — use `bgLine` borders to carry hierarchy, especially for anything that has to read on OLED at low brightness.

For any pairing not listed, compute the ratio rather than guessing, and state the number.

## Not in this theme

Do not invent values for these. If a design needs one, flag it as an open decision:

- **Pressed states.** No CDS token exists for pressed. `#9DDF71` is the candidate value but has no name.
- **Gradients, icon sizes, shadows.** Removed with `ThemeVarsExtended`.
- **Purple.** `accentBoldPurple` / `accentSubtlePurple` stay on CDS defaults. Staking, NFT and premium surfaces will look unrelated to the rest until this is resolved.
- **Light mode.** Does not exist.

## Applying the theme

`assets/tokens.css` holds the tokens as CSS custom properties, and `assets/theme-config.json` the `color` block for the CDS `ThemeProvider`. Use `theme-config.json` for React and React Native, `tokens.css` for anything web that is not consuming CDS directly.

`references/color-tokens.html` is the human-facing reference — swatches, full token map with provenance, a live contrast matrix, an applied wallet screen, and the open decisions. Open it when you need to show someone the system or check a pairing visually. Do not copy its layout or typography into product work; it is documentation, not a product surface.
