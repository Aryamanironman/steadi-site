# STEADI — product site

A scroll-driven 3D product website for STEADI, an anti-tremor stabilising
cutlery handle. Single `index.html`, no build step — three.js loads from a CDN
importmap.

## Run locally

ES-module importmaps are unreliable over `file://`, so serve the folder:

```
python -m http.server 4173
```

then open <http://localhost:4173>.

## Debug params

| Param | Effect |
| --- | --- |
| `?p=0..1` | Jump scroll progress (deterministic screenshots) |
| `&noorbit` | Disable the hero auto-orbit |
| `&utensil=fork\|knife\|spoon` | Force a finale utensil head |
| `&xray` | Start with the shell in X-ray mode |

## Interactions

Drag to spin · scroll to explode and reassemble · hover a spec row to light its
part · hover/click any component for a named callout · X-ray toggle (top
right) · J/K or arrow keys to hop chapters.
