# ✨ Magic Hands

Real-time hand tracking with magical visual effects, built with [MediaPipe Tasks Vision](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker) and plain Canvas 2D — no frameworks, no build step, single HTML file.

## Demo

Open `index.html` via any local HTTP server (e.g. `python3 -m http.server 8080`) and allow camera access.

> **Note:** Must be served over HTTP/HTTPS (not `file://`) for camera access and WASM to work.

## Effects

| Mode | Description |
|------|-------------|
| 🕸 **Web** | Glowing lines between all fingertips + hand skeleton |
| 🌀 **Warp** | Blurred video strips between fingers with animated turbulence strands |
| ⚡ **Lightning** | Fractal electric bolts between fingers — within hand and across both hands |
| ✨ **Particles** | Sparks that react to hand speed, inherit velocity, and scatter when your hand pushes through them |
| 🔥 **Trails** | Glowing motion trails following each fingertip |
| 🦴 **Rigging** | Every hand landmark connected to every other — 210 lines per hand |
| 🎆 **Fireworks** | Slow = light trail; sudden fast flick = particle explosion burst |
| 🔮 **Orbs** | Smooth-lagging orbs with orbiting ring particles; opposite hand orbs connect with beams |
| 🌊 **Ripple** | Expanding concentric rings from finger movement; interference glow between hands |

## How it works

- **MediaPipe Hand Landmarker** detects 21 3D landmarks per hand at video frame rate
- All rendering is pure Canvas 2D — no WebGL required
- Hand velocity is tracked per-landmark to drive speed-reactive effects
- Particles have physics: gravity, drag, and hand-push interaction (90px radius)
- Lightning bolts are cached for ~6 frames to prevent flickering
- GPU delegate attempted first, falls back to CPU automatically

## Stack

- [MediaPipe Tasks Vision](https://cdn.jsdelivr.net/npm/@mediapipe/tasks-vision) `0.10.14` (WASM)
- Vanilla JS ES Modules
- Canvas 2D API
- No build step
