# Pixel Ring Calculator · 像素圆环计算器

An interactive, bilingual (Chinese/English) tool for visualizing pixel-perfect rings using the Midpoint Circle Algorithm, with 2D canvas rendering and 3D voxel extrusion via Three.js.

基于中点圆算法的交互式像素圆环可视化工具，支持 2D 画布渲染与 Three.js 3D 体素拉伸，中英双语。

---

## Features · 功能

- **Pixel-accurate circle rendering** — Uses the Midpoint Circle Algorithm to compute exact pixel boundaries for integer-radius circles
- **Adjustable ring thickness** — Visualize rings (annuli) of any thickness from 0 (boundary-only) to full fill
- **Dual center modes** — Single-pixel center or quad-pixel center for different aesthetic preferences
- **Real-time metrics** — Ring pixel count, inner pixel count, outer pixel count, and accuracy ratio vs. theoretical area (π(R² − r²))
- **3D voxel view** — Extrude the 2D pixel ring into a 3D voxel model with orbit controls (drag to rotate, scroll to zoom, right-drag to pan)
- **Solid / hollow inner** — Toggle whether the inner area renders as filled voxels in 3D
- **Adjustable extrude height** — Control the Z-axis depth of the 3D model (1–50)
- **Export to PNG** — Save the current 2D view with a choice of dark or light background
- **Grid overlay** — Toggle grid lines for precise pixel counting
- **Hover inspection** — Mouse over the canvas to see pixel coordinates, distance from center, and zone (ring/inner/outer/edge)
- **Bilingual UI** — Chinese (ZCOOL QingKe HuangYou) and English (Press Start 2P) with a one-click font toggle

## How It Works · 原理

The Midpoint Circle Algorithm (Bresenham circle) determines which integer grid cells lie on the circumference of a circle of radius `R`. By computing both an outer and inner boundary, the tool identifies three zones for every pixel in the grid:

| Zone | Color | Description |
|------|-------|-------------|
| **Inner** | Blue | Pixels inside the inner radius |
| **Ring** | Gold/Orange | Pixels on the ring (between inner and outer boundary) |
| **Outer** | Dark | Pixels outside the outer radius |

Outer edges are highlighted in orange, inner edges in yellow.

The 3D view extrudes each pixel column along the Z-axis as a unit cube (voxel), preserving the same zone coloring with checkerboard patterns for depth perception.

## Usage · 使用

Open `pixel-ring.html` in any modern browser. No build step, no dependencies to install — all libraries (Three.js, fonts) are loaded from CDN.

```
# Clone and open
git clone https://github.com/Fragile-373/pixel-ring.git
cd pixel-ring
# Open pixel-ring.html in your browser
```

Or simply visit the [GitHub Pages demo](https://fragile-373.github.io/pixel-ring/) if deployed.

### Controls · 操作

| Control | Action |
|---------|--------|
| Sliders / ± buttons | Adjust outer radius (1–100), thickness (0–20), extrude height (1–50) |
| 单格 / 四格 | Switch between single-pixel and quad-pixel center |
| 空心 / 实心 | Toggle hollow vs. solid inner rendering (3D) |
| 开启 3D 视图 | Toggle the 3D voxel view (expands to fill the main area) |
| 重置视角 | Reset 3D camera to default position |
| 网格线 | Toggle grid overlay |
| 导出PNG | Export the 2D canvas as a PNG image |
| 背景:深色/浅色 | Switch export background between dark and light |
| 中 / EN | Switch between Chinese and English UI |

## Tech Stack · 技术栈

- **Vanilla JS** — No framework, single self-contained HTML file
- **Canvas 2D** — Pixel-level rendering with the Midpoint Circle Algorithm
- **Three.js** (v0.160) — 3D voxel rendering with InstancedMesh for performance
- **OrbitControls** — Intuitive 3D camera manipulation
- **Google Fonts** — ZCOOL QingKe HuangYou (Chinese) + Press Start 2P (English)

## Browser Compatibility · 浏览器兼容

All modern browsers: Chrome, Firefox, Safari, Edge. Requires WebGL support for the 3D view.

## License · 许可

MIT
