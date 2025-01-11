# Reagle Microseismic Pipeline

<p align="center">
</p><br><br><br><br>


[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

!This package is under construction!

This repository contains instructions and scripts for setting up and running the **Reagle Microseismic Pipeline**. Follow the steps below to create and configure the environment, build required libraries, and install packages.
## Creating Conda Environment

conda create -n microseismic python=3.10 obspy numpy scipy pandas matplotlib h5py ipython jupyter cartopy colorcet -c conda-forge -y
conda activate microseismic

## Installing required tools
conda install pytorch=2.3.1 torchvision torchaudio=2.3.1 pytorch-cuda=11.8 -c pytorch -c nvidia -y
conda install pytorch-cluster=1.6.3 -c pyg
conda install pytorch-scatter=2.1.2 -c pyg
conda install -c conda-forge scikit-fmm
conda install gcc
conda install -c nvidia cuda-nvcc cuda-toolkit

## Installing beam power
git clone https://github.com/ebeauce/beampower.git
python setup.py build_ext
pip install .

## Installing fast_matched_filter
git clone https://github.com/beridel/fast_matched_filter.git
vi Makefile
Put '#' in front of '-gencode arch=compute_35,code=sm_35\'
Quit vi
python setup.py build_ext
pip install .

## Installing additional python packages
pip install pykonal
pip install seisbench
pip install torch_geometric==2.5.3
pip install cvxpy
pip install basemap
pip install jupyterlab-git

## Installing NonLinLoc
git clone https://github.com/alomax/NonLinLoc
cd src
mkdir bin
cmake .
make 
vi ~/.bashrc
export PATH=/YOUR/PATH/TO/NonLinLoc/src/bin:$PATH
source ~/.bashrc

## installing Reagle_microseismic (currently mostly from BPMF package)
git clone https://github.com/Jaewoo-Kim-Rice/Reagle_microseismic.git
cd ./Reagle_microseismic
python setup.py build_ext
pip install -e . (-e flag makes you can develop the package in your local directory)


## Contact
jk103@rice.edu