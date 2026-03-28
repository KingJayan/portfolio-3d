# 3d portfolio template

### description
a single-file, immersive 3d portfolio experience. config-driven, minimalistic, dark-industrial aesthetic with a focus on spatial interaction and fluid camera movement.

### features
- **config-driven**: edit your bio, projects, and skills from a single json-like config block—no html/css hunting required.
- **6-dof spatial camera**: smooth interpolation, tracking, and zoom logic.
- **proximity rendering**: nodes dynamically render and intercept clicks based on camera distance to save memory.
- **performant**: built specifically for performance. avoids heavy filters on massive elements to prevent compositing crashes on mac/webkit.
- **dynamic styling**: deep obsidian theme with electric highlight accents.

### setup
1. clone or download the repository.
2. open `index.html` in your editor.
3. edit the `CONFIG` object at the very top of the `<script>` tag (lines 561-610)
4. open `index.html` in a modern browser. no build step required.

### structure
- `index.html` (the entire project):
  - `<style>`: contains custom properties (`:root`) for easy theme tweaking.
  - `<body>`: minimal markup. mostly rendering contexts like `#scene` and `#viewport`.
  - `<script>`: contains the `CONFIG` data, camera interpolation math, spatial focusing logic, and dynamic dom rendering.
  
### constraints
- **single-file**: no external assets (images, fonts, or libraries). google fonts are used, but can be removed.
- **vanilla-only**: zero dependencies. pure html, css-3d, and js.

### what its for
curating engineering projects, experimental prototypes, and architectural artifacts in a persistent spatial environment.

### needed
- modern browser with hardware acceleration.
- mouse/trackpad (recommended for 3d navigation).
