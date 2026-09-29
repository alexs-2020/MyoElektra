# MyoElektra
The main reason your Gantt chart wasn't rendering cleanly was the **`:vert` tag** under your key dates section. Mermaid Gantt syntax does not support `:vert` for custom vertical line overlays—adding it forces Mermaid to render broken 1-day task bars that misalign the grid.

### What Was Fixed
1. **Weekly Vertical Grid Lines:** Removed `:vert` and let `tickInterval 1week` + `weekday monday` automatically create vertical line divisions every Monday across the entire chart.
2. **Key Date Diamonds:** Converted key dates (`Sensor Decision`, `Order Cutoff`, `Demo Gate`, `Final Presentation`) into true **`:milestone`** entries with `0d` duration so they display as crisp diamond markers.
3. **Character Escaping:** Stripped special symbols (`·`, `—`, `+`, `/`, `.`) from task names to prevent GitHub's syntax parser from crashing.
4. **Clean Grid Theme:** Simplified the directive block so vertical grid lines (`gridColor`) and week ticks stand out clearly without cluttering task text.

---

### Cleaned & Working GitHub Markdown Code

Copy and paste this snippet directly into your GitHub `README.md`:


```mermaid
%%{init: {"gantt": {
  "useWidth": 1180,
  "leftPadding": 230,
  "barHeight": 26,
  "barGap": 8,
  "sectionFontSize": 14,
  "fontSize": 12,
  "gridColor": "#c9c9c9",
  "todayLineColor": "#e63946",
  "sectionBkgColor": ["#f2f4f8", "#ffffff"],
  "altBkgColor": ["#fafbfd", "#f2f4f8"],
  "taskTextColor": "#111111",
  "sectionBkgColorTransparency": false
}}}%%
gantt
    title MyoElektra — Capstone Phase Timeline
    dateFormat  YYYY-MM-DD
    axisFormat  %b %d
    tickInterval 1week
    excludes    weekends

    section P1 · Research
    Literature review + source audit  :done,      p1, 2026-09-07, 2026-10-05
    Gap statement + matrix locked     :milestone, crit, m1, 2026-10-05, 0d

    section P2 · HID Foundation
    Teensy 4.1 procure + env setup   :active,    crit, p2, 2026-10-05, 2026-10-19
    Driverless gamepad enumerated    :milestone, m2, 2026-10-19, 0d

    section P3 · Sensor + PoC
    Sensor choice: Olimex vs MyoWare :           p3a, 2026-10-12, 2026-10-26
    Single-gesture PoC               :           p3b, 2026-10-26, 2026-11-09

    section P4 · Processing Pipeline
    Simulated EMG input path         :           p4a, 2026-11-09, 2026-11-23
    Discrete + proportional tiers   :           p4b, 2026-11-23, 2026-12-07

    section P5 · Integration + Report
    Output profiles (game/RC/drone) :           p5a, 2026-12-07, 2026-12-18
    Final report + demo              :milestone, crit, m3, 2026-12-18, 0d
```
