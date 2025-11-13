#  TransFusion

This repository contains the evaluation setups for the paper "TransFusion: End-to-End Transformer Acceleration via Graph Fusion and Pipelining."

## System Requirements

| Environment | Version |
|----|---------|
| Ubuntu | 24.04.2 LTS | 
| Python | 3.10+ |

## Installation 

### Step 1: Clone the Repository

Clone the repository and its submodules recursively:

```bash
git clone --recurse-submodules git@github.com:FusedMindLab/TransFusion.git
cd TransFusion
```

### Step 2: Install Dependencies

Install the required Python packages and system libraries:

```bash
pip install -r requirements.txt
sudo apt install libboost-all-dev
```

Ensure `~/.local/bin` exists and is included in your `PATH`:
```bash
mkdir -p ~/.local/bin
export PATH=$PATH:~/.local/bin
```

### Step 3: Install Timeloop and Accelergy:

Navigate to the Timeloop/Accelergy infrastructure directory and install:

```bash
cd third_party/accelergy-timeloop-infrastructure
make install_accelergy
pip install ./src/timeloopfe
make install_timeloop
```

For more information, see the [Accelergy-Timeloop GitHub repo](https://github.com/Accelergy-Project/accelergy-timeloop-infrastructure/) and the [installation guide](https://timeloop.csail.mit.edu/v4/installation).

### Step 4: Install Accelergy Plugin

Install the custom Accelergy plugin and return to the root directory:

```bash
cd src/accelergy-library-plug-in
pip install .
cd ../../../..
```

### Step 5: Copy Custom Component Tables

Copy the custom component table for FuseMax to the appropriate Accelergy plugin directory. For example, if you are using a conda environment:
```bash
cp -r third_party/FuseMax/custom_pc_2021 ~/miniconda3/envs/<your-conda-env-name>/share/accelergy/estimation_plug_ins/accelergy-library-plugin/library
```

## Run Experiments

### Run from Command Line

Activate the environment by running:

```bash
source set-env.sh
```

To start the evaluation, run:

```bash
python3 main.py
```

Generated figures and results will be saved in the `results/` directory.
