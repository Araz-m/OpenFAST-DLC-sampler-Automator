# OpenFAST-DLC-Runner

A Python-based automation script for running sequential OpenFAST Design Load Case
(DLC) simulations by updating input files, executing OpenFAST, and organizing
simulation outputs.

This tool was developed for project-specific DLC studies where a large number of
wind seeds and wind speeds must be simulated without manual intervention.

---

## Overview

Running multiple OpenFAST simulations for a single DLC often requires repetitive
manual steps such as updating wind files, modifying HydroDyn inputs, executing
OpenFAST, and organizing output files.

OpenFAST-DLC-Runner automates this workflow by iterating over a set of wind files,
updating the corresponding OpenFAST input files, launching simulations via a
batch file, and systematically renaming and storing outputs for post-processing.

The script is designed as a **project-level automation utility**, not as a
general-purpose OpenFAST framework.

---

## Key Capabilities

- Iterates over multiple `.bts` wind files
- Extracts wind speed and seed information from filenames
- Automatically updates:
  - Inflow wind file references (`InflowFile.dat`)
  - HydroDyn input files based on wind speed
  - HydroDyn references in the `.fst` file
- Executes OpenFAST simulations via a Windows batch file
- Automatically handles command prompt interaction
- Organizes and renames output files by wind speed and seed
- Reduces the need for manual supervision during long DLC runs

---

## Typical Use Cases

- Running many wind seeds for a single DLC
- Automating repetitive OpenFAST input updates
- Overnight or long-duration simulation campaigns
- Academic and research-based DLC studies

---

## Installation

### Requirements

- Windows operating system
- Python 3.x
- OpenFAST installed and accessible via batch file

### Python Dependencies

Install required packages:
 pyautogui
 
```bash
pip install pyautogui
```

### Required libraries include:

- pyautogui

- os, shutil, subprocess (standard library)

---

## Usage
### 1. Prepare Input Files

- Place all wind files (.bts) in the Wind directory

- Place HydroDyn input files in the Wave directory

- Ensure wind file names follow a consistent naming convention
  (used to extract wind speed and seed)

### 2. Configure Script Paths

Edit the following paths in the script:

```bash
wind_directory = "../Wind"
hydrodyn_directory = "../Wave"
main_directory = "path/to/DLC_directory"
```

Ensure that:

- InflowFile.dat

- .fst file

- start_OpenFAST_v3-41.bat

exist in the main directory.

### 3. Run the Script

Execute the script from a terminal or IDE (VS Code recommended):

```bash
python project.py
```

VS Code is recommended for better scrollback and monitoring of long runs.

---

## Output Organization

Simulation outputs are automatically:

- Moved to the `Outputs/<DLC>` directory corresponding to the DLC being run

- Renamed using the format that is needed

Example:

```bash
OPT-MP-V{WindSpeed}_S{Seed}.out
OPT-MP-V{WindSpeed}_S{Seed}.outb
```

This structure simplifies post-processing and traceability.

---

# Project Structure
📂 OpenFast-DLC-Runner
├── 📁 DLC12             # Main Directory
│  └── 📂 Outputs           # Outputs are generated here
│     └── 📂 DLC12         # Organized simulation results
│  └── OpenFast-DLC-Runner.py      # Main script for automation
│  └── start_OpenFAST_v3-41.bat
│  └── openfast related files and directories
├── 📁 Wind              # Contains .bts wind files
├── 📁 Wave              # Contains HydroDyn input files

```bash

⚠️ Note: The exact file names and folder arrangement may vary depending on your project setup.
Ensure that `project.py`, OpenFAST input files, and the batch file are located in the same DLC folder when running the script.

```

---


----------------------------------------------------------------------------
# Contributing
 Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a new branch (git checkout -b feature-branch).
3. Commit your changes (git commit -m "Add new feature").
4. Push to your branch (git push origin feature-branch).
5. Open a pull request.
--------------------------------------------------------------------------------

A detailed *pdf manual* added as a guide
--------------------------------------------------------------------------
## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
