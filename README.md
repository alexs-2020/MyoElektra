# MyoElektra
The reason it doesn't render graphically inside the **Studio panel** on the right is that the Studio panel is a standard text/markdown viewer—it displays the raw code rather than running a live Mermaid.js graphics engine.

However, **GitHub DOES render it natively!** Here is how to get it rendering on GitHub:

### How to render it on GitHub:
1. Open any `.md` file in your GitHub repository (e.g., `README.md`) and click **Edit** (the pencil icon).
2. Paste the snippet below **exactly as shown** (making sure the triple backticks ` ```mermaid ` are on their own line):

```markdown
```mermaid
gantt
    title Fall Semester Gantt — MyoElektra (Sim & Controls)
    dateFormat  YYYY-MM-DD
    axisFormat  %m/%d

    section Phase 0: Literature & Research
    Expanded Lit Review & Gap Analysis           :done,    p0_lit, 2026-09-10, 2026-09-24

    section Phase 1: Controller Setup (Teensy HID)
    Procure Teensy 4.1 & Setup Dev Env           :active,  p1_proc, 2026-09-25, 2026-10-02
    USB HID Gamepad Firmware Configuration        :         p1_hid,  after p1_proc, 5d
    Verify Gamepad Enumeration & Manual Test     :         p1_ver,  after p1_hid, 4d

    section Phase 2: Simple EMG Proof of Concept
    Finalize Sensor Choice (MyoWare vs Olimex)   :active,  p2_sens, 2026-09-25, 2026-10-02
    Hardware Wiring & 3.3V Pin Safety Check      :         p2_wire, after p2_sens, 4d
    Implement Threshold Flex-to-Trigger Logic    :         p2_flex, after p2_wire, 5d
    Test Muscle Flex to In-Game Action           :         p2_test, after p2_flex, 4d

    section Phase 3: EMG Signal Source
    Acquire Dataset / Consult Dept (Prof. Momona):         p3_data, after p2_test, 5d
    Build Synthetic EMG Signal Generator         :         p3_gen,  after p3_data, 7d

    section Phase 4: Processing & Mapping Pipeline
    Filter, Rectify & RMS Feature Extraction     :         p4_filt, after p3_gen, 9d
    Gesture Classification Logic                 :         p4_clas, after p4_filt, 8d
    Map Features to HID Output (Sticks/Triggers) :         p4_map,  after p4_clas, 7d
    Integrate Full Pipeline End-to-End           :         p4_integ,after p4_map, 6d

    section Phase 5: Controls Validation & Buffer
    Gesture-to-Input Reliability Testing         :         p5_rel,  after p4_integ, 5d
    Latency, Responsiveness & Noise Testing       :         p5_lat,  after p5_rel, 4d
```
```

3. Click the **Preview** tab at the top of the GitHub editor. GitHub will immediately compile and render the interactive Gantt chart diagram.

---

If you'd rather see the visual graphic directly here in Gemini Notebook without copying to GitHub, you can click on **`fall_semester_gantt_chart.png`** in your Studio panel!

---

💡 *Would you like me to move on to drafting your **Week 6 Progress Report** or building the **MyoWare 2.0 vs. Olimex SHIELD comparison table**?*
