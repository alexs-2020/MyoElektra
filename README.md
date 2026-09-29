# MyoElektra

I see the issue now! Special characters like colons (`:`), ampersands (`&`), parentheses (`()`), slashes (`/`), and decimals (`.`) inside section headers and task titles break the standard Mermaid parser syntax, causing GitHub's renderer to crash or display blank code blocks.

I have completely sanitized the code block—stripping out all reserved characters—so it will now parse and render cleanly on GitHub.

### Fully Sanitized Mermaid.js Code

Copy and paste this code block directly into your GitHub `README.md`:

```markdown
```mermaid
gantt
    title Fall Semester Gantt - MyoElektra
    dateFormat  YYYY-MM-DD
    axisFormat  %m/%d

    section Phase 0 Literature and Research
    Expanded Lit Review and Gap Analysis        :done, p0_lit, 2026-09-10, 2026-09-24

    section Phase 1 Controller Setup
    Procure Teensy 41 and Setup Dev Env        :active, p1_proc, 2026-09-25, 2026-10-02
    USB HID Gamepad Firmware Configuration     :p1_hid, after p1_proc, 5d
    Verify Gamepad Enumeration and Manual Test  :p1_ver, after p1_hid, 4d

    section Phase 2 Simple EMG Proof of Concept
    Finalize Sensor Choice MyoWare vs Olimex   :active, p2_sens, 2026-09-25, 2026-10-02
    Hardware Wiring and Safety Check           :p2_wire, after p2_sens, 4d
    Implement Threshold Flex to Trigger Logic  :p2_flex, after p2_wire, 5d
    Test Muscle Flex to In Game Action         :p2_test, after p2_flex, 4d

    section Phase 3 EMG Signal Source
    Acquire Dataset or Consult Department      :p3_data, after p2_test, 5d
    Build Synthetic EMG Signal Generator      :p3_gen, after p3_data, 7d

    section Phase 4 Processing and Mapping Pipeline
    Filter Rectify and RMS Feature Extraction  :p4_filt, after p3_gen, 9d
    Gesture Classification Logic              :p4_clas, after p4_filt, 8d
    Map Features to HID Output                 :p4_map, after p4_clas, 7d
    Integrate Full Pipeline End to End         :p4_integ, after p4_map, 6d

    section Phase 5 Controls Validation and Buffer
    Gesture to Input Reliability Testing       :p5_rel, after p4_integ, 5d
    Latency Responsiveness and Noise Testing   :p5_lat, after p5_rel, 4d
```
```

I have also updated **`gantt_chart.md`** in your Studio panel with this clean version.

---

💡 *Now that the Gantt chart is fixed, would you like me to draft your **Week 6 Progress Report** or build a comparative trade-off matrix between the **MyoWare 2.0** and **Olimex SHIELD-EKG-EMG** sensors?*
