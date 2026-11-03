# 🚀 Array-Lab

> **Modern Interactive Array Algorithm Workbench, Visualizer & Stepper IDE with Real DevTools REPL and Time-Travel Debugging.**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-brightgreen?logo=github)](https://favouritesir.github.io/Array-Lab/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-0-orange.svg)](#features)
[![Bangla Documentation](https://img.shields.io/badge/Docs-বাংলা%20(Bengali)-ff69b4)](languages/bn/README.md)

---

## 🌟 Overview

**Array-Lab** is an ultra-fast, zero-dependency, single-file interactive workbench for designing, learning, visualizing, and researching array algorithms and data structures. It features physical 3D arcing element glides, multi-pointer tracking, live breakpoints, forward and reverse time-travel stepping, interactive draggable sticky notes, an embedded in-stream Chrome-style DevTools JavaScript REPL, and a human thinking session recorder.

Whether you are mastering Bubble Sort, Quick Sort, Binary Search, Two Pointers, Sliding Window, or pioneering innovative sorting algorithms like Cloud Merge Sort, **Array-Lab** gives you a transparent, physical glass box into every single memory change.

---

## ✨ Key Features & Capabilities

### 1. 🤹 Interactive Dual-Layer Array Stage
- **Physical Gliding Cards**: Elements glide in 3D arc trajectories (`translate(deltaX, y)`) during swaps and settle with tactile landing pulses.
- **Dedicated Speed Controls**: Independent control sliders for algorithm execution step interval (`40ms - 1200ms`) and swap glide animation speed (`80ms - 900ms`).
- **Drag-and-Drop & Free Rearrangement**: Reorder elements directly with your mouse or load custom arrays via the built-in Studio Generator.

### 2. 🎯 Multi-Pointer Architecture & Scoped Isolation
- **Freeform & Code-Driven Pointers**: Create custom colored pointers (`i`, `j`, `left`, `right`, `mid`, `minIdx`, etc.) that smoothly snap above array slots.
- **Smart Pointer Isolation (`fn::var`)**: In recursive routines (like QuickSort or MergeSort), local function scopes retain isolated pointer representations.
- **Zero Card Overlap**: Intelligent collision offset prevents card text obstruction when multiple pointers point to the same index.

### 3. ⏪ Time-Travel Stepping (Backward & Forward)
- **Granular Execution Snapshots**: Step backward (`⏮️`) or forward (`⏭️`) at any point during code execution.
- **Reverse Physical Swaps**: Reversing a step triggers a reverse physical glide back to original slots with landing pulses.
- **Redo Stack Support**: Seamlessly navigate back and forth along your execution path.

### 4. 💻 Real In-Stream Chrome DevTools Console REPL
- **Unified Log Stream**: The prompt line (`>`) lives right inside the scrollable log stream—identical to Chrome DevTools.
- **Persistent Global Scope**: Evaluates expressions in global `window` scope (`(0, eval)`). Variables, objects, and functions declared remain available for subsequent commands.
- **Built-in Global Bindings**:
  - `arr` : Current live array.
  - `state` : Engine state (pointers, speed, history).
  - `swap(i, j)` : Trigger animated swaps interactively.
  - `console.table(arr)` : Interactive formatted table view.
  - `clear()` / `cls` : Clean console output.
  - `$_` : Result of the last evaluated expression.
  - `< undefined` return value logging just like modern browser DevTools.

### 5. ⚡ Zero-Boilerplate Standard Code Execution
- Write standard JavaScript algorithms without tedious custom helper wrappers:
  ```javascript
  let n = arr.length;
  for (let i = 0; i < n - 1; i++) {
    for (let j = 0; j < n - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        let temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
  ```
- The AST transpiler automatically instruments loops, comparisons, destructuring swaps (`[arr[i], arr[j]] = [arr[j], arr[i]]`), and pointers seamlessly in the background.

### 6. 📝 Draggable Sticky Notes & Canvas Workspace
- Drop floating, color-coded sticky notes on the canvas to jot down thoughts, invariants, or mathematical bounds while experimenting.
- Drag notes anywhere; their locations and text persist across session exports and project saves.

### 7. 🎬 Thinking & Action Session Recorder
- Record entire algorithmic thought processes, including manual card moves, pointer manipulations, and code runs.
- Export recordings as `.json` files or replay them step-by-step for classrooms, interviews, and presentations.

---

## 🚀 Quick Start & Live Access

### Use Online Instantly (No Installation Required)
Open your browser and visit:  
👉 **[https://favouritesir.github.io/Array-Lab/](https://favouritesir.github.io/Array-Lab/)**

### Run Locally
Since **Array-Lab** is built as an all-in-one standalone HTML application with CDN-backed CodeMirror, you only need a modern web browser:

```bash
# Clone the repository
git clone https://github.com/favouritesir/Array-Lab.git

# Navigate to the folder
cd Array-Lab

# Open in your browser (Windows)
start index.html

# Open in your browser (macOS)
open index.html

# Open in your browser (Linux)
xdg-open index.html
```

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| `Alt + E` / `F2` | **Focus Code Editor** |
| `Alt + C` / `F3` | **Focus Canvas / Playground Stage** |
| `Alt + K` / `Ctrl + \`` | **Focus Console REPL Prompt** |
| `Ctrl + Enter` / `F5` | Run Algorithm |
| `Space` | Pause / Resume Execution |
| `Shift + F5` | Stop Execution |
| `F10` / `Ctrl + .` / `]` | Step Forward (`⏭️`) |
| `F9` / `Ctrl + ,` / `[` | Step Backward / Time-Travel (`⏮️`) |
| `Enter` (inside modals) | Submit & Save Modal / Form |
| `Escape` | Cancel & Close Any Modal or Context Menu |
| `Arrow Left / Right` | Move Selected Pointer Left / Right |
| `Delete` | Remove Selected Pointer |
| `Ctrl + Z` / `Ctrl + Y` | Undo / Redo (Time Travel History) |
| `Ctrl + S` / `Ctrl + O` | Save / Open Project Snapshot (.json) |

---

## 🌐 Multilingual Documentation

Array-Lab is committed to global algorithmic literacy. Full localized documentations and codebases are available:

- 🇬🇧 **[English Documentation (Current)](README.md)**
- 🇧🇩 **[বাংলা ডকুমেন্টেশন (Bengali Guide & Code)](languages/bn/README.md)**
- 📘 **[User Guideline & Manual (English)](GUIDELINE.md)**
- 📗 **[ব্যবহার নির্দেশিকা (Bengali Guideline)](languages/bn/GUIDELINE.md)**

---

## 🤝 Contributing

Contributions, feature requests, and bug reports are warmly welcome!
1. Fork the Project (`https://github.com/favouritesir/Array-Lab/fork`)
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

Developed with ❤️ by **[Ashikur Rahman (favouritesir)](https://github.com/favouritesir)**
