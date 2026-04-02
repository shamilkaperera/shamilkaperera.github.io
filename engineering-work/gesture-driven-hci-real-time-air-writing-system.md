---
title: 'Gesture-Driven HCI: Real-Time Air-Writing System'
date: 2026-04-03T01:06:00
thumbnail: /images/Screenshot 2026-04-03 010336.png
description: I developed a high-precision Air-Writing application using Python, OpenCV, and MediaPipe. The project focuses on seamless Human-Computer Interaction (HCI) by mapping complex hand landmarks to a digital canvas.
gallery:
  - /images/Screenshot 2026-04-03 010401.png
  - /images/Screenshot 2026-04-03 010645.png
---

This project explores the intersection of **Computer Vision** and intuitive **Human-Computer Interaction (HCI)**. Developed using **Python**, **OpenCV**, and **MediaPipe**, the system transforms a standard webcam into a high-precision digital canvas, allowing users to write and interact with a UI in 3D space without physical contact.

### **Technical Architecture**

The core of the application relies on a **21-point hand-landmarking model** that maps physical coordinates to a 1080p digital overlay. To resolve the inherent "jitter" found in raw hand-tracking data, I implemented an **Exponential Moving Average (EMA)** smoothing filter. This ensures that the digital ink remains fluid and precise, even when tracking subtle hand tremors.

### **Gesture State Machine & UI Design**

The system is built on a robust **State Machine** that dynamically switches between operation modes based on real-time finger geometry:

- **Drawing Mode:** Triggered by specific finger configurations (V-sign or Index Up).
- **Eraser Logic:** A "Spiderman" gesture activates a localized pixel-clearing function on the **NumPy-based ink canvas**.
- **UI Interaction:** A vertical **HSV-mapped color bar** and a thickness slider allow for seamless parameter adjustments.
- **Modal Control:** The system intelligently freezes drawing functions when the user interacts with UI elements, preventing accidental input and ensuring a "clean" creative workflow.

### **Optimization & Performance**

By utilizing **NumPy** for mask operations and **cv2.addWeighted** for frame blending, the system maintains a high frame rate while managing a persistent drawing layer. The result is a low-latency, professional-grade interface that demonstrates how sophisticated signal processing can turn simple video data into a powerful creative tool.
