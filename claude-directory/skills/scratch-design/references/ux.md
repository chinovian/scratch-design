# UX and interaction

Read before building a prototype, a page or a review.

## Start from the job

- Write the job in one sentence: "A member books a day pass for Saturday morning
  with rental shoes, in under a minute." Every screen either moves that job
  forward or gets cut.
- Count the steps from the first frame to done. Then try to remove one: merge two
  screens, choose a sensible default, or skip a question the system can answer.
- Know who arrives where. A first-time visitor and someone returning need
  different first screens. Say which one you designed for.

## The flow

- One primary action per screen. A second action is visibly secondary. A third
  goes in a menu.
- Always show where the person is, what they've already chosen and what happens
  next. In a multi-step flow, show the step and the total ("2 of 4") and let
  people go back without losing anything.
- Branches are real paths. If a frame has two exits, both work in the prototype.
- Dead ends are bugs. Every screen has a way forward or back.
- Put choices where they matter. Ask for payment details at payment, not at
  sign-up.

## States

Design every state the flow can reach, not only the happy one:

| State | What good looks like |
|---|---|
| Empty | Says what will appear here and offers the action that fills it. |
| Loading | A skeleton in the real layout if it takes over 300 ms; a progress bar with words if over 2 s. No spinner on its own for long waits. |
| Partial | Shows what's there and loads the rest in place, without layout jumps. |
| Error | Says what happened in plain words, keeps everything the person entered, and offers the next step ("Try again", "Use another card"). |
| Success | Confirms the result with specifics ("Saturday 10:00, 2 passes, shoes size 42") and the obvious next step. |
| Edge | Long names, zero, one and many items, slow networks, no permission granted. |

## Feedback and response time

- Within 100 ms, acknowledge every press: a pressed state, a color change.
- Within 1 s, show the result or a sign of progress.
- Past 10 s, let people leave and come back, and tell them when it's done.
- Use optimistic updates for things that almost always succeed (a like, a
  reorder), with a quiet rollback if they fail.
- Prefer undo to "Are you sure?". Keep confirmation for things that can't be
  undone, and name the object and the consequence in the button: "Delete
  board", not "OK".

## Forms

- One column. Labels above fields, never only placeholders.
- Ask for as little as possible. Mark the few optional fields, not the many
  required ones.
- Use the right `type`, `inputmode` and `autocomplete` (`email`, `tel`,
  `one-time-code`, `cc-number`, `postal-code`) so phones show the right
  keyboard and browsers can fill things in.
- Validate when someone leaves a field, not on every keystroke. Put the message
  beside the field and say how to fix it ("Use a date after today").
- Don't disable the submit button without saying why. Let people submit, then
  point to what's missing.
- Group related fields (date and time, card number and expiry) and keep the
  order people expect.

## Navigation

- Phone: a bottom tab bar for 3 to 5 top-level places, a back control at the top
  left, and sheets for focused tasks that keep context.
- Desktop: persistent navigation for the main places, breadcrumbs only for deep
  hierarchies, and keyboard shortcuts for frequent actions, shown in menus and
  tooltips.
- Links go to places; buttons do things. Don't mix them up in markup or style.

## Phone ergonomics

- The bottom third of the screen is easiest to reach. Put the primary action
  there, full width or close to it.
- Touch targets of at least 44 × 44 px, with 8 px between them.
- Respect safe areas (`env(safe-area-inset-*)`) and the on-screen keyboard: the
  focused field and its primary action stay visible.
- Gestures are shortcuts, never the only way. A swipe to delete also has a
  visible delete.

## Writing interface copy

- Say what happens: "Book 2 passes", "Save changes", "Send invite".
- Sentence case everywhere. No ALL CAPS paragraphs.
- Front-load the words people scan for. "Shoes: rent for $5", not "If you'd
  like to rent shoes, it's $5".
- Errors blame the situation, not the person, and offer a way out.
- Use the same word for the same thing on every screen.
- Leave placeholders like `[PRICE]` where facts are missing. Never invent them.

## Accessibility (as part of the design, not after)

- Contrast at least 4.5:1 for text, 3:1 for large text (24 px, or 19 px bold)
  and for controls and chart marks against their background.
- Every control is a real `button`, `a`, `input`, `select` or `textarea`, usable
  by keyboard in a sensible order, with a visible focus ring.
- Every input has a label. Icon-only buttons have an `aria-label`.
- Don't use color alone to show state. Add a word, an icon or a pattern.
- Respect `prefers-reduced-motion` and `prefers-color-scheme`.
- Headings in order. Landmarks (`header`, `nav`, `main`, `footer`). Page titles
  that say where you are.
- Images that carry meaning get `alt` text. Decorative ones get `alt=""`.

## Heuristics for a quick check

1. Can people see what's going on?
2. Does it speak their language?
3. Can they undo and leave?
4. Is it consistent with itself and with platform conventions?
5. Does it prevent errors before it explains them?
6. Can people recognise options instead of remembering them?
7. Are there shortcuts for frequent users?
8. Is everything on screen needed?
9. Do errors say how to recover?
10. Is help there when it's needed, in context?

## Prototypes that test well

- Use realistic content: real-length names, prices with the right format,
  dates relative to today.
- Keep state across screens, so a choice on frame 2 shows up on frame 4.
- Make every flow trigger in the hand-off work, and the browser back button too.
- Include a way to reset, so the next person starts clean.
