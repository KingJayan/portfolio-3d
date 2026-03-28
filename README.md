# 3d portfolio template

### description
a single-file, immersive 3d portfolio experience. config-driven, minimalistic, glassmorphism aesthetic with a focus on spatial interaction.

![midnight theme, particles background on about section](screenshots/midn-particles-about.png)

### features
- **config-driven**: edit your bio, projects, and skills from a single json-like config block—no html/css hunting required.
- **6-dof spatial camera**: smooth tracking and zoom logic.
- **proximity rendering**: nodes dynamically render and intercept clicks based on camera distance to save memory.
- **performant**: built specifically for performance. avoids heavy filters on massive elements to prevent compositing crashes on mac/webkit.
- **dynamic styling**: configurable themes to fit your style.

### requirements
- modern browser with hardware acceleration.
- mouse/trackpad (recommended for 3d navigation).

### setup
1. clone or download the repository.
2. open `index.html` in your editor.
3. edit the `CONFIG` object at the very top of the `<script>` tag (starts @ line 614)
4. open `index.html` in a modern browser. no build step required.

**what's in `CONFIG`:**

| key | what it does |
|---|---|
| `name`, `title` | your name and page title |
| `theme` | color/glass preset (`forge`, `midnight`, `arctic`, `terminal`, `ember`) |
| `bg` | background effect (`none`, `particles`, `scanlines`, `nebula`) |
| `camera` | scroll speed, drag speed, easing, and focus distance |
| `bootSequence` | lines shown on the loading screen |
| `homeNav` | the text for the "return to center" nav button |
| `sections` | an array of objects defining your 3d nodes (see below) |

### adding new sections
the portfolio is entirely dynamic. to add a new section, simply add a new object to the `CONFIG.sections` array. the engine will automatically generate the 3d node, wire up the camera focus logic, and add a button to the nav bar.

```javascript
{
    id: "gallery",
    nav: "My Art",             // nav bar label
    pos: [1000, 1000, 0],      // [x, y, z] coordinates in 3d space
    rot: [0, -45],             // [x, y] tilt rotation
    panel: true,               // applies the glassmorphism panel styling
    contentHTML: `
        <h2>gallery</h2>
        <p>this is a new section</p>
    `
}
```

### file structure
everything lives in `index.html`. the file is split into three sections:

- **`<style>`**: theme tokens (`:root` css variables), component styles, animations
- **`<body>`**: minimal html shell. contains `#viewport` → `#scene` (the 3d world), fixed ui overlays (nav, load screen), and background effect layers
- **`<script>`**: split into two parts:
  + **`THEMES` / `CONFIG`** (top, editable): all user-facing content and settings. change this to customize your portfolio
  + **render + engine** (bottom, do not edit): parses `CONFIG`, renders html from it, drives the camera, background effects, and proximity detection loop

### constraints
- **single-file**: no external assets. google fonts are used, but can be removed, and images are for docs only.
- **vanilla-only**: zero dependencies. pure html, css transforms, and js.

### limitations
- **browser compatibility**: utilizes 3d css transforms and `backdrop-filter`. older browsers or those without hardware acceleration enabled will experience significant lag or visual artifacts.
- **performance context**: while optimized, rendering many 3d elements via css has limits. keep component counts reasonable to maintain a fluid 60fps experience.
- **safari/webkit**: to prevent known webkit compositing bugs, `backdrop-filter` is applied only to fixed overlays, not to 3d-transformed scene nodes.
- **mobile UX**: currently optimized for mouse and trackpad interaction (6-dof panning and dolly zoom). mobile touch support is present but less precise.
- **no dynamic backend**: as a static, single-file template, it does not include a backend. contact forms and social links must be hooked into external services.

### what its for
curating engineering projects, prototypes, and artifacts in a persistent spatial environment.
