# SDV-HGNN

Code submission for paper titled: SDV-HGNN: similarity-based dual view heterogeneous graph neural network method for drug adverse side effect prediction

Please reachout mayankkom.dev@gmail.com or mayankk.om@gmail.com for any copyright or permission issues.

Special mention to repos which are used for data 
- https://github.com/yuliyi/idse-HE/tree/main/data
- https://github.com/zhc940702/MGPred/tree/main/original_data

# 10-Fold CV
You can run and validate model performance directly using [notebook](exp/sdv-hgnn-train-cv.ipynb). This uses provided prep_data.

# Environment
All the experiments using an Intel(R) Core(TM) i7-12700 CPU @2.70GHz with DDR4 RAM 40 GB @3.2GHz and an NVIDIA GeForce TX 3070 Ti GPU. We implemented SDV-HGNN experimental setup using Python 3.7, PyTorch 1.13.1, PyG2.3, rdkit, and other packages. We particularly used PyG extensively for dealing with GNN designs and utility functions such as - neighborhood sampler and random negative sampling.

# Environment Reproducibility (WIP)
- conda env create -f environment.yml # update environment name and location in environment.yml
- conda activate sdv
- pip install -r installed_packages.txt