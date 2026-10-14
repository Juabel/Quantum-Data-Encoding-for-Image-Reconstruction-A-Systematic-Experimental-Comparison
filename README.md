# Quantum Data Encoding for Image Reconstruction

Repository containing the Python code developed for a master's thesis on image compression and reconstruction using hybrid quantum-classical autoencoders, and subsequently used in the research work comparing different quantum data encoding strategies.

## Overview

The project investigates the performance of five quantum data encoding strategies in a hybrid quantum-classical autoencoder framework:

- **Angle Encoding**
- **Amplitude Encoding**
- **Dense Angle Encoding**
- **Basis Encoding**
- **Single Qubit Encoding**

The experiments evaluate the encoding strategies in the context of image reconstruction, considering reconstruction quality, computational cost and qubit requirements.

The repository contains the main experiment scripts, quantum circuit implementations, data preparation utilities, parameter configurations and result visualisation scripts.

## Repository status and limitations

**Important:** The codebase is provided in its original research and development state and has not undergone a complete refactoring or systematic cleanup.

As a result, the repository includes experimental scripts, legacy implementations and auxiliary files that may not be required for the main experiments. Code organisation and inline documentation are also limited in some areas.

The descriptions in this README are intended to help navigate the codebase and identify the main components. They should not be interpreted as a guarantee that every file is currently used or that the complete experimental pipeline can be reproduced without additional configuration.

The code reflects the implementation used during the research process. Users intending to reuse or extend it should inspect the relevant scripts and verify their behaviour before making modifications or drawing conclusions from new executions.

## Repository structure

Most of the relevant implementation is located in the `Terceras pruebas/` directory.

The following sections describe the main files and their intended roles, based on the current understanding of the codebase.

### Core implementation

| File | Description |
|---|---|
| `Circuito.py` | Contains the principal quantum circuit implementations and encoding-related functions, including custom implementations of Dense Angle Encoding and Single Qubit Encoding. It also includes auxiliary quantum-state and circuit operations. |
| `Funciones_estado.py` | Provides functions for quantum-state manipulation, pixel-block processing, data normalisation, autoencoder initialisation, loss computation, training support, result storage and visualisation. It acts as a central interface between the experiment scripts and the circuit implementations. |
| `Inicializa_params.py` | Initialises the parameters used throughout the experiments, including qubit counts, circuit layers, learning rates, block sizes, encoding parameters and optimiser settings. |
| `Generador_datos.py` | Contains utilities for generating and preparing the datasets used in the experiments. |

### Experiment execution

The following scripts implement the main experimental workflows for the different encoding strategies.

| File | Description |
|---|---|
| `mainAmplitude_DenseAutoencoder.py` | Implements the experimental workflow for Amplitude Encoding and Dense Angle Encoding. The encoding strategy is selected through a configuration parameter. |
| `mainAngle_BasisAutoencoder.py` | Implements the corresponding workflow for Angle Encoding and Basis Encoding. |
| `mainSQOriginal.py` | Implements the workflow for Single Qubit Encoding. |
| `Main.py` | Contains additional experiment execution code. |
| `main_prueba.py` | Contains supplementary experimental code and tests. |

The main workflows generally involve data loading, parameter initialisation, image-block preparation, circuit configuration, training, development-set evaluation, testing and result storage.

The exact execution procedure and configuration requirements should be checked in the corresponding scripts before attempting to reproduce an experiment.

### Results and visualisation

| File | Description |
|---|---|
| `Grafico.py` | Generates the scatter plot used to present the best results in the research article. |
| `Graficador.py` | Contains an earlier plotting implementation that is not considered part of the main workflow. |

### Auxiliary and legacy files

| File | Description |
|---|---|
| `Archivador.py` | Earlier utility for organising directories, files and experimental results. Its current use has not been confirmed. |
| `Autoencoder.py` | Preliminary implementation used during the initial exploration of autoencoders. It is not required by the final experimental workflows, according to the current project notes. |
| `Paralelizador.py` | Experimental attempt to execute two autoencoders in parallel. It may provide a starting point for further investigation into parallel execution, but its behaviour should be verified. |
| `phase-field-compr` | Auxiliary code associated with an exploratory experiment using phase-field data. |
| `read_sim_data_for_training.py` | Script associated with the preparation or reading of simulation data for the phase-field experiment. |

The repository also contains a Jupyter notebook and additional scripts, tests and intermediate files generated throughout development. These are retained as part of the original project history and should not automatically be considered necessary for the main experiments.

## General experimental workflow

The main experimental pipeline can be summarised as follows:

1. **Data preparation:** load and prepare the image datasets.
2. **Parameter initialisation:** configure the encoding strategy, quantum circuit and training parameters.
3. **Image processing:** divide images into blocks and prepare the corresponding inputs.
4. **Quantum processing:** encode the input data and execute the encoder and decoder circuits.
5. **Training and evaluation:** train the hybrid autoencoder and evaluate its reconstruction performance.
6. **Testing and result storage:** execute the test workflow and save the relevant outputs for subsequent analysis.

The quantum circuit implementations and state-processing functions are primarily located in `Circuito.py` and `Funciones_estado.py`, respectively. The experiment-specific scripts coordinate the execution of the pipeline.

## Recommended starting point

For users wishing to explore the implementation, the following reading order is recommended:

1. `Generador_datos.py` — understand data preparation.
2. `Inicializa_params.py` — inspect the experiment configuration.
3. One of the `main*.py` scripts — follow the execution workflow for a specific encoding strategy.
4. `Funciones_estado.py` — examine the data-processing and autoencoder support functions.
5. `Circuito.py` — investigate the underlying quantum circuits and encoding implementations.
6. `Grafico.py` — inspect the generation of the article's result visualisation.

This order provides an overview of the experimental pipeline before introducing the lower-level circuit details.

## Branch information

The `develop` branch has historically been used as the working branch for this project.

Before inspecting or modifying the repository, check the available branches and their current state. If continuing the original development workflow, use `develop` where appropriate and verify that it contains the intended version of the code.

## Reproducibility and further development

This repository documents the implementation developed during the research process. Because the code has not been fully refactored, additional work may be required to reproduce the experiments or adapt the implementation to a different environment.

In particular, users should verify:

- The Python environment and required package versions.
- The availability and expected directory structure of the datasets.
- The configuration parameters used by each experiment.
- The relationship between the execution scripts and their auxiliary modules.
- The paths and configuration required to save and analyse results.

A complete environment specification and a fully automated reproduction procedure are not currently documented in this README.

## Citation

If you use this code in your research, please cite the associated research article once its final bibliographic information is available.

