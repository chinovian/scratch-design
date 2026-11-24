# Reviewing work

Use this to check your own build before showing it, and as the format when
`intent.make` is `review`.

## Severity

| Level | Meaning | Rule |
|---|---|---|
| Blocker | Someone can't finish the task, loses data, or is shut out (inaccessible). | Fix before showing anything. |
| Major | It slows people down, confuses them, breaks consistency, or looks unfinished. | Fix before showing, unless the brief rules it out. |
| Minor | Polish: a misaligned edge, an uneven gap, a weak word. | Fix what you can; list the rest. |

## How to look

- Look at the real thing: render it, screenshot it, click through it. Reading
  your own code is not reviewing.
- Check at the sizes that matter: 320 px, 390 px, 768 px, 1280 px and wider for
  pages; the target device for prototypes; full frame and phone preview for
  motion.
- Check light and dark, the longest content, an empty state and an error.
- Use the keyboard alone once. Turn on reduced motion once.

## Checklist

### Task and flow
- [ ] From the first frame, the main task can be finished without help.
- [ ] Every flow trigger in the hand-off works, and back works.
- [ ] One primary action per screen, and it's the right one.
- [ ] Choices carry across screens.
- [ ] Mistakes can be undone or corrected without starting over.

### States
- [ ] Empty, loading, error and success are designed, not default.
- [ ] Long names, zero, one and many items hold up.
- [ ] Errors keep what people typed and say how to fix the problem.

### Hierarchy and layout
- [ ] The squint test passes: the most important thing reads first.
- [ ] No more than three or four type sizes show at once.
- [ ] Edges align to one grid. Spacing comes from the scale and shows grouping.
- [ ] Nothing overflows, overlaps or gets cut off at any size checked.

### Type and color
- [ ] Body text is 16 px or more, with a comfortable measure and line height.
- [ ] Every text pair meets 4.5:1; large text and controls meet 3:1.
- [ ] One accent, used for action and focus. Semantic colors only mean something.
- [ ] Numbers that compare use tabular figures.

### Interaction and access
- [ ] Every control is a real control, reachable and usable by keyboard.
- [ ] Focus is always visible. Touch targets are 44 px or more.
- [ ] Inputs have labels; icon buttons have names; images have `alt`.
- [ ] Nothing depends on color alone or on hover alone.

### Motion
- [ ] Every animation has a job and stays within the duration tokens.
- [ ] Nothing blocks input or loops for no reason.
- [ ] Reduced motion swaps movement for fades or instant changes.
- [ ] For motion pieces: each line of text holds long enough to read twice, one
      thing moves at a time, and any frame renders on its own via `seek(t)`.

### Data
- [ ] Each chart's title states the answer; units, range and source are stated.
- [ ] Bars start at zero; series are labeled directly; color does one job.

### Craft
- [ ] None of the tells: decorative gradients, uniform big radii, cards in
      cards, left-border callouts, emoji icons, three-card rows, vague copy,
      invented numbers.
- [ ] Copy is specific to this product and these people.
- [ ] The fidelity setting was respected, and the brief is met.

## Format for a design review (`make: review`)

1. **Summary:** two or three sentences on how well the frames serve the job.
2. **What works:** up to three things to keep, each tied to a frame.
3. **Issues:** a table with frame, issue, why it matters, the fix and severity,
   most severe first. Be specific: "Frame 2: the time slots read as one block
   because they have no gaps; add 8 px between slots and show sold-out slots
   as disabled with the word 'Full'", not "improve spacing".
4. **The flow, revised:** if steps should merge, split or reorder, show the new
   sequence as a numbered list.
5. **Quick wins:** the three changes that would help most for the least work.

Point to evidence (a frame, a hotspot, a measured contrast) rather than taste.
When it is taste, say so.
