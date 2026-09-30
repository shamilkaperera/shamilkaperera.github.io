---
title: 'Project Overview: CAD-Style Cover Page Designer'
date: 2026-10-01T00:26:00
thumbnail: /images/pasted-image-1790794649857.png
description: I built a purely client-side web application that generates millimeter-perfect A4 PDF cover pages. Instead of using standard fonts, I collaborated with AI to engineer a custom Simplex Vector Font Engine in JavaScript.
gallery: []
---

LINK = ([https://shamilkaperera.github.io/lab-report-cover-page/](https://shamilkaperera.github.io/lab-report-cover-page/))

**The Problem:** Standard web fonts contain invisible bounding boxes (ascenders and descenders) that make it impossible to guarantee exact physical print dimensions. When university engineering departments require lab report cover pages with strictly enforced millimeter heights (e.g., exactly 10mm for titles, 5mm for names) and exact line spacing, standard HTML-to-PDF converters fail. 

**The Solution:** I built a purely client-side web application that generates millimeter-perfect A4 PDF cover pages. Instead of using standard fonts, I collaborated with AI to engineer a custom **Simplex Vector Font Engine** in JavaScript.

![](/images/pasted-image-1790794690684.png)

HTML = ([https://drive.google.com/drive/u/2/folders/1EUfuoHvlp0j_ujMylYY-IQKILEzy2W78](https://drive.google.com/drive/u/2/folders/1EUfuoHvlp0j_ujMylYY-IQKILEzy2W78))

**Key Technical Features:**

- **Algorithmic Typography:** The application does not load any `.ttf` or `.otf` files. Every letter, number, and symbol is mathematically drawn using an ultra-dense array of X/Y vector coordinates mapped to a 10x8 grid.
- **Absolute Millimeter Precision:** By drawing paths directly via `jsPDF`, the engine bypasses font bounding boxes entirely. A requested 10mm font height yields exactly 10mm of physical black ink on the printed page.
- **Dynamic Layout Engine:** Features real-time calculation of physical string widths (accounting for custom 1mm letter spacing and dynamic spacebar gaps) to ensure perfect right-side anchoring and absolute center alignment.
- **Live Preview & Edge Rendering:** Features a reactive UI that updates a base64 PDF iframe in real-time as the user types, mimicking the exact aesthetic of a classic 0.2mm CAD drafting pen.
