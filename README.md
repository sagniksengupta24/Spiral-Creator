# Spiral Studio 🌀

https://sagniksengupta24.github.io/Spiral-Creator/ 

> A high-performance, zero-dependency parametric generative art studio built with vanilla HTML5 Canvas, harmonic mathematics, and a glassmorphic UI.

---

## Overview

**Spiral Studio** transforms abstract parametric equations into interactive generative artwork. Built entirely with native web technologies—no heavy frameworks, bundlers, or third-party graphing libraries—it pairs mathematical curve modeling with a fluid, hardware-accelerated rendering pipeline.

---

## Key Features

* **6 Parametric Mathematical Engines:** Switch on the fly between Archimedean, Logarithmic, Fermat (Phyllotaxis), Maurer Roses, Hypotrochoids (Spirographs), and Clothoid wave spirals.
* **Hardware-Accelerated Retina Rendering:** Automatic device pixel ratio (`window.devicePixelRatio`) scaling for crisp lines on 4K, 5K, and Retina displays.
* **Dual-Pass Glow Compositing:** Multi-pass bloom architecture layering a diffused glow beneath a sharp vector core.
* **Interactive Camera Controls:** Smooth drag-to-pan and wheel-to-zoom navigation across an infinite 2D canvas plane.
* **Live Harmonic Modulation:** Tweak divergence angles, harmonic frequencies, scale, and resolution with zero frame drops at 60 FPS.
* **Production-Ready Exports:**
* **4K UHD Raster (.PNG):** Off-screen canvas rendering at $3840 \times 3840$ resolution.
* **Infinite-Resolution Vector (.SVG):** Raw SVG path generation for plotters, laser cutters, and vector design tools.


* **Zero Dependencies:** Single-file distribution, zero `npm install`, zero build steps.

---

## Mathematical Models

| Model | Polar / Parametric Form | Visual Behavior |
| --- | --- | --- |
| **Archimedean** | $r = a + b\theta$ | Uniform radial spacing with harmonic wave distortion |
| **Logarithmic** | $r = a e^{b\theta}$ | Natural equiangular spiral (Nautilus shell, hurricane vortex) |
| **Fermat / Phyllotaxis** | $r = c\sqrt{n}, \quad \theta = n \times 137.508^\circ$ | Golden-ratio distribution observed in sunflower disc florets |
| **Maurer Rose** | $r = \sin(n\theta)$ | Interconnected geometric chords forming star polygons |
| **Hypotrochoid** | $x = (R-r)\cos\theta + d\cos(\frac{R-r}{r}\theta)$<br>

<br>$y = (R-r)\sin\theta - d\sin(\frac{R-r}{r}\theta)$ | Classical mechanical roulette spirograph trajectories |
| **Clothoid Wave** | $\theta = \frac{s^2}{2a^2}$ (modulated) | Curvature varies linearly with curve length; ribbon-like folds |

---

## Getting Started

### Local Setup

Because Spiral Studio has zero external dependencies, running it locally requires no runtime or package manager:

```bash
# Clone the repository
git clone https://github.com/sagniksengupta24/Spiral-Creator.git

# Navigate to the folder
cd Spiral-Creator

# Open directly in your browser
open index.html  # On macOS
# or start a quick local server
python3 -m http.server 8000

```

Visit `http://localhost:8000` in your browser.

---

## Controls & Navigation

| Input | Action |
| --- | --- |
| **Left Click + Drag** | Pan across the infinite canvas plane |
| **Scroll Wheel / Pinch** | Zoom in / Zoom out ($0.1\times$ to $15\times$) |
| **Formula Selector** | Select the active mathematical generative algorithm |
| **Resolution Slider** | Adjust vertex density ($100$ to $6,000$ points) |
| **Divergence Slider** | Modify the angular step (try $137.5^\circ$ for golden phyllotaxis) |
| **Harmonics Slider** | Add sinusoidal frequencies to the radial vector |
| **Palette Grid** | Apply pre-computed color gradients (Aurora, Cyberpunk, Sunfire, etc.) |
| **Animate (▶ / ⏸)** | Toggle real-time phase-shift animation loop |
| **🎲 Randomize** | Generate a randomized parametric aesthetic |
| **4K PNG / Vector SVG** | Trigger high-resolution rendering and download |

---

## Performance Architecture

```
User Input / RAF Loop (60 FPS)
              │
              ▼
   State Matrix (Pan, Zoom, Phase t)
              │
              ▼
Parametric Computation Kernel (calculatePoints)
              │
     ┌────────┴────────┐
     ▼                 ▼
Glow Bloom Layer    Sharp Vector Core
(shadowBlur + a)   (Round Cap/Join)
     │                 │
     └────────┬────────┘
              ▼
Composite to Retina Canvas (dpr-scaled)

```

1. **Decoupled Math Kernel:** Coordinate computation uses clean mathematical mappings without mutating DOM nodes or relying on global browser state.
2. **Sub-Pixel Crispness:** All vector offsets are normalized around canvas center offsets ($W/2, H/2$) with transformation matrices applied via `ctx.setTransform` and `ctx.scale`.
3. **Off-Screen Export Pipeline:** 4K downloads are rendered onto an isolated headless canvas memory buffer to avoid viewport stutter or resolution scaling artifacts.

---

## Project Structure

```
Spiral-Creator/
├── index.html        # Complete standalone application (Structure, Styles, Engine)
├── README.md         # Documentation & mathematical overview
└── LICENSE           # MIT License

```

---

## Contributing

Pull requests are welcome. If you would like to implement additional mathematical curves (e.g., Lissajous knots, Lorenz attractors, or Ulam prime spirals):

1. Fork the project (`git checkout -b feature/NewSpiralModel`).
2. Add your parametric formula inside the `calculatePoints()` function in `index.html`.
3. Add the formula name to the `#selModel` dropdown.
4. Commit your changes and open a Pull Request.

---

## License

Distributed under the **MIT License**. See `LICENSE` for more information.
