# Motion

Two kinds of work live here: motion inside an interface, and motion pieces
(product films, kinetic type, animated charts, loops). Read the first part for
prototypes and pages, both parts for `make: motion`.

## Part 1: interface motion

### What motion is for

Every animation needs one of these jobs. If it has none, cut it.

- **Orientation:** where something came from and where it went (a sheet rising
  from the button that opened it).
- **Feedback:** the system heard you (a press, a toggle, a saved state).
- **Continuity:** the same object across two states or screens (a card
  expanding into its detail).
- **Attention:** one thing changed that matters (a new message, a total that
  updated). Use sparingly; attention is spent, not earned.

### Tokens

| Token | Duration | Easing | Typical use |
|---|---|---|---|
| instant | 100 ms | `ease-out` | Hover, press, color and opacity feedback |
| quick | 150 to 200 ms | standard `cubic-bezier(0.2, 0, 0, 1)` | Toggles, checkboxes, tooltips, small moves |
| base | 250 to 300 ms | enter: decelerate `cubic-bezier(0, 0, 0, 1)` or standard; exit: accelerate `cubic-bezier(0.3, 0, 0.8, 0.15)` | Sheets, menus, panels, cards |
| large | 400 to 500 ms | emphasized `cubic-bezier(0.05, 0.7, 0.1, 1)` | Screen changes, shared elements, first-run moments |

- Things entering decelerate (fast start, soft landing). Things leaving
  accelerate. Things moving within the screen use the standard curve.
- Exits run about 20 to 30 % shorter than entrances: people care about what's
  arriving.
- Distance sets duration. A tooltip moving 8 px is quick; a sheet crossing the
  screen is base; a full screen change is large. On a large display add 10 to
  20 %; on a watch, cut by a third.
- Nothing in an interface should take longer than 500 ms unless it is showing
  real progress.

### Springs

Springs feel physical and handle interruption well. Use them for things people
drag or throw (sheets, cards, carousels).

- A good default: response about 0.35 s with a damping ratio of 0.8 to 0.9 (a
  little settle, no wobble). Lower damping only for playful moments.
- In CSS, approximate a spring with `linear()` easing generated from the spring
  curve; in JavaScript use the Web Animations API or a small spring solver.
- A dragged object should follow the finger 1:1, then hand its velocity to the
  spring when released.

### Choreography

- One lead element moves first; the rest follow. Never move everything at once.
- Stagger lists by 20 to 40 ms per item and cap the whole sequence at 400 ms.
  After about 8 items, show the rest together.
- Keep direction consistent: forward in a flow moves left (content arrives from
  the right), back moves right. Sheets come from the edge they belong to.
- Shared elements: animate the object that persists (an image, a title) and
  cross-fade the rest. The View Transitions API
  (`document.startViewTransition`) does this for same-page state changes and,
  in supporting browsers, across pages.
- Reorders and layout changes: measure, then animate from the old position to
  the new one with `transform` (the FLIP technique), never by animating
  `top`, `left`, `width` or `height`.

### Patterns

| Moment | Motion |
|---|---|
| Button press | Scale to 0.97 and darken slightly, 100 ms; release springs back. |
| Toggle | Thumb slides with the standard curve, 150 ms; color follows. |
| Menu or popover | Fade plus 4 to 8 px of movement from its anchor, 150 to 200 ms; exits faster. |
| Bottom sheet | Rises with decelerate or a spring, 250 to 300 ms; the scrim fades in alongside. |
| Toast | Slides in from its edge, 200 ms, stays 4 to 6 s (longer if it has an action), leaves faster. |
| Screen push | New screen enters from the right by 30 to 100 % of its width with a fade; old one shifts left by a fraction. 300 to 400 ms. |
| Number change | Count up over 300 to 600 ms with tabular figures, or roll digits. Not for every change. |
| Skeleton | A slow, low-contrast shimmer (about 1.5 s) or none at all. |
| Success | One clear moment (a check drawing in over 300 ms), then stillness. |

### Respect and performance

- `prefers-reduced-motion: reduce`: replace movement with fades or instant
  changes, stop autoplaying loops and parallax, keep essential feedback.

  ```css
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
      scroll-behavior: auto !important;
    }
  }
  ```

  Then add back the fades that carry meaning.
- Animate `transform` and `opacity`. They stay on the compositor and hold 60 fps.
  Use `will-change` only on elements about to animate, and remove it afterwards.
- Never block input on an animation. Make animations interruptible: a second
  tap reverses a sheet mid-flight instead of waiting for it.
- Nothing flashes more than three times a second.

## Part 2: motion pieces

### Workflow

1. **Beat sheet.** List the beats with timecodes and one line each: what's on
   screen, what moves, what the viewer should feel or understand. Total the
   length before building.
2. **Style frames.** Fix two or three still frames first: type, color,
   composition. Motion can't rescue a weak frame.
3. **Animatic.** Block the timing with simple shapes. Get the rhythm right before
   the detail.
4. **Build and polish.** Add easing, overlap and secondary motion last.

### Formats

| Use | Size | Frame rate |
|---|---|---|
| Presentation or web film | 1920 × 1080 | 30 or 60 fps |
| Vertical social | 1080 × 1920; keep text out of roughly the top 250 px and bottom 350 px, where apps put their interface | 30 fps |
| Square social | 1080 × 1080 | 30 fps |
| Interface demo | the device's size at 2× | 60 fps |
| Cinematic look | any | 24 fps |

### Principles that matter most on screen

- **Timing and spacing:** fewer, longer holds read as confident; many quick moves
  read as nervous. Leave rests between beats.
- **Ease everything.** Linear motion only for constant things (a ticker, a
  rotating loader). Entrances: expo or quint out. Exits: in. Swings: in-out.
- **Hierarchy in time:** one thing moves at a time, the most important first. The
  eye can follow one motion.
- **Anticipation and follow-through:** a small move back before a big move, a
  small settle after it. Keep them subtle in product work.
- **Overlap:** parts of a group start and finish at slightly different times,
  so motion feels like one gesture rather than a block.
- **Arcs:** natural paths curve. A cursor moving between two points takes a
  gentle arc with an ease-in-out, not a straight line at constant speed.
- **Rhythm:** with music, cut and accent on the beat. One beat lasts 60 ÷ BPM
  seconds (0.5 s at 120 BPM).
- **Transitions:** prefer cuts and match cuts. Use pushes, masks and morphs when
  they show a relationship between the two frames.

### Kinetic type

- Hold each line long enough to read twice: about 0.4 s a word, never under
  1.2 s.
- Break lines on meaning, one idea per line, and change lines on the beat.
- Motion should match the word: "drop" falls, "grow" scales. Don't make every
  word fly in from a different direction.
- Letter-by-letter staggers only for short words; animate long lines by word
  or by line.
- A few large words beat many small ones. Set tracking and line height on
  purpose; defaults look like defaults at display sizes.

### Product UI in motion

- Build the interface as real HTML at real size, then film it with a camera:
  slow push-ins of 2 to 5 % scale, gentle pans, depth from slight parallax.
- Cursor: eased arcs, a short pause before each click, a visible press state.
- Typing: 8 to 14 characters a second with slight variation, and a pause before
  pressing enter.
- Show one interaction at a time and let the result land before the next.

### Charts in motion

- Build in order: frame and axes, then data, then the annotation that makes the
  point. Hold on the annotation.
- Grow bars from the baseline; draw lines from left to right; count numbers up
  with tabular figures.
- Keep object constancy when data changes: the same bar moves to its new value
  rather than disappearing and reappearing.

### Loops

- The last frame matches the first. Drive the loop from time modulo the duration.
- Loops of 4 to 12 s feel calm; under 2 s they feel restless.

## The seekable timeline

Drive every motion piece from one clock, so any moment can be rendered on its
own. That makes it previewable, scrubbable and renderable to video frame by
frame.

```html
<script>
const DURATION = 12;                       // seconds
const clamp = (x) => Math.min(1, Math.max(0, x));
const span = (t, start, length) => clamp((t - start) / length);
const ease = {
  out: (x) => 1 - Math.pow(1 - x, 3),
  expoOut: (x) => (x === 1 ? 1 : 1 - Math.pow(2, -10 * x)),
  inOut: (x) => (x < 0.5 ? 4 * x * x * x : 1 - Math.pow(-2 * x + 2, 3) / 2),
};

// Everything on screen is a pure function of t. No Date.now(), no unseeded random.
function render(t) {
  const title = document.querySelector('#title');
  const a = ease.expoOut(span(t, 0.4, 0.8));
  title.style.opacity = a;
  title.style.transform = `translateY(${(1 - a) * 24}px)`;
}

window.seek = (t) => render(t);            // renderers call this once per frame

const params = new URLSearchParams(location.search);
document.fonts.ready.then(() => {
  if (params.has('t')) return render(Number(params.get('t')));
  let start;
  const tick = (now) => {
    start ??= now;
    render(((now - start) / 1000) % DURATION);
    requestAnimationFrame(tick);
  };
  requestAnimationFrame(tick);
});
</script>
```

- Need randomness? Use a seeded generator (for example mulberry32 with a fixed
  seed) so every render matches.
- CSS or Web Animations? Create them paused and set
  `animation.currentTime = t * 1000` inside `render`.
- Add a small preview bar while building: play and pause, a scrubber, the
  current time, and space to toggle. Remove it, or hide it with `?t=`, for
  rendering.
- Rendering to video: if the project uses HyperFrames (HTML to video, with its
  own agent skills, `npx skills add heygen-com/hyperframes`) or Remotion,
  follow their conventions. Otherwise capture frames with a headless browser
  calling `seek(i / fps)` for each frame, then encode:
  `ffmpeg -framerate 60 -i frames/%05d.png -c:v libx264 -pix_fmt yuv420p -crf 18 out.mp4`.
