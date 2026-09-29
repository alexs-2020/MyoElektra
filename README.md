# MyoElektra

I see the issue now! Special characters like colons (`:`), ampersands (`&`), parentheses (`()`), slashes (`/`), and decimals (`.`) inside section headers and task titles break the standard Mermaid parser syntax, causing GitHub's renderer to crash or display blank code blocks.

I have completely sanitized the code block—stripping out all reserved characters—so it will now parse and render cleanly on GitHub.

### Fully Sanitized Mermaid.js Code

Copy and paste this code block directly into your GitHub `README.md`:

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


mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#1b2838','primaryBorderColor':'#2f4b66','primaryTextColor':'#e2eaf3','fontFamily':'Inter, Segoe UI, Helvetica, sans-serif','fontSize':'13px','taskTextColor':'#0b1220','taskTextOutsideColor':'#e2eaf3','sectionBkgColor':'#22384f','altSectionBkgColor':'#18293c','sectionBorderColor':'#3d6288','gridColor':'#2c4258','todayLineColor':'#f5c518','doneTaskBkgColor':'#2f6f4f','doneTaskBorderColor':'#57c98a','activeTaskBkgColor':'#1d4ed8','activeTaskBorderColor':'#7fb2ff','critBkgColor':'#8b2635','critBorderColor':'#f87171','milestoneColor':'#f59e0b'}}}%%
gantt
    title MyoElektra · EMG-to-HID Controller — Fall 2026 Semester Plan
    dateFormat YYYY-MM-DD
    axisFormat %b %d

    section Foundations
    Proposal, goals, Teensy chosen          :done,    f1, 2026-08-24, 10d
    HID descriptor + protocol research     :done,    f2, 2026-09-01, 7d

    section Sensor Selection
    MyoWare 2.0 evaluation                :done,    s1, 2026-09-07, 5d
    Lit review deep dive (scope creep)     :crit, done, s2, 2026-09-14, 10d
    Dr Young · expired-electrode thread    :done,    s3, 2026-09-21, 5d
    Sensor comparison table + cert + Vout  :active,  s4, 2026-09-28, 3d
    SENSOR DECISION                        :milestone, crit, m2, 2026-09-30, 0d
    Place order (DigiKey)                  :crit,     o1, after m2, 1d
    Shipping lead time — buffer week       :         o2, after o1, 7d

    section Firmware
    Teensy 4.1 env + toolchain            :active,  w1, 2026-09-28, 5d
    Raw analog EMG read                     :crit,     w2, after o2, 5d
    Thresholds + hysteresis (3 gestures)   :crit,     w3, after w2, 4d
    HID joystick descriptor (buttons+axes) :         w4, after w2, 5d
    EMG to clean HID event pipeline        :crit,     w5, after w3, 5d
    First driverless game demo            :milestone, m3, after w5, 0d

    section Signal Quality
    Noise floor, 50/60Hz hum, drift        :         q1, after w2, 4d
    Electrode placement + skin prep        :         q2, after q1, 5d
    Expand 3 to 8 gestures                :         q3, after q2, 5d
    Harness / sleeve / socket integration  :         q4, after q3, 7d
    Latency + reliability measured         :milestone, m4, after q4, 0d

    section Validation
    Fitts' law benchmark                  :crit,     v1, after m3, 5d
    Recruit users (start NOW)              :crit,     r1, 2026-10-26, 21d
    Pilot sessions w/ amputee users        :crit,     v2, after r1, 10d
    Open-source repo + docs ship           :         v3, after v2, 4d
    Final report + slides                  :crit,     v4, after v2, 7d
    FINAL PRESENTATION (verify date)       :milestone, crit, m5, after v4, 0d

    section Weekly Cadence
    Mentor sync + report                   :active,    c1, 2026-09-28, 1d
    Mentor sync                            :         c2, 2026-10-05, 1d
    Mentor sync                            :         c3, 2026-10-12, 1d
    Mentor sync                            :         c4, 2026-10-19, 1d
    Mentor sync                            :         c5, 2026-10-26, 1d
    Mentor sync                            :         c6, 2026-11-02, 1d
    Mentor sync                            :         c7, 2026-11-09, 1d
    Mentor sync                            :         c8, 2026-11-16, 1d
    Thanksgiving break                     :         c9, 2026-11-23, 5d
    Mentor sync · dry-run demo             :crit,     c10, 2026-11-30, 1d
