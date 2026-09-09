# STEADI — Every meal, steadier.

> *Independence, served daily.*

A scroll-driven 3D product website for **STEADI**, an anti-tremor stabilising
cutlery handle for people living with essential tremor and Parkinson's.

Built as a **single `index.html`** — no framework, no build step. The product
model is generated entirely in code with three.js and tells its own story as
you scroll: the shell opens, the electronics lift out, and every part returns
to the dock.

**Live:** <https://aryamanironman.github.io/steadi-site/>

## Features

- **Scroll choreography** — one continuous camera journey through eight
  chapters: hero → shell → liner → gimbal → sensors → power → dock → finale.
  Camera, explode offsets and lighting are keyframed against section centres
  and eased with frame-rate-independent damping.
- **Procedural 3D product** — the handle, dock, servos, PCB, IMU, battery and
  wiring are all built from lathe/box/capsule primitives in code.
- **Part callouts** — hover any component for its name; click to pin a
  dot + leader-line card explaining what it does.
- **X-ray mode** — toggle turns the cream shell to glass so the guts show.
- **Utensil switcher** — spoon / fork / knife crossfade on the model at the
  finale, with a silicone-liner glow flash.
- **Interactive spec sheets** — hovering a fact row lights its part up in the
  model (per-part emissive clones).
- **Feel-good details** — drag to spin, mouse parallax, scroll-velocity lean,
  keyboard chapter hops (J/K, arrows), reduced-motion fallbacks, mobile
  framing.

## Run locally

ES-module importmaps are unreliable over `file://`, so serve the folder:

```
python -m http.server 4173
```

then open <http://localhost:4173>.

## Debug params

Handy for screenshots and QA:

| Param | Effect |
| --- | --- |
| `?p=0..1` | Jump scroll progress (deterministic) |
| `&noorbit` | Disable the hero auto-orbit |
| `&utensil=fork\|knife\|spoon` | Force a finale utensil head |
| `&xray` | Start with the shell in X-ray mode |

## Tech notes

- three.js r170 via CDN importmap; `RoomEnvironment` + PMREM for lighting,
  ACES filmic tone mapping, soft shadows.
- Camera stops are resolved from the `.section` elements at layout time — the
  choreography indexes sections by order, so adding/removing a section means
  re-checking `KEYFRAMES` / `updateExplode`.
- Works in any modern browser (Chromium/Firefox/Safari), desktop and mobile.
