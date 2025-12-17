# AlgoQuestVR 🎮📚  
Interactive VR Puzzles for Learning Sorting Algorithms

AlgoQuestVR is a Unity-based VR experience that turns classic sorting algorithms into interactive, replayable puzzles. Instead of watching passive 2D animations, learners physically grab, compare, and place elements in a virtual scene, while a world-space pseudocode panel shows how each action maps to algorithm steps.

The project currently focuses on:

- **Bubble Sort**
- **Quick Sort**

Each algorithm has:

- A **Demo** mode (guided walkthrough)  
- A **Puzzle** mode (hands-on problem solving)

---

## ✨ Key Ideas

- **Embodied learning**: Learners manipulate a rack of spheres representing array elements using ray or direct grab.
- **Code grounding**: A pseudocode panel highlights the current step in green and explains in plain English which elements are being compared and whether they will be swapped.
- **Replayable levels**: Demo and puzzle modes are short, focused scenes designed for repeated practice with different element orders.
- **Fast feedback**: Color and snapping feedback make correct vs. incorrect moves obvious without heavy text.

---

## 🧱 System Overview

AlgoQuestVR is built with:

- **Engine**: Unity 6  
- **XR Framework**: Unity XR Interaction Toolkit  
- **Target Platform**: Meta Quest (ray + direct grab controllers)

High-level structure:

- **Hub Scene**  
  - Central “home” space with two algorithm entry points:
    - Bubble Sort
    - Quick Sort  
  - Each algorithm exposes:
    - **Demo** scene
    - **Puzzle** scene

- **Algorithm Scenes (Demo + Puzzle for each algorithm)**  
  Each scene is assembled at runtime via C# scripts:
  - A **rack of spheres** representing array elements (values 1..N, shuffled).
  - **UI panels**:
    - Left: demo controls (Play, Next, Reset, Shuffle)
    - Right: pseudocode and step explanation (when enabled).
  - A **navigation panel** behind the player to jump between levels / return to hub.

- **Algorithm Engine**  
  - Step-wise engine that simulates comparisons and swaps.
  - In **Demo**:
    - Drives animations, pseudocode highlighting, and English explanations.
  - In **Puzzle**:
    - Compares learner actions against the next valid algorithm step rather than auto-playing.

---

## 🎮 Interaction & Feedback Design

- **Interaction Modes**
  - **Ray grab**: Grab spheres at a distance with a controller ray.
  - **Direct grab**: Grab spheres up close, like physical objects.

- **Visual Feedback**
  - Spheres start **grey**.
  - Currently compared elements are highlighted **yellow**.
  - Incorrect actions in Puzzle mode cause **red flashes** and revert to the last valid state.
  - When the entire rack is correctly sorted, all spheres turn **green**.

- **Snapping & Validation**
  - Spheres are placed into discrete positions using XR socket interactors.
  - The system checks correctness in real time.
  - Invalid placements:
    - Flash the rack red.
    - Reset to the previous valid configuration.

- **Demo Controls**
  - **Play**: Automatically run through the algorithm.
  - **Next**: Step through one comparison/swap at a time.
  - **Reset**: Return to the original arrangement.
  - **Shuffle**: Generate a new random permutation.

Learners can still pick up spheres in Demo mode, but the control panel can always restore a clean state.

---

## 🧪 Experiments (In-Class Pilot)

We ran a small **formative pilot** with **4 in-class participants**. Each learner tried both Demo and Puzzle modes for Bubble Sort and Quick Sort.

**Observed positives:**

- Grabbing and moving spheres made the sorting process feel more intuitive than a traditional 2D animation.
- Demo controls were useful for *step-by-step* understanding before attempting puzzles.

**Feedback that led to changes:**

- Improve **scene lighting** so the rack and UI panels are easier to read at a glance.
- Clarify the **ordering of options in the hub/menu** so Demo vs. Puzzle is more discoverable.

**Changes implemented:**

- Adjusted lighting/contrast in key scenes.
- Reorganized the hub so algorithm and mode choices are more clearly structured.

---

## 🛠 Requirements

* **Unity**: Unity 6 (or compatible 6.x release)
* **Packages**:

  * XR Interaction Toolkit
  * XR Plug-in Management (for Quest / OpenXR)
* **Hardware**:

  * Meta Quest (2/3/Pro) or similar standalone VR headset
  * Or PC VR setup configured with appropriate runtime

---

## 🚀 Getting Started

1. **Clone the repo**

   ```bash
   git clone https://github.com/<your-username>/AlgoQuestVR.git
   cd AlgoQuestVR
   ```

2. **Open in Unity**

   * Open Unity Hub
   * Add the project folder
   * Open it with **Unity 6**.

3. **Check XR setup**

   * Ensure XR Plug-in Management is enabled for your target platform.
   * Verify the XR Interaction Toolkit is installed and configured.

4. **Open the Hub scene**

   * Open `Hub.unity` (or your main hub scene).
   * Press **Play** in the editor (for quick testing with mouse/keyboard) or build to a Quest device for full VR interaction.

---

## 🎮 How to Use

### In VR (recommended)

1. **Launch the built app** on your Quest.
2. In the **hub**, walk or ray-point toward:

   * **Bubble Sort** or **Quick Sort**
3. Choose:

   * **Demo**: Guided, with playback controls and pseudocode.
   * **Puzzle**: You perform the sorting manually with feedback.
4. Use:

   * Controller **ray** or **direct grab** to move spheres.
   * Buttons on panels to control playback, reset, or shuffle.

### In the Editor

* Use the **Game** view with XR set up (or mock input).
* Interact using your VR headset connected via Link/Air Link or equivalent.

---

## 📄 Research / Poster

AlgoQuestVR is accompanied by an IEEE VR–style **poster paper** written in LaTeX, describing:

* Motivation and design goals
* System architecture
* Interaction and feedback design
* Formative in-class experiment
* Future directions

Check the LaTeX file in this repo.

---

## 🔭 Future Work

Planned or possible extensions:

* Add more algorithms:

  * Insertion Sort, Merge Sort, basic graph traversals (e.g., BFS/DFS).
* Add adaptive scaffolding:

  * Context-sensitive hints when learners struggle.
* Run a larger user study:

  * Compare AlgoQuestVR against standard 2D visualizations on learning gains and transfer to code tracing/debugging.
* Explore collaborative modes:

  * Two learners solving a puzzle together and explaining steps to each other.

---

## 📜 License

This project is open source.
License details: see the `LICENSE` file in this repository (e.g., MIT or similar).