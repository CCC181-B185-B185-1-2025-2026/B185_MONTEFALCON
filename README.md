# B185_MONTEFALCON
This is a powerful, single-file HTML5 and JavaScript-based tool for simulating and visualizing the behavior of various digital logic flip-flops. It allows users to draw input waveforms directly on a canvas and instantly see the resulting output based on a configurable, true-to-life simulation engine.

# Interactive Flip-Flop Timing Diagram Tool
It's the perfect tool for students learning digital electronics, engineers who need to quickly visualize a sequence, or educators looking for an interactive teaching aid.

## Features

- **Interactive Drawing:** Click and drag directly on the canvas to draw your `CLK`, `D`, `T`, `J`, `K`, `PRE`, and `CLR` input waveforms.
- **Multiple Flip-Flop Types:** Accurately simulate the most common flip-flops:
    -   **D-Type** (Data)
    -   **T-Type** (Toggle)
    -   **JK-Type**
- **Configurable Simulation Engine:**
    -   **Clock Trigger:** Choose between **Positive Edge** and **Negative Edge** triggering.
    -   **Asynchronous Inputs:** `PRE` (Preset) and `CLR` (Clear) can be set to **Active-Low** or **Active-High** to match different IC conventions.
    -   **Initial State:** Define whether `Q` should start at `0` or `1`.
- **Visual Clarity:**
    -   **Snap-to-Grid:** Enforce clean, aligned waveforms with a configurable number of columns.
    -   **Logic Level Indicators:** Each signal row clearly displays `1` and `0` markers.
    -   **Solver Edge Lines:** When you solve, vertical dashed lines appear, showing the exact clock edges that triggered a change in the output.
- **User-Friendly Interface:**
    -   **Undo:** Made a mistake? Undo your last drawing action.
    -   **Clear:** Start over with a clean slate.
    -   **Save as Image:** Export the entire timing diagram as a high-quality PNG file, perfect for reports and documentation.
- **Zero Dependencies:**
    -   Everything is contained in a **single HTML file**. No need for servers, installations, or external libraries. Just download and open in any modern web browser.

## How to Use

1.  **Download:** Download the `index.html` file from this repository.
2.  **Open:** Open the file in your favorite web browser (e.g., Chrome, Firefox, Safari, Edge).
3.  **Configure:** Use the dropdown menus at the top to select your desired Flip-Flop Type, Trigger Edge, and other simulation parameters.
4.  **Draw:** Click and drag on the input rows (`CLK`, `D`, etc.) to create your desired input waveforms. The drawing will automatically snap to the grid columns.
5.  **Solve:** Click the **Solve** button. The `Q` and `Q̅` output waveforms will be generated instantly, with red dashed lines indicating the trigger points.
6.  **Save:** Click the **Save Image** button to download a PNG of your completed diagram.

## Controls Explained

| Control              | Description                                                                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Flip-Flop**        | Switches the simulation logic and UI between `D`, `T`, and `JK` types. This will clear the canvas.                                       |
| **Initial Q**        | Sets the starting value (`0` or `1`) for the `Q` output at the beginning of the simulation.                                              |
| **Trigger**          | Sets the clock edge that the flip-flop will react to (`Positive Edge` or `Negative Edge`).                                               |
| **Async Active**     | Defines whether the `PRE` and `CLR` inputs are `Active-Low` (a `0` activates them) or `Active-High` (a `1` activates them).             |
| **Snap Cols**        | Sets the number of columns in the grid. Drawing will snap to these columns. Changing this will clear the canvas.                         |
| **Solve**            | Runs the simulation based on the current configuration and input waveforms.                                                              |
| **Undo**             | Reverts the last drawing action.                                                                                                         |
| **Clear**            | Resets all waveforms to their default inactive state.                                                                                    |
| **Save Image**       | Prompts a download of the current canvas view as a `timing_diagram.png` file.                                                            |

## Simulation Logic

The simulator is designed to closely mimic the behavior of real-world integrated circuits by following a strict order of operations for every point in time:

1.  **Asynchronous Priority:** The `PRE` (Preset) and `CLR` (Clear) inputs are checked first. If they are in their active state, they will **immediately** override any clock or data inputs and force the output to the corresponding state.
2.  **Edge Triggering:** If and only if the asynchronous inputs are inactive, the simulator checks for an active clock edge (rising or falling, based on the configuration).
3.  **Correct Data Sampling:** To respect the "setup time" of a real flip-flop, the simulator samples the value of the data inputs (`D`, `T`, `J`, `K`) at the moment **just before** the clock edge occurs.
4.  **Hold State:** If neither an asynchronous override nor a clock edge is detected, the flip-flop holds its previous state.

## Contributing

This is a self-contained project, but feedback, bug reports, and feature suggestions are always welcome! Feel free to open an issue in this repository.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
