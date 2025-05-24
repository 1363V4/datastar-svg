# 🤯 Datastar SVG Morphing Demo

A HTML-only demonstration showcasing SVG path morphing animations using **Datastar** reactive features and the **anime.iife** animation library.

## ✨ Live Demo Features

- **SVG Path Morphing**: Watch geometric shapes smoothly transition between "kiki" and "booba" forms
- **Real-time Controls**: Interactive sliders, checkboxes, and dropdowns that instantly update the SVG
- **Dynamic Text Animation**: Text morphs along paths with time-based content switching
- **Rainbow Animations**: CSS animations triggered by Datastar state
- **Responsive Viewport**: Dynamic SVG viewBox that responds to zoom controls

## 🎯 Datastar Features Highlighted

### 1. **Data Binding (`data-bind-*`)**

```html
<input type="checkbox" data-bind-labels />
<input type="number" data-bind-width value="8" min="1" max="20" />
<input type="checkbox" data-bind-rainbow />
<select data-bind-fill>
  <select data-bind-outline>
    <input type="range" data-bind-zoom min="-200" max="0" />
    <input type="range" data-bind-time min="0" max="5000" />
  </select>
</select>
```

- Two-way data binding between form controls and SVG properties
- Reactive updates without manual event listeners
- Automatic state synchronization across the entire UI

### 2. **Computed Properties (`data-computed-*`)**

```html
<svg
  data-computed-vb.width="600 - $zoom"
  data-computed-vb.heigth="250 - $zoom"
  data-attr="{'viewBox': [0, 0, $vb.width, $vb.heigth].join(' ')}"
></svg>
```

- Reactive calculations that automatically update when dependencies change
- Creates derived state for SVG transformations
- Enables dynamic viewport sizing based on zoom level

### 3. **Conditional Rendering (`data-show`)**

```html
<textPath
  data-show="$labels"
  data-text="($time < 1000 && 'kiki') || ($time < 3000 && 'booki') || 'booba'"
  href="#path1"
>
</textPath>
```

- Conditionally displays text labels based on checkbox state
- Clean declarative approach to showing/hiding elements

### 4. **Dynamic Text Content (`data-text`)**

```html
data-text="($time < 1000 && 'kiki') || ($time < 3000 && 'booki') || 'booba'"
```

- Time-based text transitions using JavaScript expressions
- Reactive text that changes based on animation timeline position

### 5. **Attribute Binding (`data-attr-*`)**

```html
<svg data-attr="{'viewBox': [0, 0, $vb.width, $vb.heigth].join(' ')}">
  <g data-attr-stroke-width="$width" data-attr-rainbow="$rainbow">
    <use data-attr-fill="'url(' + $fill + ')'">
      <use data-attr-stroke-dasharray="$outline"></use>
    </use>
  </g>
</svg>
```

- Dynamic SVG attributes that respond to form control changes
- Seamless integration between HTML form state and SVG presentation
- Conditional attribute application for rainbow effects

### 6. **Event Handling (`data-on-*`)**

```html
<button
  data-on-click="animate(svg1, { scale: 1.02, filter: 'drop-shadow(2px 0px 2px black)', loop: true, alternate: true });"
>
  <input data-on-raf="animation.seek($time)" />
</button>
```

- Event-driven anime.js integration
- Seamless bridge between Datastar state and animation libraries
- Real-time animation seeking using requestAnimationFrame

> `data-on-raf` is a special event that is triggered on every requestAnimationFrame event. This is useful for updating the UI at maximum at the rendering refresh rate of the browser. In this example we update the currentTime signals with a new Date object. This triggers a re-render of the currentTime span element. You can still use the **throttle and **debounce modifiers to control the rate of updates even further.

### 7. **Signals (`data-signals-*`)**

```html
<input type="range" data-signals-time="0" data-bind-time />
```

- Manual signal initialization for animation timeline control
- Provides precise control over animation state

## 🛠 Technical Architecture

### Dependencies

- **Datastar**: Reactive Hypermedia framework
- **anime.js**: High-performance SVG morphing animations
- **Open Props**: CSS normalization

### Key Components

1. **Interactive Controls Panel**

   - Stroke width adjustment
   - Fill pattern selection (French/Spanish flag gradients)
   - Outline style options (solid/dashed/dotted)
   - Rainbow animation toggle
   - Zoom and timeline controls

2. **Dynamic SVG Viewport**

   - Responsive viewBox calculations
   - Preserves aspect ratio with slice scaling
   - Interactive hover effects with CSS filters

3. **Path Morphing System**
   - Two predefined SVG paths representing different shapes
   - Smooth anime.js morphing between geometric forms
   - 5-second animation timeline with manual scrubbing

## 🎨 Animation Details

The demo features a morphing animation between two SVG paths:

- **Path 1**: Angular, spiky "kiki" shape with sharp transitions
- **Path 2**: Rounded, flowing "booba" shape with smooth curves

The morphing animation demonstrates the **bouba/kiki effect** - a psychological phenomenon where people associate certain sounds with specific visual shapes.

## 🚀 Running the Demo

Simply open `index.html` in a modern web browser. No build process or server required!

```bash
# Clone and open
git clone [repository-url]
cd datastar-svg
open index.html
```

## 💡 Educational Value

This demo showcases how **Datastar** eliminates the complexity typically associated with:

- Manual DOM manipulation
- Event listener management
- State synchronization between UI controls and visual elements
- Complex reactive calculations

The result is clean, declarative HTML that's easy to understand and maintain, while still enabling sophisticated interactive animations.
