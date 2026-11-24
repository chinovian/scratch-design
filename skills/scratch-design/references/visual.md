# Visual design

Read before building a page, a prototype or a system.

## Direction before details

- Name the look in one line before touching layout, then hold to it. "Quiet
  utility", "editorial and generous", "dense instrument panel" each imply
  different type, spacing and color.
- Take one specific thing from each reference image: its palette, its type
  mood, its density, its use of space, its photography. Write down what you're
  taking and what you're leaving.
- If the project has a design system or brand, it wins over anything here.

## Typography

- **Families:** one is usually enough. Add a second only for contrast that the
  content needs (a serif for long reading, a mono for code or data). Pick type
  for the subject: a booking tool and a literary magazine shouldn't share a face.
- **Scale:** 5 to 7 sizes from a ratio. 1.2 for dense interfaces, 1.25 to 1.333
  for pages, larger for editorial display. Round to whole pixels. Example at
  1.25: 12, 14, 16, 20, 25, 31, 39.
- **Body:** 16 px or more on screens (17 to 18 px for long reading), line height
  1.4 to 1.6, 45 to 75 characters a line (66 is the sweet spot).
- **Display:** line height 1.0 to 1.2, tracking tightened by 1 to 2 % at large
  sizes. Use `text-wrap: balance` on headings and `text-wrap: pretty` on
  paragraphs to avoid lone words.
- **Small text:** 12 px is the floor for anything people must read. All-caps
  labels get 4 to 8 % extra tracking and stay short.
- **Numbers:** tabular figures (`font-variant-numeric: tabular-nums`) in tables,
  prices, timers and charts. Align decimals.
- **Weight:** two or three weights do the work. Hierarchy from weight should
  survive in grayscale.
- **Loading:** preconnect to the font host, load only the weights you use, and
  set `font-display: swap` with a close fallback so text doesn't jump.

## Color

- Define roles first: background, surface, raised surface, text, muted text,
  border, accent, text on accent, focus, danger, warning, success. Components
  use roles, never raw hex.
- Mostly neutrals. Tint the neutrals slightly toward the accent's hue so the
  palette feels like one family.
- One accent, used for the primary action, links, focus and selection. If
  everything is accented, nothing is.
- Build ramps in OKLCH: hold hue, step lightness evenly, and lower chroma at the
  very light and very dark ends.
- Contrast: text at least 4.5:1, large text and UI parts at least 3:1. Check
  muted grays especially; light gray on white is the most common failure.
- Semantic colors (danger, success) mean something. Don't use them for
  decoration.
- Dark theme: not an inversion. Base around `#121212` to `#1C1C1E` rather than
  pure black; raised surfaces get lighter, not shadowed; accents lose some
  chroma; check every contrast pair again.

## Space and layout

- A 4 px base with steps of 4, 8, 12, 16, 24, 32, 48, 64 and 96. Use few steps
  and use them consistently.
- Proximity is grouping: space inside a group is smaller than space between
  groups. If two things are related, move them closer before you add a box.
- Grids: 4 columns with 16 to 20 px margins on phones, 8 on tablets, 12 on
  desktop with 24 px gutters. Content width around 1200 to 1280 px, text
  columns narrower.
- Align to edges, not centers, for anything people read. Center only short,
  standalone things.
- Fewer containers. Use space and alignment to group; reach for a border or a
  card only when grouping needs more.
- Nested corners: outer radius equals inner radius plus padding. Keep one radius
  family (for example 4, 8 and 12) and don't round everything to the maximum.

## Hierarchy

- Squint: the first, second and third things you see should be the most
  important, in that order.
- Use the fewest levers that work: size, then weight, then color, then space.
  Don't use all four on one heading.
- One primary button per view. Secondary actions are quieter: outline or text.
- Shorten before shrinking. Cutting words beats smaller type.

## Imagery and icons

- Every image has a job: show the product, set a mood, explain something. A
  picture that does none of these goes.
- Give images consistent aspect ratios and treatments. Art-direct crops for each
  breakpoint when the subject matters.
- Set `width` and `height` (or `aspect-ratio`) so nothing shifts while loading.
  Use modern formats and `loading="lazy"` below the fold.
- No stock clichés (handshakes, people pointing at screens) and no AI-generated
  people presented as real.
- Icons from one set, one stroke width (1.5 to 2 px at 24 px), aligned by eye
  rather than by bounding box. An icon without a label needs one in its
  `aria-label` and usually a visible label too.

## Finishing detail

- Borders: 1 px, low contrast against their surface. Hairlines between list
  rows rather than boxes around them.
- Shadows: soft and layered, from one light source above, and only on things
  that float (menus, sheets, dialogs). Not on cards that sit on the page.
- Focus rings: 2 px in the accent, offset 2 px, on every interactive element.
- States for every control: rest, hover, pressed, focus, disabled, loading.
- Empty, error and success states get the same care as the main screen.
- Check the page at 320 px, 768 px, 1280 px and 1920 px, in light and dark, with
  the longest realistic content.

## Tells of machine-made design (avoid)

- Purple-to-blue gradients, glows, glass and noise used as decoration.
- The same 16 to 24 px radius on everything, and cards inside cards.
- Colored left borders on callouts. Emoji as icons. Icons in colored circles.
- Every section centered with a small label, a big headline, a subhead and three
  cards in a row.
- Copy that could describe any product ("Unlock the power of…",
  "Seamlessly…") and numbers nobody measured.
- Everything fading up on scroll with the same easing.
- Shadows on every surface. Centered paragraphs. Gray text too light to read.
