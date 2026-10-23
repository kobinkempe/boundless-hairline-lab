# bound.less SVG Hairline Lab

A focused browser experiment for a difficult rendering question: why can paths with the same apparent thickness disappear when their local SVG coordinate scale changes?

![Live transformed-SVG grid](docs/screenshots/desktop.jpg)

## Run

```sh
python -m http.server 8000 --bind 127.0.0.1
```

Open http://127.0.0.1:8000 and choose the live SVG grid. No package installation, backend or API key is required.

## Experiment

`experiments/chrome.html` varies target thickness and local coordinate scale while a group transform compensates to preserve on-screen dimensions. `chrome2.html` supplies another comparison. `chrome3.html` reduces the case to four scales at a target width of 0.165 CSS px. `experiments/index.html` is a canvas measurement control.

The original investigation identified a disappearing-path region around that width in its tested Chrome environment. This is a historical observation, not a universal browser threshold. Canvas rasterization can disagree with live SVG paint, so a canvas pixel count alone is an insufficient visual oracle. Capture the actual page and compare at a known browser zoom and device pixel ratio.

## Why it belongs in the portfolio

This isolates a real infinite-canvas failure into a small, shareable experiment. It shows numerical reasoning, negative controls and attention to what a test actually measures. It was developed with AI assistance; there is no model at runtime.

The portfolio cleanup adds navigation and explanation while retaining the experiment geometry. Static links and inline JavaScript are checked; Chrome screenshots confirm the live grids render. Performance, paint and device-specific behavior require fresh measurements on each target browser. [Publication review](PUBLICATION_REVIEW.md).
