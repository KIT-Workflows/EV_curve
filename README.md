# EV Curve Workflow

**Version:** 0.0.1

**Author:** J. Schaarschmidt

## Description
This suite comprises seven Python scripts designed to automate the process of crystal structure analysis using Quantum Espresso. The scripts facilitate the relaxation of crystal structures, application of strain, calculation of energy and volume, and finally, visualization of energy-volume relationships in a graph.

### 1. FileInput for Pseudo-Potential files
- Input: `fname` - The name for the file.
- Input: `input_file` - The actual file to be used as input.
- Output: The utilized file for input.

### 2. `relax_qe.py` - Structure Relaxation:
- Creates a Quantum ESPRESSO input file for crystal structure relaxation (`relax.pwi`).
- Inputs: Element, lattice parameter, cubic flag, crystal type, k-points grid.
- Outputs: Quantum ESPRESSO input file (`relax.pwi`).

### 3. `resize.py` - Strain Application and Optimized Structure Creation:
- Reads the last structure from a Quantum Espresso output file (`relax.pwo`) and writes it as an ASE atoms object to a trajectory file.
- Applies specified strain to the relaxed crystal structure.
- Inputs: YAML file with strain value, trajectory file of the optimized structure.
- Outputs: Strained structure file, YAML file with output details (`output_dict.yml`).

### 4. `structure_creation.py` - YAML File Preparation:
- Copies `rendered_wano.yml` to `structure.yml` for further processing.
- Inputs/Outputs: Copies and renames a YAML file.

### 5. `qe_run.py` - Quantum ESPRESSO Calculation Execution:
- Executes a Quantum ESPRESSO calculation using specified input and output files.
- Inputs: Input file name from YAML (`rendered_wano.yml`).
- Outputs: Quantum ESPRESSO output file (`*.pwo`).

### 6. `calculate_energy.py` - Energy Calculation Input Preparation:
- Prepares input files for energy calculation in Quantum Espresso.
- Inputs: Element, file pattern, output filename, crystal type, k-points grid.
- Outputs: PWscf input file (`strain.pwi`).

### 7. `EV_analysis.py` - Energy-Volume Analysis and Plotting:
- Reads energy and volume data from Quantum Espresso output files and generates a plot.
- Inputs: Pattern for data files, output graph file name.
- Outputs: Graph image (`energy_volume_graph.png`), energy-volume data file, error log file.

## Parameters
- Element and lattice parameters for the crystal structure.
- Number of MPI processes for Quantum Espresso calculations.
- Strain values and file paths for input/output files.

## Functions
The suite provides functions for:
- Creating Quantum Espresso input files for relaxation and energy calculation.
- Optimizing crystal structures and applying strain.
- Executing Quantum Espresso calculations.
- Preparing energy calculation inputs.
- Analyzing and plotting energy vs. volume data.

## Output
The suite generates various output files, including:
- `relax.pwi`: Quantum Espresso input file for relaxation.
- `optimized_structure.traj`: Contains the optimized crystal structure.
- `output_dict.yml`: Contains output details from strain application.
- `*.pwo`: Quantum Espresso output files.
- `strain.pwi`: Quantum Espresso input file for energy calculation.
- `energy_volume_data.txt`: Contains energy and volume data.
- `error_data.txt`: Logs errors encountered during calculations.
- `energy_volume_graph.png`: Visual representation of the energy-volume relationship.