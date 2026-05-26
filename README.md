# AudioMass (Enhanced Edition)
Free full-featured web-based audio & waveform editing tool.

Live: https://audiomass.netlify.app/

### Now with Ableton Live 12 Theme!

This fork enhances the original AudioMass codebase with a premium Ableton Live 12 theme, customizable visualization tools, and Zero Crossing Rate (ZCR) frequency colorized waveforms, built natively on top of the original zero-dependency architecture.

![AudioMass Multitrack<img width="1728" height="1082" alt="image" src="https://github.com/user-attachments/assets/099c6595-7f75-4ca6-9906-bbff3ff771e9" />


---

## Key Additions in this Fork

### 🎛️ Ableton Live 12 theme
* **Ableton Live 12 Theme**: Instantly switch to a professional dark production environment via the **View** menu.
* **Dynamic Track Colors**: Channel headers, inputs, and canvas clips dynamically style in vibrant, Ableton-matching color accents based on track order.
* **DAW-inspired Controls**: Flat custom scrollbars, clean button states, and color-coded statuses (amber for Mute, cyan for Solo, red for Arm/Record).

### Zero Crossing Rate (ZCR) Rainbow Waveforms
* **Frequency Mapping**: Visualizes frequency density directly on the audio clip. Low frequencies render in warm orange/reds, and high frequencies render in cool blues.
* **Toggleable & Persistent**: Easily toggle Rainbow Waveforms from the **View** menu. The setting is stored in `localStorage` and automatically loaded on startup.
* **High Performance**: Employs an `O(1)` zero crossing rate algorithm capped at 120 samples per horizontal pixel column, ensuring fluid rendering performance (< 1.5ms per draw loop) during zooms and pans.

### Modernized Visualizer Engines
* **Spectrogram (`sp.html`)**: Now features dynamic Ableton Live theme color interpolation, smooth contrast gradients, and a fixed division-by-zero color scaling bug.
* **Frequency Analyser (`eq.html`)**: Rewritten to detect the master window's theme class. Renders in a modern, Minimeters-inspired look with a 1px visual gap spacing between frequency bands.

### 📱 Layout Overlap Correction
* Modified the top control toolbar (`.pk_tb`) to use a responsive flexbox layout. Floating panels and absolute duration indicators now flow dynamically without overlapping when the viewport is narrow.

---

## Setup & Local Running

1. Checkout this repository (or download it as a zip).
2. Navigate to it in your terminal, then access the `src` directory.
3. Run `go run audiomass-server.go` or, if you do not have Go installed, start the simple python webserver by running `python3 audiomass-server.py`.
4. Open your browser and navigate to **[http://localhost:5055/](http://localhost:5055/)**.

---

## Production Build Pipeline

If you want to package/minify the scripts into `all.build.js` for production publishing, you can run:

```bash
cat dist/wavesurfer.js dist/plugin/wavesurfer.regions.js oneup.js app.js keys.js contextmenu.js lufs.js ui-fx.js ui.js modal.js state.js engine.js actions.js drag.js recorder.js multitrack.js welcome.js fx-pg-eq.js fx-auto.js local.js id3.js lzma.js | uglifyjs -c -m -o all.build.js
