# EV Curve Workflow

**Version:** 0.0.1

**Author:** J. Schaarschmidt

## Description
This suite comprises seven Python scripts designed to automate the process of crystal structure analysis using Quantum Espresso. The scripts facilitate the relaxation of crystal structures, application of strain, calculation of energy and volume, and finally, visualization of energy-volume relationships in a graph.

### `QE_jobs.py` - Unified Quantum ESPRESSO Process:
- Handles the creation of Quantum ESPRESSO input files, structure relaxation (`relax.pwi`), output file preparation, and execution of relaxation and energy calculations.
- Inputs: YAML configuration file specifying the job type (`relaxation` or `energy calculation`), element, lattice parameter.
- Outputs: Quantum ESPRESSO input (`*.pwi`) and output (`*.pwo`) files, copied and prepared YAML file for further processing.

### `resize.py` - Strain Application and Optimized Structure Creation:
- Reads the optimized structure from the QE output file, applies specified strain, and prepares the structure for subsequent calculations.
- Inputs: Strain value, trajectory file of the optimized structure.
- Outputs: File of the strained structure, YAML file detailing the output (`output_dict.yml`).

### `calculate_energy.py` - Energy Calculation Input Preparation:
- Prepares input files for energy calculations in Quantum Espresso, following the application of strain.
- Inputs: Element, file pattern, output filename, crystal type, k-points grid.
- Outputs: PWscf input file for energy calculations (`strain.pwi`).

### `EV_analysis.py` - Energy-Volume Relationship Analysis and Plotting:
- Analyzes energy and volume data derived from QE output files, generating a comprehensive plot to illustrate the relationship.
- Inputs: Data file pattern, output filename for the generated graph.
- Outputs: Graphical visualization (`energy_volume_graph.png`), data file containing energy-volume points, and an error log file.

## Parameters
Parameters include but are not limited to:
- Crystal structure details (element, lattice parameters),
- Computational details (number of MPI processes),
- Strain values,
- File paths required for input and output.

## Functions
The `EV Curve` workflow facilitates:
- Preparation and execution of Quantum Espresso jobs for relaxation and energy calculation.
- Optimization of crystal structures with strain application.
- Graphical representation of energy vs. volume relationships for analyzed structures.

## Output
Generated outputs encompass:
- Quantum Espresso input (`*.pwi`) and output (`*.pwo`) files for various computational operations.
- `optimized_structure.traj`: Featuring the finalized, optimized crystal structure.
- `output_dict.yml`: Detailing the outputs from strain applications.
- `strain.pwi`: Quantum Espresso input file tailored for energy calculations.
- `energy_volume_data.txt`: Compiling the collated energy and volume data.
- `error_data.txt`: Documenting encountered calculation errors.
- `energy_volume_graph.png`: A graph depicting the energy-volume relationship.