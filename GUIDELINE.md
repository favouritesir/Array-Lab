# 📘 Array-Lab User Guideline & Manual

Welcome to **Array-Lab**! This guide provides a step-by-step walkthrough on how to use every tool, feature, and visual control inside the workbench.

---

## 📑 Table of Contents
1. [Interface Overview](#1-interface-overview)
2. [Managing Arrays](#2-managing-arrays)
3. [Working with Pointers](#3-working-with-pointers)
4. [Writing & Running Code](#4-writing--running-code)
5. [Stepping & Time-Travel Debugging](#5-stepping--time-travel-debugging)
6. [Controlling Speed & Animation](#6-controlling-speed--animation)
7. [Using the Real In-Stream DevTools Console](#7-using-the-real-in-stream-devtools-console)
8. [Sticky Notes & Research Canvas](#8-sticky-notes--research-canvas)
9. [Human Thinking Recorder](#9-human-thinking-recorder)
10. [Saving, Exporting & Sharing Projects](#10-saving-exporting--sharing-projects)

---

## 1. Interface Overview

The interface is structured into three primary interactive zones:
- **Top Toolbar**: Quick access to array input, array generator studio, pointer creator, sticky notes, recorder controls, project save/load, and help modals.
- **Visual Canvas Stage (Middle Top)**: Live card slots, stacked pointer badges, physical swap animations, and free draggable sticky notes.
- **Split Workspace (Bottom)**: 
  - **Left**: CodeMirror JavaScript Code Editor with gutter breakpoints, line highlighting, and algorithm templates.
  - **Right**: Dual-tab panel featuring the **Execution History Timeline** and the **Chrome-Style DevTools Console REPL**.
  - A draggable vertical splitter (`resizer-v`) allows you to resize editor vs console width freely.

---

## 2. Managing Arrays

### Manual Loading
1. Enter comma-separated numbers in the top input field:  
   `10, 45, 2, 89, 34, 12, 7`
2. Click **"📥 লোড করুন"** or press `Enter` to refresh the stage.

### Array Creator Studio
Click **"✨ স্টুডিও"** on the top bar to generate specialized arrays:
- **Random Range**: Generate `N` random integers between min and max bounds.
- **Nearly Sorted**: Slightly perturbed array, ideal for testing Insertion Sort or Bubble Sort optimizations.
- **Reverse Sorted**: Strict descending order, ideal for worst-case benchmarks.
- **Duplicates / Few Unique**: Test stability and 3-way partitioning.
- Toggle **Live Preview** to inspect the data before loading it into the workspace.

---

## 3. Working with Pointers

### Manual Pointer Creation
1. Enter a pointer name (e.g. `i`, `left`, `mid`) in the top pointer input.
2. Select an accent color and click **"➕ পয়েন্টার যোগ"**.
3. Pointers appear in the lower Pointer Tray and directly above their corresponding array card.

### Drag & Keyboard Controls
- **Drag & Drop**: Click and drag any pointer badge across array slots.
- **Keyboard Navigation**: Click a pointer to select it, then press `Arrow Left` or `Arrow Right` to shift it. Press `Delete` to remove it.

---

## 4. Writing & Running Code

Array-Lab comes with zero-boilerplate standard JavaScript instrumentation. You don't need to manually inject `await sleep()` or custom visual helpers.

### Example: Bubble Sort
```javascript
let n = arr.length;
for (let i = 0; i < n - 1; i++) {
  for (let j = 0; j < n - i - 1; j++) {
    if (arr[j] > arr[j + 1]) {
      // Classic 3-line swap:
      let temp = arr[j];
      arr[j] = arr[j + 1];
      arr[j + 1] = temp;
    }
  }
}
```

### Breakpoints
Click any line number in the CodeMirror gutter to toggle a red breakpoint dot (`🔴`). When the algorithm runs, execution automatically pauses at marked lines so you can inspect memory and pointers.

---

## 5. Stepping & Time-Travel Debugging

Under the Right Panel toolbar:
- **`▶️ রান`**: Starts or resumes continuous execution.
- **`⏸️ পজ`**: Pauses continuous execution at the current statement.
- **`⏭️ এক স্টেপ`**: Executes the single next instruction.
- **`⏮️ পিছনের স্টেপ`**: Reverses the previous instruction, restores array elements, moves pointers back, and runs a reverse 3D physical swap animation.
- **`⏹️ থামাও`**: Aborts execution and resets the stepper engine.

---

## 6. Controlling Speed & Animation

- **`স্টেপ গতি` Slider**: Controls delay between subsequent algorithm steps (`40ms` to `1200ms`).
- **`সোয়াপ গতি` Slider**: Controls the physical glide duration for card exchanges (`80ms` to `900ms`). Adjust this higher to clearly see curved 3D crossing arcs during sorting demonstrations.

---

## 7. Using the Real In-Stream DevTools Console

Switch to the **"💻 কনসোল"** tab on the right panel.

- The prompt (`>`) is located directly inside the scrollable log stream.
- Click anywhere inside the console to immediately focus the input.
- **Persistent Global Variables**: Anything defined in the console stays in memory (`window`).
- **Useful Commands**:
  - `arr` : Inspect the current array.
  - `console.table(arr)` : Render formatted index-value table.
  - `swap(0, 5)` : Manually trigger a 3D animated swap.
  - `state.pointers` : View active pointer coordinates.
  - `clear` or `cls` : Clear the console log buffer.
  - `$_` : Re-evaluate the return value of your last command.

---

## 8. Sticky Notes & Research Canvas

- Click **"📝 স্টিকি নোট"** to generate a floating notepad.
- Drag the note title bar to place notes anywhere on the canvas.
- Change note background colors or write notes regarding invariants, edge cases, and algorithmic complexity.
- Notes are saved and reloaded automatically with project files.

---

## 9. Human Thinking Recorder

Click **"🔴 রেকর্ড"** to capture algorithmic walkthroughs:
- Records manual card drag-and-drops, pointer adjustments, notes, code runs, and timestamps.
- Pause/resume recording at any time.
- Click **"💾 এক্সপোর্ট"** to save a `.json` trace file that can be played back later.

---

## 10. Saving, Exporting & Sharing Projects

- **`💾 সেভ প্রজেক্ট`**: Downloads an all-in-one `.json` snapshot of your current array, pointers, notes, and code.
- **`📂 ওপেন প্রজেক্ট`**: Loads previously exported project files instantly into Array-Lab.

Enjoy exploring algorithms with Array-Lab!
