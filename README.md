---

# LoCoGNN
This project is a modified fork of the official [DGL (Deep Graph Library)](https://github.com/dmlc/dgl). We have created a new branch in our fork and integrated our custom code for experiments and performance analysis.
Please follow the DGL installation process if you get any errors.

---
## 🖥️ System Configuration

We conducted our experiments on a machine with the following specifications:

- **GPU**: NVIDIA RTX A6000 with 48 GB memory  
- **CPU**: Intel(R) Xeon(R) Gold 5218, 16 cores @ 2.30 GHz  
- **RAM**: 512 GB  
- **Software Stack**:
  - DGL v2.2.2_cu121  
  - PyTorch v1.13.0  
  - CUDA 12.1  
  - GCC 11.4.0  

---

## 📦 Installation Process

### Option 1: Install via Conda Environment File

To quickly set up the exact same environment used in our experiments:

```bash
conda env create -f locognn.yml
conda activate locognn
```

Then proceed with the build and install:

```bash
bash script/build_dgl.sh -g
cd python
python setup.py install
python setup.py build_ext --inplace
```

> Make sure you have CUDA 11.7 installed and accessible.

---

### Option 2: Install from Source Manually

## Install from Source

Download the source files from GitHub:

```bash
Download the zip and extract
cd metis_based_sampling
git submodule update --init --recursive
```

### Linux Dependencies

#### For Debian/Ubuntu users:

```bash
sudo apt-get update
sudo apt-get install -y build-essential python3-dev make cmake
```

#### For Fedora/RHEL/CentOS users:

```bash
sudo yum install -y gcc-c++ python3-devel make cmake
```

### Conda Environment Setup for GPU Development

```bash
bash script/create_dev_conda_env.sh -g 12.1
```

To check additional configuration options:

```bash
bash script/create_dev_conda_env.sh -h
```

### Build the Shared Library for GPU

```bash
bash script/build_dgl.sh -g
```

For more build options:

```bash
bash script/build_dgl.sh -h
```

### Install Python Bindings

```bash
cd python
python setup.py install
# Build Cython extensions
python setup.py build_ext --inplace
```

---


### After successful installation, the framework is ready to execute 
### Note: While building and installing the framework, the Metis based sampling is compiled and installed

### Move to graphsage directory
```bash
cd examples/pytorch/graphsage/
```

### Run the Script 
```bash
bash run_script_respmm.sh ogbn-arxiv 100
```
### This script runs for all fanouts and batch sizes specified in the paper for the 100-epoch provided dataset.
