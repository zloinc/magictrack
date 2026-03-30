# ✨ Magic Hands

Real-time hand tracking with magical visual effects, built with [MediaPipe Hands](https://chuoling.github.io/mediapipe/solutions/hands.html) and plain Canvas 2D — no frameworks, no build step, single HTML file.

## Demo

Open `index.html` via any local HTTP server (e.g. `python3 -m http.server 8080`) and allow camera access.

> **Note:** Must be served over HTTP/HTTPS (not `file://`) for camera access and WASM to work.

## Effects

| Mode | Description |
|------|-------------|
| 🕸 **Web** | Glowing lines between all fingertips + hand skeleton |
| 🌀 **Warp** | Color-mixed slime bridges between nearby raised fingers |
| ⚡ **Lightning** | Fractal electric bolts between fingers — within hand and across both hands |
| ✨ **Particles** | Sparks that react to hand speed, inherit velocity, and scatter when your hand pushes through them |
| 🛡 **Aura** | Open-palm energy shield with concentric halos and finger beams |
| 🦴 **Rigging** | Every hand landmark connected to every other — 210 lines per hand |
| 🎆 **Fireworks** | Slow = light trail; sudden fast flick = particle explosion burst |
| 💥 **Nova** | Two-finger gesture spawns bright radial bursts and particle detonations from the gesture center |
| 🌀 **Portal** | Close palms form a glowing portal with arcs linking active fingers across hands |
| 🔮 **Orbs** | Smooth-lagging orbs with orbiting ring particles; opposite hand orbs connect with beams |

## How it works

- **MediaPipe Hands** detects 21 3D landmarks per hand at video frame rate
- All rendering is pure Canvas 2D — no WebGL required
- Hand velocity is tracked per-landmark to drive speed-reactive effects
- Particles have physics: gravity, drag, and hand-push interaction (90px radius)
- Lightning bolts are cached for ~6 frames to prevent flickering
- MediaPipe downloads its model/WASM assets on first launch, then starts continuous tracking from the camera

## Stack

- [@mediapipe/hands](https://cdn.jsdelivr.net/npm/@mediapipe/hands) `0.4.1675469240`
- Vanilla JS
- Canvas 2D API
- No build step
