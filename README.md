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
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#1b2838', 'primaryBorderColor': '#2f4b66', 'primaryTextColor': '#ffffff', 'sectionBkgColor': '#1d2f42', 'altSectionBkgColor': '#152332', 'gridColor': '#3a5878', 'todayLineColor': '#f5c518'}}}%%
gantt
    title MyoElektra - EMG to HID Controller - Fall 2026
    dateFormat  YYYY-MM-DD
    axisFormat  %b %d
    tickInterval 1week
    weekday monday
    excludes weekends, 2026-11-26, 2026-11-27, 2026-11-28

    section Key Milestones
    Sensor Decision Deadline           :milestone, vm1, 2026-09-30, 0d
    Hardware Order Cutoff              :milestone, vm2, 2026-10-02, 0d
    First Driverless Demo Gate         :milestone, vm3, 2026-11-09, 0d
    Final Project Presentation         :milestone, vm4, 2026-12-11, 0d

    section Foundations
    Proposal goals and Teensy selection :done, f1, 2026-08-24, 10d
    HID descriptor and protocol study   :done, f2, 2026-09-01, 7d

    section Sensor Selection
    MyoWare 20 evaluation               :done, s1, 2026-09-07, 5d
    Literature review deep dive         :done, crit, s2, 2026-09-14, 10d
    Electrode lifespan research         :done, s3, 2026-09-21, 5d
    Comparison table and Vout check     :active, crit, s4, 2026-09-28, 3d
    SENSOR DECISION                     :milestone, crit, m2, 2026-09-30, 0d
    Place hardware order DigiKey        :crit, o1, after m2, 1d
    Shipping lead and buffer week       :o2, 2026-10-05, 7d

    section Firmware Development
    Teensy 41 setup and toolchain       :active, w1, 2026-09-28, 5d
    Raw analog EMG signal reading       :crit, w2, after o2, 5d
    Thresholds and hysteresis 3 gest    :crit, w3, after w2, 4d
    HID joystick descriptor config      :w4, after w2, 5d
    EMG to HID event pipeline           :crit, w5, after w3, 5d
    First driverless game demo          :milestone, m3, after w5, 0d

    section Signal Quality
    Noise floor hum and drift analysis  :q1, after w2, 4d
    Electrode placement and skin prep   :q2, after q1, 5d
    Expand gesture set 3 to 8           :q3, after q2, 5d
    Harness and sleeve integration      :q4, after q3, 7d
    Latency benchmarking complete       :milestone, m4, after q4, 0d

    section Validation
    Fitts law benchmark testing         :crit, v1, after m3, 5d
    Recruit amputee and user testing    :crit, r1, 2026-10-26, 21d
    Pilot testing sessions              :crit, v2, after r1, 10d
    Open source repo and docs           :v3, after v2, 4d
    Final report and slide deck         :crit, v4, after v2, 7d
    FINAL PRESENTATION                  :milestone, crit, m5, after v4, 0d
```
