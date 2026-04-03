---
title: 'Biometric HCI: Real-Time Ocular-Controlled Interface'
date: 2026-04-03T17:28:00
thumbnail: /images/Screenshot 2026-04-03 172355.png
description: This project demonstrates a fully functional Eye-Tracking OS Interface designed to replace traditional HID peripherals with real-time biometric inputs. Built primarily with Python, OpenCV, and MediaPipe, the system interprets a 478-point facial mesh to drive system-level cursor navigation and click events via PyAutoGUI.
gallery:
  - /images/Screenshot 2026-04-03 172406.png
  - /images/Screenshot 2026-04-03 172631.png
---

files=https://drive.google.com/file/d/1WNtqPwRA7aqaHkOS4ssfWj0Y9iL9M0R6/view?usp=sharing

video = https://youtu.be/fW4aA76ArdA?si=5a8gxq3XBpr-HYjj

### **Ocular Tracking & Cursor Kinematics**

The core navigation engine isolates the **Iris landmark indices** and maps their center point relative to a dynamically calibrated "Face Box." Because human eyes constantly make tiny, involuntary movements (micro-saccades), raw coordinate mapping results in severe cursor jitter. To solve this, I engineered an **Exponential Moving Average (EMA) filter** ($\alpha = 0.85$), which aggressively smooths the signal telemetry, yielding a fluid, sub-pixel accurate cursor.

### **Biometric State Machine**

Rather than relying on dwell-time for clicks, the system uses a highly responsive biometric state machine:

- **Asynchronous Clicking:** Utilizes the **Eye Aspect Ratio (EAR)** algorithm. Independent threshold checks determine intentional left or right eye closures (under 0.5 seconds) to fire discrete mouse clicks.
- **Drag-and-Drop Logic:** Sustained closure of the right eye triggers a `mouseDown` state, allowing users to drag windows or files until the eye reopens.
- **Z-Axis Input (Eyebrow Deviation):** To add a dimension of input without compromising eye-tracking, the system measures the vertical pixel deviation between the eyebrows and a fixed anchor (the nose tip). A sustained elevation triggers a double-click event.

### **Safety & Calibration Architecture**

To ensure real-world usability, the architecture includes independent cooldown timers to prevent input flooding. It also features a zero-state calibration sequence that triggers when both eyes are closed from an idle state, dynamically resetting the baseline facial geometry and EMA buffers. A hardware-toggle failsafe allows instant switching between ocular and physical mouse control.
