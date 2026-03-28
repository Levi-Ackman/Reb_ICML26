## Pseudocode: Deterministic Visualization Operator in ViRe

**Input**
- Medical time series sample `X ∈ R^{T×C}`
- Sampling rate `fs`
- Per-panel height `H_panel`
- Panel width `W_panel`
- Render DPI `dpi`
- Line width in pixels `line_px`

**Output**
- Square RGB waveform image `I_square`

---

### Algorithm

1. Construct a shared time axis:
   - `t ← [0, 1, ..., T−1] / fs`

2. Assign one fixed color to each channel:
   - `colors ← colormap("tab20", C)`

3. Initialize an empty panel list:
   - `Panels ← []`

4. For each channel `c = 1, 2, ..., C`:
   1. Create a blank figure with size:
      - width = `W_panel / dpi`
      - height = `H_panel / dpi`
   2. Plot the waveform:
      - draw `X[:, c]` against `t`
      - use color `colors[c]`
      - use line width converted from pixel to point:
        - `lw_pt = max(0.5, line_px) * 72 / dpi`
   3. Fix the x-axis range:
      - `xlim ← [t[0], t[T−1]]`
   4. Remove all axis elements:
      - hide x-ticks
      - hide y-ticks
      - hide top/right/left/bottom spines
   5. Export the figure as an RGB PNG panel
   6. Append the panel to `Panels`

5. Unify panel width:
   - `target_w ← max(width(panel) for panel in Panels)`
   - For each panel in `Panels`:
     - if `width(panel) < target_w`:
       - right-pad with white pixels until width = `target_w`

6. Vertically stack all padded panels:
   - `total_h ← sum(height(panel) for panel in Panels)`
   - create white canvas `I_stack` of size `(target_w, total_h)`
   - paste panels one by one from top to bottom

7. Pad the stacked image to a square canvas:
   - `side ← max(width(I_stack), height(I_stack))`
   - create white square canvas `I_square` of size `(side, side)`
   - center `I_stack` onto `I_square`

8. Return `I_square`

---

### Optional downstream step in ViRe

9. Apply CLIP image preprocessing:
   - `x_img ← CLIP_preprocess(I_square)`

10. Feed into the frozen CLIP vision encoder:
   - `Z ← f_CLIP(x_img)`

11. Use `Z` as the vision feature / Vision Query source.
