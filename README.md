# IntuiDATHE

**IntuiDATHE** (Intuitive Digital Lathe) is an open-source project aimed at unifying CAM and CNC control into a single, seamless application. By merging the standalone **IntuiCAM** (CAM software with 3D viewer and toolpath generation) and **IntuiGUI** (QtVCP-based LinuxCNC interface), IntuiDATHE will empower CNC operators with an integrated workflow: from CAD import to toolpath generation and machine execution—without ever leaving the GUI.

---

## Table of Contents

* [Project Overview](#project-overview)
* [Goals](#goals)
* [Key Features](#key-features)
* [Architecture](#architecture)
* [Roadmap](#roadmap)
* [Getting Started](#getting-started)
* [Contributing](#contributing)
* [License](#license)
* [Acknowledgements](#acknowledgements)

---

## Project Overview

Traditional CNC workflows require users to switch between separate applications: a CAM package for toolpath generation and a CNC controller GUI for machine operation. **IntuiDATHE** bridges this gap by embedding full CAM capabilities (powered by IntuiCAM) directly into a QtVCP GUI (IntuiGUI) for LinuxCNC. The result is a single, cohesive application where you can:

1. Import and visualize CAD models in 3D
2. Define machining setups and generate toolpaths
3. Simulate material removal
4. Post-process toolpaths to G-code
5. Load and run programs on the CNC machine—all without context switching.

## Goals

* **Unified Interface**: Combine IntuiCAM’s CAM core and 3D viewer with IntuiGUI’s LinuxCNC controls into one application.
* **Seamless Workflow**: Enable operators to go from design to machining within a single GUI panel or tab.
* **Modular Design**: Preserve IntuiCAM and IntuiGUI as independent libraries/repos, while orchestrating them through IntuiDATHE glue code.
* **Performance and Stability**: Ensure real-time CNC control is unaffected by CAM computations or 3D rendering.
* **Open Source Collaboration**: Invite contributions and extensions from the community.

## Key Features (Targeted)

The Application will preserve IntuiGUIs App-like architecture and IntuiCAMs Setup and Simulation Tabs will become APPs on the homescreen.

1. **3D CAD Import & Visualization**

   * Support for STEP, IGES, and common CAD formats (via OpenCASCADE).
   * Interactive QOpenGL-based viewer for part inspection and selection.

2. **CAM Operations & Toolpath Generation**

   * Facing, contouring, pocketing, drilling, threading, and custom operations.
   * Parameter-driven setup panels (cut depths, stepover, speeds, feeds).

3. **Simulation & Material Removal**

   * Layered or voxel-based stock removal visualization.
   * Play, pause, and step-through simulation modes.

4. **G-code Post-Processing**

   * Configurable post-processor templates for various controllers.
   * Direct export to LinuxCNC-ready programs.

5. **Integrated CNC Control**

   * All LinuxCNC QtVCP controls (jog, feed override, MDI, DROs).
   * Program loading and execution commands from within the CAM tab.

6. **Plugin Architecture**

   * Modular components for CAM, simulation, and control.
   * Future support for additional CAM cores or machine controllers.

## Architecture

IntuiDATHE consists of three repositories:

1. **IntuiCAM** (\*existing repo\*)

   * C++ CAM core with Python bindings (pybind11).
   * Qt6-based standalone GUI (for reference).

2. **IntuiGUI** (\*existing repo\*)

   * Python/PyQt5 QtVCP screens for LinuxCNC.
   * Core CNC controls and HAL integration.

3. **IntuiDATHE** (\*this repo\*)

   * Glue layer combining IntuiCAM core and widgets into QtVCP.
   * New QtVCP screens (in Python/C++) for embedded 3D viewer and CAM panels.
   * Build scripts, packaging, and documentation.

## Roadmap

> **Phase 0: Planning & Prototyping**
>
> * Finalize architecture and dependency versions (Qt5 vs Qt6 decision).
> * Prototype embedding of IntuiCAM’s QOpenGL3D widget in a minimal QtVCP screen.

> **Phase 1: Core Integration** 
>
> * Enable IntuiCAM Python API usage within QtVCP handlers.
> * Basic CAD import and display in LinuxCNC GUI.

> **Phase 2: CAM Workflow** 
>
> * Implement setup panels for operations (facing, pocketing, drilling).
> * Generate toolpaths and visualize in embedded viewer.

> **Phase 3: Simulation & G-code** 
>
> * Material removal simulation module integration.
> * Post-processing and export to LinuxCNC program loader.

> **Phase 4: Polishing & Packaging** 
>
> * Performance tuning, threading model improvements.
> * Single-package installer or AppImage for Linux.
> * Comprehensive documentation, tutorials, and example projects.

## Contributing

Contributions, issues, and feature requests are welcome! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) for details on the development workflow and code standards.

## License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

## Acknowledgements

* **IntuiCAM**: The powerful standalone CAM solution.
* **IntuiGUI**: QtVCP-based LinuxCNC interface.
* **OpenCASCADE**: For CAD import and 3D visualization.
* **LinuxCNC**: Real-time CNC control platform.
   

---
