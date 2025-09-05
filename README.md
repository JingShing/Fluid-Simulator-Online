English | [繁體中文](README_TCH.md)

# Fluid Gravity Simulator Web

## Online Preview

* [fluid Simulator | JingShing blog](https://jingshing.com/fluidsim/)
* [Github page](https://jingshing.github.io/Fluid-Simulator-Online/)

## How to Use

- Download `web-fluidsim.html` and open it directly.

## Controls

**PC**

- Mouse drag → the drag direction becomes the “gravity direction”
- Arrow keys `↑ ↓ ← →` → adjust gravity
- “Reset Particles” / “Zero Gravity” buttons → quick scene control

**Mobile**

- Tap “Enable Sensors” to grant permission (may not be required depending on platform)
- “Re-calibrate” to treat the current device posture as 0
- You can **invert X/Y** axes in settings

## Settings

- **Particle count / radius**: control quantity and size
- **Collision iterations / restitution**: more iterations → more solid; higher restitution → bouncier
- **Grid size**: grid render density (also affects the “blocky” fluid look)
- **Gravity multiplier / damping**: scene gravity strength and velocity decay
- **One-per-cell (experimental)**: prevent multiple particles from piling in the same cell (stricter, more expensive)
- **Particle color**: pick via color input; foam/rim colors are auto-derived
- **Render mode**: toggle between Grid / Particles
- **Language**: Traditional Chinese / English
- **Sidebar**: can be collapsed; use the top-left button to reopen

## Customize Defaults

**1) Change HTML input defaults:**

```html
<input id="nRange"    value="700" />
<input id="rRange"    value="4"   />
<input id="iterRange" value="3"   />
<input id="restRange" value="0.50"/>
<input id="gridRange" value="56"  />
<input id="gRange"    value="1.0" />
<input id="dRange"    value="0.995"/>
<input id="colorPicker" type="color" value="#0078ff"/>
<select id="langSel">…</select>
```

**2) Change JS fallbacks (initial values when there’s no `localStorage`):**

```js
let lang = localStorage.getItem('lang') || 'zh';
let baseColor = localStorage.getItem('baseColor') || '#0078ff';
// whether the sidebar is collapsed by default
const collapsedSaved = (localStorage.getItem('sidebarCollapsed') ?? '0') === '1';
// default render mode
let renderMode = 'grid'; // or 'balls'
```

> Note: if you’ve used the UI before, the browser may store your settings in `localStorage`. To make your new defaults take effect, clear them:

```js
['lang','baseColor','sidebarCollapsed','invX','invY'].forEach(k=>localStorage.removeItem(k));
```

## Roadmap

- Noisy distributions for particle radius/color
- WebGL acceleration
- Export/Load setting presets
- Auto-detect mobile device