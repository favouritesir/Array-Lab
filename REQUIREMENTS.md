# 📋 Array-Lab: Software Requirements Specification (SRS)

> **Document Version:** 2.0.0  
> **Status:** Approved / Implemented  
> **Target Audience:** Developers, Educators, Students, Competitive Programmers & Algorithm Researchers  
> **Language:** English (For Bengali, see [`languages/bn/REQUIREMENTS.md`](languages/bn/REQUIREMENTS.md))

---

## 1. Executive Summary & Purpose

**Array-Lab** is a high-performance, zero-dependency, single-file interactive workbench for designing, testing, visualizing, and mastering array algorithms and memory structures. It provides developers and learners with a physical, glass-box environment to observe algorithm execution step-by-step with physical 3D glide swaps, multi-pointer tracking, live breakpoints, bidirectional time-travel debugging, an integrated in-stream Chrome-style DevTools REPL, and a human thinking session recorder.

---

## 2. System Architecture & Constraints

1. **Single-File Standalone Architecture**:
   - The workbench MUST run as a self-contained, client-only application in any modern web browser without requiring a backend server or build pipeline.
   - CDN-backed libraries are limited strictly to CodeMirror for professional syntax highlighting and code editing.
2. **Zero Arbitrary Delay Mandate**:
   - Animations, time steps, and DOM updates MUST be deterministic, driven by reactive promises, state resolvers, and CSS transitions. No arbitrary background sleep blocking the UI thread.
3. **Cross-Browser Compatibility**:
   - Full support for modern desktop and mobile browsers: Google Chrome, Mozilla Firefox, Apple Safari, Microsoft Edge, and Chromium-based mobile browsers.
4. **Data Isolation & Security**:
   - All code evaluation is performed strictly within the client-side browser runtime.
   - Project save/load uses local JSON serialization with validated schemas to prevent malformed injections.

---

## 3. Functional Requirements

### 3.1 Interactive Dual-Layer Array Stage
- **FR-1.1 (Slot & Card Representation)**: Each array element MUST render as an elevated visual 3D card resting inside an indexed slot `[0..N-1]`.
- **FR-1.2 (3D Physical Glide Animation)**: Swaps MUST NOT teleport; elements MUST physically glide along an arcing 3D parabolic trajectory (`translate(deltaX, y)`) and conclude with a tactile landing pulse.
- **FR-1.3 (Drag-and-Drop Reordering)**: Users MUST be able to reorder cards manually via mouse/touch drag-and-drop.
- **FR-1.4 (In-Place Value Editing)**: Double-clicking any card MUST allow immediate numeric value modification.
- **FR-1.5 (Accidental Click Protection)**: A simple left-click on a card MUST NOT move or reassign any pointer. Pointers are moved exclusively via dragging, navigation buttons, shortcuts, or context menu actions.
- **FR-1.6 (Array Studio Generator)**: A dedicated generator modal MUST support creating custom arrays (Random, Uniform, Sorted, Reversed, Nearly Sorted, Gaussian, Block-Partitioned) with duplicate filtering and custom range syntax.

### 3.2 Multi-Pointer Tracking & Context Controls
- **FR-2.1 (Dynamic Pointers)**: Support creation, renaming, color customization, and deletion of user/code pointers (`i`, `j`, `left`, `right`, `mid`, etc.).
- **FR-2.2 (Scoped Pointer Isolation)**: Pointers associated with recursive or helper functions (`fn::var`) MUST maintain isolated scopes, preventing collisions in divide-and-conquer routines.
- **FR-2.3 (Collision Stacking)**: When multiple pointers reference the same index, they MUST visually stack with vertical offsets so that labels and card values remain 100% visible.
- **FR-2.4 (Context Menu Suppression)**: The browser's default right-click menu MUST be suppressed across 100% of the application canvas and chrome.
- **FR-2.5 (Custom Context Menu)**: Right-clicking an array slot MUST open a custom context menu clamped to viewport boundaries.
- **FR-2.6 (Move Selected Pointer Here)**: Selecting "👉 নির্বাচিত পয়েন্টার এখানে আনুন" (Move selected pointer here) MUST relocate the active pointer (or default to the first pointer) to the target index, record a history snapshot, update logs, and immediately close the menu.

### 3.3 Stepper Engine & Bidirectional Time-Travel
- **FR-3.1 (Independent Speed Controls)**:
  - Algorithm step delay MUST be adjustable between `40ms` and `1200ms`.
  - Swap animation duration MUST be separately adjustable between `80ms` and `900ms`.
- **FR-3.2 (Playback States)**: Support Run, Pause, Stop (`Shift+F5`), Step Forward (`F10`, `Ctrl+.`, `]`), and Step Backward (`F9`, `Ctrl+,`, `[`).
- **FR-3.3 (Reverse Physical Glide)**: Stepping backward MUST physically glide swapped elements in reverse back to their previous slots with corresponding landing pulses.
- **FR-3.4 (Undo/Redo Stack)**: Manual changes and code steps MUST be captured as immutable snapshots, allowing full undo (`Ctrl+Z`) and redo (`Ctrl+Y`).

### 3.4 Zero-Boilerplate JavaScript IDE
- **FR-4.1 (Clean Code Standard)**: Users MUST be able to write natural JavaScript algorithm loops without custom visualization API boilerplate:
  ```javascript
  let temp = arr[i]; arr[i] = arr[j]; arr[j] = temp;
  // OR destructuring:
  [arr[i], arr[j]] = [arr[j], arr[i]];
  ```
- **FR-4.2 (AST Transpilation)**: The engine MUST automatically instrument variable assignments, comparisons, and swaps to sync visual pointers and trigger physics animations.
- **FR-4.3 (Gutter Breakpoints)**: Clicking code line numbers MUST toggle visual breakpoints that pause execution before that line executes.
- **FR-4.4 (Code Templates)**: Provide pre-loaded templates for Bubble Sort, Two Pointers, QuickSort partition, Cloud Merge Sort, and custom user algorithms.

### 3.5 Real In-Stream Chrome DevTools Console REPL
- **FR-5.1 (In-Stream Prompt)**: The prompt input (`>`) MUST live directly inside the scrollable log stream at the bottom, matching Google Chrome DevTools.
- **FR-5.2 (Global Persistence)**: Commands MUST evaluate in the global `window` scope (`(0, eval)`). Variables and functions declared MUST persist across subsequent evaluations.
- **FR-5.3 (Built-in REPL API)**:
  - `arr`: Live array state.
  - `swap(i, j)`: Programmatic physical swap.
  - `console.table(arr)`: Interactive tabular data view.
  - `clear()` / `cls`: Log stream wipe.
  - `$_`: Return value of the last evaluated expression.
  - `< undefined` logging for expressions without explicit returns.
- **FR-5.4 (Prompt Protection on Clear)**: Calling `clear()` or clicking the "Clear" button MUST remove log entries but MUST NEVER wipe, detach, or destroy `#consolePromptLine` and `#consoleInput`.

### 3.6 Draggable Sticky Notes & Thinking Trace Recorder
- **FR-6.1 (Canvas Notes)**: Users can create color-coded, draggable sticky notes anywhere on the canvas to annotate invariants, mathematical proofs, or complexity notes.
- **FR-6.2 (Session Recording)**: A built-in action recorder MUST capture time-stamped human actions (pointer shifts, value edits, code runs) with Pause/Resume/Stop controls.
- **FR-6.3 (Export/Import)**: Recorded traces and full workbench state MUST export/import as structured JSON.

### 3.7 Form Dialogs & Keyboard Ergonomics
- **FR-7.1 (Enter to Submit)**: Pressing `Enter` inside any dialog input or field (pointer modal, creator studio, top array input) MUST validate and submit immediately.
- **FR-7.2 (Escape to Cancel)**: Pressing `Escape` MUST cancel and close any active modal, dialog, or context menu.
- **FR-7.3 (Focus Shortcuts)**:
  - `Alt + E` / `F2`: Focus Code Editor.
  - `Alt + C` / `F3`: Focus Canvas / Array Stage.
  - `Alt + K` / ``Ctrl + ` ``: Focus Console REPL Prompt.
- **FR-7.4 (Typing Protection Guard)**: When the user is typing inside text fields or CodeMirror, single-key execution shortcuts (like `Space`, `]`, `[`) MUST NOT trigger workbench actions.

---

## 4. Responsive & Mobile Requirements

- **RR-1.1 (Desktop Split Layout `> 900px`)**: Horizontal and vertical splitters allow arbitrary panel resizing between Canvas, Code Editor, and History/Console.
- **RR-1.2 (Mobile & Tablet Tabbed Drawer `≤ 900px`)**:
  - The lower drawer MUST collapse into a clean, 3-tab unified navigation bar:
    1. **⚡ Code Editor**
    2. **📜 History Timeline**
    3. **💻 DevTools Console**
  - Switching tabs MUST automatically refresh CodeMirror layout (`editorInstance.refresh()`).
- **RR-1.3 (Canvas Collapse Prevention)**: The lower drawer height MUST be constrained via viewport-relative caps (`min(380px, 48vh)` on tablets, `min(340px, 45vh)` on phones) so that the array canvas NEVER collapses to zero height.
- **RR-1.4 (Array Track Overflow)**: The array track MUST scroll horizontally within `.board-viewport` on narrow screens, without causing window-level horizontal layout breaks.

---

## 5. Non-Functional Requirements (NFR)

1. **Performance**:
   - Card animations MUST use GPU-accelerated CSS transforms (`translate3d`, `scale`) targeting consistent 60 FPS.
   - Minimal DOM reflows: Card elements update existing slot attributes without re-creating track containers during execution.
2. **Robustness & Error Resilience**:
   - User algorithm syntax errors or infinite loops MUST be caught gracefully with descriptive error banners without crashing the host application.
   - Memory snapshots are capped at 500 entries to prevent memory leaks during long runs.
3. **Accessibility & Aesthetics**:
   - High-contrast Deep Cyberpunk Dark Neon color scheme with glowing pointer indicators.
   - Font typography optimized with clean monospaced fonts for code and numeric cards.
4. **Localization**:
   - Dual-language support: complete parity between English (`/`) and Bengali (`/languages/bn/`) codebases, interfaces, and documentation.

---

## 6. Verification & Quality Matrix

| Requirement Area | Test Criterion | Pass / Fail Condition |
| :--- | :--- | :--- |
| **Accidental Click** | Left-click on card | Pointers stay unchanged |
| **Context Relocation** | Right-click card -> Move selected pointer | Pointer moves to card index, snapshot logged |
| **Context Menu Safety** | Right-click anywhere else | Browser menu blocked, custom menu closed |
| **Modal Enter Key** | Press `Enter` in pointer/generator modal | Form validates & submits immediately |
| **Modal Escape Key** | Press `Escape` | Modals & context menus close immediately |
| **Console Clear** | Click Clear in DevTools | Logs wipe, prompt line remains focused & functional |
| **Mobile Tabs** | Resize to `<= 900px` & switch tabs | Single active tab shown, canvas remains visible |
| **Focus Shortcuts** | Press `Alt+E`, `Alt+C`, `Alt+K` | Respective pane/field receives focus |
