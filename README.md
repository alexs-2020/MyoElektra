# MyoElektra


```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#1b2838','primaryBorderColor':'#2f4b66','primaryTextColor':'#e2eaf3','fontFamily':'Inter, Segoe UI, Helvetica, sans-serif','fontSize':'13px','taskTextColor':'#0b1220','taskTextOutsideColor':'#e2eaf3','sectionBkgColor':'#22384f','altSectionBkgColor':'#18293c','gridColor':'#4b7ba6','todayLineColor':'#f5c518'}}}%%
gantt
    title MyoElektra · EMG-to-HID Controller — Fall 2026
    dateFormat  YYYY-MM-DD
    axisFormat  %b %d
    tickInterval 1week
    weekday     monday
    topAxis     true
    excludes    weekends
    todayMarker stroke-width:3px,stroke:#f5c518,opacity:0.9

    section Key dates
    Sensor decision  :vert, vm1, 2026-09-30, 1d
    Order cutoff     :vert, vm2, 2026-10-02, 1d
    Demo gate        :vert, vm3, 2026-11-09, 1d
    Final present    :vert, vm4, 2026-12-11, 1d

    section Foundations
    Proposal, goals, Teensy chosen     :done, f1, 2026-08-24, 10d
    HID descriptor + protocol research:done, f2, 2026-09-01, 7d

    section Sensor Selection
    MyoWare 2.0 evaluation           :done, s1, 2026-09-07, 5d
    Lit review deep dive              :done, crit, s2, 2026-09-14, 10d
    Dr Young - electrode lifespan    :done, s3, 2026-09-21, 5d
    Comparison table + cert + Vout   :active, crit, s4, 2026-09-28, 3d
    SENSOR DECISION                   :milestone, crit, m2, 2026-09-30, 0d
    Place order (DigiKey)             :crit, o1, after m2, 1d
    Shipping lead - buffer week       :o2, 2026-10-05, 7d

    section Firmware
    Teensy 4.1 env + toolchain       :active, w1, 2026-09-28, 5d
    Raw analog EMG read              :crit, w2, after o2, 5d
    Thresholds + hysteresis (3 gest) :crit, w3, after w2, 4d
    HID joystick descriptor          :w4, after w2, 5d
    EMG - HID event pipeline         :crit, w5, after w3, 5d
    First driverless game demo        :milestone, m3, after w5, 0d

    section Signal Quality
    Noise floor, hum, drift          :q1, after w2, 4d
    Electrode placement + skin prep  :q2, after q1, 5d
    Expand 3 to 8 gestures           :q3, after q2, 5d
    Harness / sleeve integration     :q4, after q3, 7d
    Latency measured                 :milestone, m4, after q4, 0d

    section Validation
    Fitts law benchmark              :crit, v1, after m3, 5d
    Recruit users (start now)        :crit, r1, 2026-10-26, 21d
    Pilot sessions w/ amputee users  :crit, v2, after r1, 10d
    Open-source repo + docs          :v3, after v2, 4d
    Final report + slides            :crit, v4, after v2, 7d
    FINAL PRESENTATION              :milestone, crit, m5, after v4, 0d

    %% Thanksgiving break - shift to real academic dates
    excludes 2026-11-26 2026-11-27 2026-11-28
```
