# Halvorsen Resources — Brand Guidelines

These are the visual rules for Halvorsen Resources (**ASX: HVR**) content: logo, typography, colour, layout, and how an HVR Stori or web asset is put together. They are enforceable defaults. Anything produced under the HVR brand follows them unless there's a deliberate reason not to.

**Version 0.1 · derived from `HVR_Style_Guide.pdf` + the StoriBot multi-industry template v0.5.**

> Halvorsen Resources is a fictional company used for demonstration content. Its name, palette and logo are invented and do not represent any real listed entity.

### How this document is structured
There are two parts.

- **Part 1 — Core** carries the HVR brand system: palette, type, tokens, charts and formatting rules. It uses the same layout as the multi-industry template, so tooling and agents can read it the same way.
- **Part 2 — Mining (ASX) pack** applies because HVR is an ASX-listed resources company. The template's tech and research packs are left out as not relevant.

Where this document and the source PDF disagree, the PDF's palette and typeface win. Where the PDF says nothing (contrast steps, tokens, chart rules, spacing), the values here are the working defaults.

---

# Part 1 — Core

## Logo

From the HVR Style Guide:

### Main logo
The main logo is the horizontal lockup. The **strata mark** is three stacked horizontal bands rising to a shallow peak, like a stylised drill cross-section. The top two bands are **Halvorsen Teal** `#0E4D5C`, and the lowest band is **Copper** `#C8762B`. The "Halvorsen Resources" wordmark sits beside it in teal. This is the default on white and light backgrounds.

### Alternative logos
Use these for materials that need a particular placement, style or shape:
- **Reversed on slate** (`#16242B`): the wordmark and teal bands reverse to white, and the copper band stays copper (≈ 4.6 : 1 on slate). For small sizes there is a single-colour all-white version.
- **Stacked lockup:** the mark sits above a two-line "Halvorsen / Resources" wordmark, for square or narrow placements and social avatars.
- **Mark only:** the strata mark on its own, for favicons and app icons.

### Usage rules (suggested defaults; the PDF doesn't specify, so treat as working values)
- **Clear space:** keep a margin at least the height of the mark on all sides.
- **Minimum size:** don't render the horizontal lockup narrower than about 120px on screen. Below that, use the mark alone.
- **Never** do any of the following:
  - recolour the mark outside the approved combinations;
  - stretch or rotate it;
  - set it on a copper (`#C8762B`) or mist (`#C9D3D8`) background;
  - drop the copper band from the primary mark.
- **Web:** serve the logo as SVG. Provide the reversed version through `prefers-color-scheme` or an explicit dark-surface class, not CSS filters.

---

## Typography

### Font stack
The brand face is **Source Sans 3**. Use it for headings and body alike, with no second display face. For tables of figures, **Source Sans 3** with tabular numerals is enough; don't bring in a monospace face.

```css
font-family: "Source Sans 3", "Source Sans Pro", "Segoe UI", "Helvetica Neue", Arial, sans-serif;
```

Source Sans 3 is released under the SIL Open Font License. It can be self-hosted or loaded from Google Fonts without extra licensing, which is why HVR chose it over a commercial face.

### Weights & usage
| Use | Weight | Notes |
|---|---|---|
| Display / H1 | 700 | Bold. Tight leading, generous size |
| Headings H2–H3 | 600 | Semibold |
| Body | 400 | Regular. 16px minimum, 1.5–1.6 line-height |
| Captions / labels | 500 | Medium. Smaller; used for source attributions |

### Loading the font
**Hosted (simplest):**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Source+Sans+3:wght@400;500;600;700&display=swap" rel="stylesheet">
```

**Self-hosted (preferred for performance and privacy):** use the variable file from Google Fonts or Fontsource.
```css
@font-face {
  font-family: "Source Sans 3";
  font-style: normal;
  font-weight: 400 700;
  font-display: swap;
  src: url("/fonts/source-sans-3-var.woff2") format("woff2-variations");
}
```
Preload the font file to reduce layout shift:
```html
<link rel="preload" href="/fonts/source-sans-3-var.woff2" as="font" type="font/woff2" crossorigin>
```

### Type scale (suggested baseline, 1.25 ratio)
| Token | Size | Line-height |
|---|---|---|
| `text-xs` | 12px | 1.5 |
| `text-sm` | 14px | 1.5 |
| `text-base` | 16px | 1.6 |
| `text-lg` | 20px | 1.5 |
| `text-xl` | 25px | 1.4 |
| `text-2xl` | 31px | 1.3 |
| `text-3xl` | 39px | 1.2 |

Keep body copy at 16px or above. Retail holders read this content on phones, and source attributions must stay legible.

---

## Colour

### Brand colours (from the HVR Style Guide)
| Name | Hex | Role |
|---|---|---|
| **Halvorsen Teal** | `#0E4D5C` | Primary brand and lead accent: the mark and wordmark colour |
| **Copper** | `#C8762B` | Primary brand and signature highlight: the lower band of the mark |
| **White** | `#FFFFFF` | Primary: default background |
| **Slate** | `#16242B` | Secondary: ink, dark surfaces, reversed lockups |
| **Mist** | `#C9D3D8` | Secondary: decorative neutral, hairlines, table rules |

**Read this before you use them for text.** On a white background:

- `#0E4D5C` (teal) on white ≈ **9.4 : 1**
- `#C8762B` (copper) on white ≈ **3.5 : 1**
- `#16242B` (slate) on white ≈ **15.9 : 1**
- `#C9D3D8` (mist) on white ≈ **1.5 : 1**

WCAG AA needs **4.5 : 1** for normal text and **3 : 1** for large text and UI components. That puts each colour in a different place:

- ✅ **Teal clears AA for normal text by a wide margin.** It works everywhere, including body text, links, small labels and button fills. It's the workhorse.
- ✅ **Slate clears everything.** It's the default ink for text on light surfaces and the default dark surface.
- ⚠️ **Copper clears the 3 : 1 large-text/UI bar but not normal text.** On white you can use it for headings of 24px and up (or 19px bold and up), icons, chart marks, borders and accent bars. It must not be used for body text, links or small labels; use the text-safe steps below for those.
- ❌ **Mist fails every text threshold** (≈ 1.5 : 1). Use it for hairlines, table rules, subtle backgrounds and dividers only, never text.

### The copper-on-slate pairing
Copper's strongest role is on **slate**. `#C8762B` on `#16242B` is ≈ **4.6 : 1**, which just clears AA for normal text. This is how the reversed logo works, and it's the on-brand way to make copper stand out. Slate text on a copper fill is also ≈ 4.6 : 1. **White on copper is ≈ 3.5 : 1: large or bold labels only, never body-size text.** Avoid **copper on teal** (≈ 2.7 : 1) for anything that has to be read.

### Text-safe variants
When copper has to read as normal-size text, or has to carry white text, use a darker step:

| Name | Hex | On white | Use for |
|---|---|---|---|
| Teal — text | `#0E4D5C` | ✅ ~9.4 : 1 | Body text and links (no substitution needed) |
| Copper — UI | `#A25A17` | ✅ ~5.2 : 1 | Copper-family button fills with white text, badges |
| Copper — text | `#8A4B12` | ✅ ~6.8 : 1 | Copper-family links and small text |
| Copper — chart | `#C8762B` | ✅ ~3.5 : 1 | Brand copper is chart-legible as-is |
| Mist — text | `#5B6770` | ✅ ~5.8 : 1 | Muted labels where a cool grey is wanted |

**Buttons:**
- **Default primary:** teal fill with **white** text, ≈ 9.4 : 1 ✅.
- **Slate:** slate fill with white text, ≈ 15.9 : 1 ✅.
- **Copper call-to-action:** either the `#A25A17` step with white text (≈ 5.2 : 1) or brand copper with **slate** text (≈ 4.6 : 1).

Check white-on-fill contrast before shipping.

> **Tonal note.** Teal and copper are complementary hues, cool against warm, so they separate strongly in colour. In greyscale, though, teal (dark) and copper (mid) differ only moderately, at ≈ 2.3 : 1 between chart copper and teal. Charts that pair the two still need the "colour is never the only signal" rule. That matters most for anything printed or photocopied, such as board packs and appendices.

### Neutrals & semantic (suggested; adjust to taste)
This is a practical neutral ramp, cooled slightly to sit with the teal, with slate as the ink. These values aren't fixed; the brand colours are.

| Token | Hex | Notes |
|---|---|---|
| `ink` (body text) | `#16242B` | Brand slate, ≈ 15.9 : 1 on white |
| `ink-muted` | `#46606B` | Teal-tinted muted, ≈ 6.7 : 1 |
| `line` (borders) | `#C9D3D8` | Brand mist |
| `surface` | `#E8F0F2` | Cool off-white (teal band) |
| `white` | `#FFFFFF` | |
| `success` | `#16A34A` | |
| `warning` | `#D97706` | |
| `danger` | `#DC2626` | |

> Note for JORC/AFSL gating UI: if PASS/FIX/BLOCK states use colour, pair each with a label or icon. That's needed for accessibility and for the compliance-officer audience.

---

## Design tokens

### CSS custom properties
```css
:root {
  /* Type */
  --font-sans: "Source Sans 3", "Source Sans Pro", "Segoe UI", "Helvetica Neue", Arial, sans-serif;

  /* Brand */
  --color-teal:   #0E4D5C;  /* primary: mark, wordmark, lead accent  */
  --color-copper: #C8762B;  /* primary: signature highlight           */
  --color-slate:  #16242B;  /* secondary: ink, dark surfaces          */
  --color-mist:   #C9D3D8;  /* secondary: decorative neutral only     */

  /* Text-safe brand */
  --color-teal-text:    #0E4D5C;  /* already AA on white */
  --color-copper-ui:    #A25A17;
  --color-copper-text:  #8A4B12;
  --color-copper-chart: #C8762B;
  --color-mist-text:    #5B6770;

  /* Neutrals */
  --color-ink:        #16242B;
  --color-ink-muted:  #46606B;
  --color-line:       #C9D3D8;
  --color-surface:    #E8F0F2;
  --color-white:      #FFFFFF;

  /* Semantic */
  --color-success: #16A34A;
  --color-warning: #D97706;
  --color-danger:  #DC2626;
}

body {
  font-family: var(--font-sans);
  color: var(--color-ink);
}
```

### Tailwind (if the site or app uses it)
```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['Source Sans 3', 'Source Sans Pro', 'Segoe UI', 'Helvetica Neue', 'Arial', 'sans-serif'],
      },
      colors: {
        brand: {
          teal: '#0E4D5C',
          copper: '#C8762B',
          'copper-ui': '#A25A17',
          'copper-text': '#8A4B12',
          slate: '#16242B',
          mist: '#C9D3D8',
          'mist-text': '#5B6770',
        },
      },
    },
  },
}
```

---

## Charts & data visualisation

Chart colour follows different rules from UI colour. A chart palette must be:
- **ordered**, so the agent assigns colours deterministically (series 1 gets colour 1, and so on);
- **distinguishable on a white background**;
- **colourblind-safe**.

The palette below starts from HVR teal and copper, uses slate as the third brand series, and keeps mist-text as the neutral.

### Principle: the brand colours lead
Teal `#0E4D5C` is series 1 and reads as HVR at a glance. Brand copper `#C8762B` (≈ 3.5 : 1) holds a line on white at normal weight, so unlike many warm accents it needs **no chart-only step**. The same copper is used across the logo, the UI accent and charts.

### Categorical palette (qualitative, for distinct series)
Use the colours in order and stop at six series; beyond that no palette stays readable, colourblind or not. Keep mist-text for an "Other" or baseline series.

| # | Name | Hex | Notes |
|---|---|---|---|
| 1 | Teal (brand primary) | `#0E4D5C` | Lead. ≈ 9.4 : 1 on white |
| 2 | Copper (brand primary) | `#C8762B` | ≈ 3.5 : 1 on white; warm complement to series 1 |
| 3 | Slate (brand secondary) | `#16242B` | ≈ 15.9 : 1; tell it from teal by adding markers |
| 4 | Violet | `#7C3AED` | ≈ 5.7 : 1 |
| 5 | Rose | `#BE185D` | ≈ 6.0 : 1 |
| 6 | Olive | `#4D7C0F` | ≈ 5.0 : 1 |
| — | Grey (Other) | `#5B6770` | Default for "Other", baseline or de-emphasised series |

All six clear ≈ 3 : 1 on white, so the whole set reads as lines without a stroke-weight caveat. Teal and slate are both dark and cool, so whenever series 1 and 3 appear together, give them different markers or line styles (solid against dashed).

### Selection rules for the agent
- **1 series:** teal (`#0E4D5C`).
- **2 series:** teal and copper. This is the default and the most on-brand pairing. If the two carry opposite meanings (above or below a line, say), keep teal for the subject or highlight and copper for the comparator.
- **3–6 series:** walk the categorical palette in order.
- **More than 6 categories:** don't add colours. Group the long tail into "Other" (grey) or change chart type, for example ranked bars instead of a 12-slice pie.
- **Highlighting one series:** colour the focus series teal and set all the others to one neutral (`#C9D3D8`). One accent beats six.

### Sequential ramps (one ordered metric: choropleths, heat cells, magnitude)
The ramps run light to dark. Use the teal ramp by default, and the copper ramp when teal already means something else. For grade heatmaps, use the copper ramp so it reads as the metal.

```
Teal:   #E6F0F2  #BFD7DD  #7FA9B4  #3F7887  #0E4D5C  #08323C
Copper: #FBEFE3  #F4D2B0  #E6A66C  #C8762B  #A25A17  #6E3C0E
```

### Diverging ramp (data with a meaningful midpoint)
Use this for values above or below a reference, such as share price against an index or % change against zero. Copper means below or negative (warm) and teal means above or positive (cool). The ramp fits the brand and is colourblind-safe. The midpoint is a true neutral (`#F1F1EF`), not a tint, because a hue at the midpoint would read as a weak signal rather than none.

```
#6E3C0E  #A25A17  #C8762B  #E6A66C  #F1F1EF  #9FC0C8  #5E919E  #2B6674  #0E4D5C
 ◄──────────── below / negative ─────────  mid  ───────── above / positive ────────►
```

### Chart neutrals (axes, gridlines, labels)
| Use | Hex |
|---|---|
| Plot title | `#16242B` (ink) |
| Axis line / strong tick | `#C9D3D8` (mist) |
| Gridline (subtle) | `#EEF3F5` |
| Tick labels / legend text | `#46606B` (ink-muted) |
| Reference / annotation line | `#8A9AA3` |
| De-emphasised series | `#C9D3D8` |

### Chart tokens
```css
:root {
  /* Categorical: assign in array order */
  --chart-1: #0E4D5C;  /* teal (brand primary)     */
  --chart-2: #C8762B;  /* copper (brand primary)   */
  --chart-3: #16242B;  /* slate (brand secondary)  */
  --chart-4: #7C3AED;  /* violet                   */
  --chart-5: #BE185D;  /* rose                     */
  --chart-6: #4D7C0F;  /* olive                    */
  --chart-other: #5B6770;  /* grey (Other)         */

  /* Chart neutrals */
  --chart-axis:   #C9D3D8;
  --chart-grid:   #EEF3F5;
  --chart-label:  #46606B;
  --chart-ref:    #8A9AA3;
  --chart-muted:  #C9D3D8;
}
```

```js
// Ordered array: the agent reads left to right, one colour per series.
export const HVR_CHART_COLORS = [
  '#0E4D5C', '#C8762B', '#16242B', '#7C3AED', '#BE185D', '#4D7C0F',
];
export const HVR_CHART_OTHER = '#5B6770';

export const HVR_SEQUENTIAL_TEAL   = ['#E6F0F2','#BFD7DD','#7FA9B4','#3F7887','#0E4D5C','#08323C'];
export const HVR_SEQUENTIAL_COPPER = ['#FBEFE3','#F4D2B0','#E6A66C','#C8762B','#A25A17','#6E3C0E'];
export const HVR_DIVERGING         = ['#6E3C0E','#A25A17','#C8762B','#E6A66C','#F1F1EF','#9FC0C8','#5E919E','#2B6674','#0E4D5C'];
```

### Accessibility rules (apply to every chart)
- **Never rely on colour alone.** Pair colour with a second cue:
  - direct series labels at the line ends;
  - markers (●▲■) on lines;
  - value labels on bars;
  - patterns on fills.

  Teal and slate need this rule most, because they sit close together in lightness.
- **No red/green for up/down.** It's the worst pairing for colourblind readers, and it reads as a buy/sell signal, which clashes with the AFSL voice. Use the copper/teal diverging ramp, and always add a sign or arrow (▲ +4.2% / ▼ −1.8%).
- **Minimum stroke 2px** on line charts, for every series.
- **Check fills that carry text** against the fill colour, not just against white. Copper fills carry slate text, or white text only when it's large and bold.

---

## Spacing & layout

A spacing scale stops the agent inventing margins. Everything sits on an **8px base grid**: use multiples of 8, with 4px as the one allowed half-step for tight inline gaps.

### Spacing scale
| Token | Value | Typical use |
|---|---|---|
| `space-1` | 4px | Icon-to-label, inline chip padding |
| `space-2` | 8px | Tight stacks, badge padding |
| `space-3` | 12px | Card inner gaps, list rows |
| `space-4` | 16px | Default element spacing |
| `space-6` | 24px | Card padding, between paragraphs |
| `space-8` | 32px | Between sub-sections |
| `space-12` | 48px | Between major sections |
| `space-16` | 64px | Section breaks on wide layouts |

### Radius scale
HVR runs slightly squarer than the template, to echo the flat strata bands of the mark.

| Token | Value | Use |
|---|---|---|
| `radius-sm` | 4px | Inputs, small chips |
| `radius-md` | 6px | Buttons, default |
| `radius-lg` | 10px | Cards, chart panels |
| `radius-full` | 9999px | Pills, avatars |

Elements with a border on one side only (a left accent bar) take `radius: 0`. Round the corners only when there's a full border.

### Layout
- **Reading measure.** Body text is capped at a **680px content column** (about 70 characters per line), because long lines are hard to read on desktop. Tables, charts and figures may break out wider, up to a **1080px** page maximum.
- **Breakpoints** (mobile-first, because investor content is read on phones first):

| Token | Min width | Notes |
|---|---|---|
| `sm` | 640px | Large phone / small tablet |
| `md` | 768px | Tablet: two-column figures become viable |
| `lg` | 1024px | Desktop |
| `xl` | 1280px | Wide desktop: maximum page gutters |

- **Page gutters:** 16px on mobile, 24px at `md`, 32px or more at `lg`.
- **Vertical rhythm:** separate major sections by `space-12` (48px). Never crowd a source attribution against the next heading.
- **Dark sections:** hero bands and footers may use brand slate `#16242B` or teal `#0E4D5C`, with white text, copper accents and the reversed logo. Put copper **text** on slate only, never on teal. Keep long-form reading on white.

```css
:root {
  --space-1: 4px;  --space-2: 8px;  --space-3: 12px; --space-4: 16px;
  --space-6: 24px; --space-8: 32px; --space-12: 48px; --space-16: 64px;
  --radius-sm: 4px; --radius-md: 6px; --radius-lg: 10px; --radius-full: 9999px;
  --measure: 680px;      /* reading column */
  --page-max: 1080px;    /* full page width */
}
```

---

## Number, date & currency formatting

These are the highest-value rules in this document. Two documents must never format the same figure two ways, and in a disclosure context formatting is a matter of correctness, not style. The default locale is **en-AU**.

### Numbers
- **Thousands separator:** comma. Decimal: point. `1,234,567.8`.
- **Round to the precision the metric calls for** (see the mining units table in Part 2). Never show raw float artefacts.
- **Ranges:** use an en dash with no spaces when a unit follows: `12–18 m`, `3.2–4.1 g/t`.
- **Negatives and changes:** use a true minus `−` (U+2212), not a hyphen, and put the sign before any symbol: `−$5M`, never `$−5M`. Change values carry an explicit sign: `+4.2%`, `−1.8%`.
- **Percentages:** state the base where it isn't obvious. Keep a percentage change distinct from percentage points, and write `pp` for points (`margin rose 3 pp`).
- **Missing data:** `n/a` or an em dash `—`. Never `0` for an unknown value.

### Dates
- **Long form (default in prose):** `29 June 2026`. **Short form (tables, captions):** `29 Jun 2026`.
- **Never** use US `MM/DD/YYYY` or ambiguous numeric dates.
- **Financial year:** `FY2026`, named for the year the 30 June close falls in. Write quarters as `September 2026 quarter` in prose and `Q1 FY27` in tables. Define the convention once and keep to it.
- **"As at" stamps:** every figure that can change (resource estimate, cash balance, share price) carries an as-at date, for example `as at 30 June 2026`.

### Currency
- **AUD is the default for ASX content.** Where operations or figures span currencies, **prefix every figure**: `A$1.2M`, `US$3.1bn`. Never leave a bare `$`.
- **First mention** in a document states the basis: `A$1.2 million (AUD)`. After that, `A$1.2M` is fine.
- **Abbreviations:** use `k` (thousand), `M` (million) and `bn` (billion) in tables and captions. Spell out `million` and `billion` in running prose for retail readers. Be consistent within a document.
- Mention GST treatment only where it's material and the source states it.

### Universal rules
- **Ticker:** `ASX: HVR`: uppercase, one space after the colon.
- **Never show a number without its unit**, and never a figure about a named entity without its source.

### Tabular numbers
In any table or aligned column of figures, use lining tabular numerals so the digits line up:
```css
.hvr-num { font-variant-numeric: tabular-nums lining-nums; text-align: right; }
```

### Reference implementation
```js
const auNum  = new Intl.NumberFormat('en-AU');                       // 1,234,568
const auDate = new Intl.DateTimeFormat('en-AU',
  { day: 'numeric', month: 'long', year: 'numeric' });               // 29 June 2026
const grade  = (n) => `${n.toFixed(2)}% Cu`;                         // 1.20% Cu
const pct    = (n) => `${n >= 0 ? '+' : '−'}${Math.abs(n).toFixed(1)}%`;  // +4.2% / −1.8%
// Currency stays manual so the A$/US$ basis is never ambiguous:
const aud    = (n) => `A$${auNum.format(Math.round(n))}`;            // A$1,234,568
```

---

## Components

These are the building blocks of an HVR Stori or page. Define each once, and the agent stops improvising layout and every output reads the same.

### Source attribution caption
Every claim carries one. It's small and muted, and sits directly under the figure or statement it supports.
```html
<p class="hvr-source">Source: ASX announcement, 27 May 2026</p>
```
`font-size: 13px; color: var(--color-ink-muted); margin-top: var(--space-1);`

Never go smaller than 12px: the caption must stay readable on a phone and satisfy a compliance reader.

### Figure / stat callout
A headline number with its label and source. The number is `text-2xl`–`text-3xl` in **teal**, the label is a muted caption, and the source sits beneath.
```html
<div class="hvr-stat">
  <span class="hvr-stat__value">170.2 Mt</span>
  <span class="hvr-stat__label">Mineral Resource (Indicated &amp; Inferred, JORC 2012)</span>
  <p class="hvr-source">Source: company announcement, 27 May 2026 · as at 27 May 2026</p>
</div>
```
The accent colour on the value is for data emphasis only; see Compliance-aware design.

### Data table
- The header row is white text on **teal** (≈ 9.4 : 1). This matches HVR's printed announcements.
- Body rules are **mist**.
- Numbers are right-aligned with `.hvr-num`.
- Total rows go on `surface` in bold.
- The source goes in a footer row, not floating after the table.
- Keep to six columns or fewer on mobile, or wrap the table in a horizontally scrolling container.

### "As at" stamp
A small pill or inline note fixing the date of a figure that can change: `as at 30 June 2026`. It's required on resources, cash, capital structure and price.

### Disclaimer block
Keep it distinct from body copy: smaller, on `surface`, with a hairline top border. It must always be legible: at least 12px, never collapsed or hidden behind a toggle.
```html
<aside class="hvr-disclaimer">
  <p>Competent Person Statement … [name] … consents to the inclusion …</p>
  <p>Forward-looking statements … may differ materially …</p>
</aside>
```
`font-size: 13px; color: var(--color-ink-muted); border-top: 1px solid var(--color-line); padding-top: var(--space-4);`

### Company statement / pull quote
Quote and attribute direct company statements; don't paraphrase them into a verdict. Pull quotes get a brand **copper** left accent bar, echoing the copper band of the logo: `border-left: 3px solid var(--color-copper); radius: 0`. It's decorative and passes 3 : 1 as a UI element. The attribution sits beneath as a muted caption.

### Highlights panel
This is the signature layout of an HVR announcement. It's a `surface` panel with a 4px **copper** left bar, holding the bullet highlights in slate at weight 600–700.

### Commentary anchor
The feedback and commentary feature binds to `data-stori-block-id`. Every block that can be annotated carries the attribute, plus a subtle hover cue such as a margin marker or faint highlight. Never use a persistent border that competes with the content.
```html
<section data-stori-block-id="blk_7f3a">…</section>
```

### Section header
Section headers are `text-xl`/`text-2xl` in **teal**, weight 600, with `space-12` above and an optional mist hairline beneath. Use one H1 per document (the title), H2 for sections and H3 for sub-points. Don't skip levels.

---

## Compliance-aware design (principle)

Every HVR document carries a regulatory obligation. The rule that applies everywhere is: **the visuals must never claim more than the data and the regime allow.** Colour, weight, arrows and ranking all carry meaning, so they follow the same rules as the words.

Without exception:
- **Colour is never the only signal** (chart series, states). Pair it with a label, marker or icon.
- **Required statements are first-class.** They're present, legible at 12px or more, and never hidden behind a toggle or collapsed by default. Visible compliance is part of the brand.
- **Internal authoring signals never appear in the output.** The gating a document passes before publication (PASS / FIX / BLOCK) is not for investors.
- **Figures that can change carry an as-at date, and claims about named entities carry a visible source.**

---

## Do / don't

- ✅ Use teal as the primary accent and workhorse, and copper as the signature highlight. Don't split usage 50/50: teal leads and copper punctuates, like the logo's two teal bands and one copper band.
- ✅ Put copper text on slate. That's the reversed-logo pairing and the bold on-brand choice.
- ✅ Use slate as the ink and the dark surface. Leave plenty of white space, and let the type plus one or two accents carry the page.
- ❌ Don't set body-size text in `#C8762B` on white. Use `#8A4B12` for text or `#A25A17` for UI.
- ❌ Don't put copper text on teal (≈ 2.7 : 1), and don't use white body text on copper (≈ 3.5 : 1).
- ❌ Don't use `#C9D3D8` for text. It's for hairlines and backgrounds only; `#5B6770` is the text-safe grey.
- ❌ Don't add a fourth brand hue or a second typeface without a reason.
- ❌ Don't use colour as the *only* signal in compliance or state UI.

---

# Part 2 — Mining (ASX) pack

HVR is an ASX-listed resources company, so this pack applies to every document. The template's Tech and Research packs are left out as not relevant to HVR.

> **Regime:** JORC Code 2012 + AFSL / ASX continuous disclosure. The company is listed and its readers include retail holders, so content about a named entity is strictly factual, sourced and dated.

### Domain units & formatting
| Quantity | Format | Decimals |
|---|---|---|
| Gold grade | `4.3 g/t Au` | 1–2 dp |
| Base-metal grade | `0.47% Cu`, `0.02% Co` | 2 dp |
| Copper equivalent | `0.54% CuEq`, with the equivalence basis footnoted | 2 dp |
| Low-tenor grade | `850 ppm` | 0 dp |
| Tonnage | `170.2 Mt`, `320 kt`, `12,500 t` | 1–2 dp for Mt |
| Contained metal | `805 kt Cu`, `259 koz Au`, `1.2 Moz` | 0–2 dp |
| Length / depth | `12 m`, `88 m` (metric only) | 0–1 dp |
| Intercept | `18 m at 3.2 g/t Au from 64 m` | per above |
| Share price | `A$0.265` | 3 dp below one dollar |
| Market cap | `A$42M` | per the Core currency rules |

Pair every figure with its unit and source. A tonnage without a JORC classification doesn't ship.

### Domain components
- **Competent Person statement block:** drops into the Core disclaimer shell:
  ```html
  <aside class="hvr-disclaimer">
    <p>Competent Person Statement … [name] … consents to the inclusion …</p>
    <p>Forward-looking statements … may differ materially …</p>
  </aside>
  ```
- **JORC classification tag:** every resource or reserve figure carries its classification and the code edition, for example `170.2 Mt (Indicated & Inferred, JORC 2012)`. Never a bare tonnage.
- **Metal-equivalent note:** any CuEq figure links to a footnote giving the prices, recoveries and formula used.

### Compliance-aware design — mining
The governing rule:

> **Every visual choice may encode data, never a verdict.** If a colour, arrow, badge, ranking or highlight implies "good", "bad", "buy", "winner" or relative merit, it fails, exactly as the equivalent words would.

**Not allowed**
- ❌ Traffic-light (RAG) status on an entity's metrics (green = good, red = bad).
- ❌ Green/red up-down arrows used as endorsement. A price *change* is data; a green ▲ that reads as a "positive call" is not.
- ❌ "Top pick", "Outperform", "Buy" or "Undervalued" badges, stars or scores.
- ❌ Leaderboards or league tables that rank named entities by merit.
- ❌ Conditional formatting that scores an entity, such as shading a company's row red because a number is "low".

**Allowed (data emphasis, not merit)**
- ✅ Sequential colour by the magnitude of a neutral quantity, such as a grade heatmap on the copper ramp. The colour maps to the number, not a judgement.
- ✅ Emphasis on the subject: accenting a figure because it's what the document is about, applied evenly and not to flatter.
- ✅ Factual change shown with a sign and a neutral cue (`−1.8%`), not a green/red moral signal.
- ✅ Thematic or commodity content has more room. Outlook colours and directional arrows on a commodity price are fine, because no named entity is being rated.

**Pre-publish checklist (mining)**
1. Does any colour, arrow or badge on a named entity imply merit? If so, neutralise it.
2. Does every resource or reserve figure carry its JORC classification and edition, and does every CuEq figure carry its basis?
3. Is every figure that can change stamped with an as-at date, and every named-entity claim sourced?
4. Are the Competent Person and forward-looking statements present and at least 12px?
5. Is colour never the only signal, and is no internal gating state (PASS/FIX/BLOCK) visible?
6. Is brand copper never used as body-size text on white, never copper text on teal, and white text on copper only when large and bold?

---

**Changelog — v0.1.** First version.
- **From `HVR_Style_Guide.pdf`:** the palette, typeface and logo system. Primary colours are teal `#0E4D5C`, copper `#C8762B` and white; secondary colours are slate `#16242B` and mist `#C9D3D8`; the typeface is Source Sans 3.
- **From the StoriBot multi-industry template v0.5:** the structure, web implementation, tokens, chart system, spacing, formatting rules and the Mining (ASX) compliance pack, all re-derived for the HVR palette.
- **Changes from the template forced by the palette:**
  - Brand copper passes 3 : 1 but not 4.5 : 1 on white (≈ 3.5 : 1). It's fine for large text, UI and charts, with `#A25A17` / `#8A4B12` as the UI and text steps.
  - The copper-on-slate pairing (≈ 4.6 : 1) is the approved high-contrast combination, and copper on teal (≈ 2.7 : 1) is ruled out.
  - Mist `#C9D3D8` is decorative only, with `#5B6770` as its text step.
  - Teal needs no text substitution (≈ 9.4 : 1).

*Prepared for Halvorsen Resources (ASX: HVR), a fictional company. Where the source guide is silent, the clear-space, minimum-size, neutral-ramp, chart and spacing values are working defaults. Contrast figures were calculated with the WCAG 2.x relative-luminance formula; check final pairings with a checker (e.g. WebAIM) before shipping. Any change to how named entities or the regime are handled needs a compliance check.*
