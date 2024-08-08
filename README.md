# SDV-HGNN

Code submission for paper titled: SDV-HGNN: similarity-based dual view heterogeneous graph neural network method for drug adverse side effect prediction

Please reachout mayankkom.dev@gmail.com or mayankk.om@gmail.com for any copyright or permission issues.

Special mention to repos which are used for data 
- https://github.com/yuliyi/idse-HE/tree/main/data
- https://github.com/zhc940702/MGPred/tree/main/original_data

# Create Heterogeneous Data to Train SDV-HGNN
Similarity enhanced heterogeneous data is created using [notebook](exp/sdv-hgnn-prep-data.ipynb). The prep-data is dumped and available to be used for running 10-Fold CV

# 10-Fold CV
You can run and validate model performance directly using [notebook](exp/sdv-hgnn-train-cv.ipynb). This uses provided prep_data.

# Environment
All the experiments using an Intel(R) Core(TM) i7-12700 CPU @2.70GHz with DDR4 RAM 40 GB @3.2GHz and an NVIDIA GeForce TX 3070 Ti GPU. We implemented SDV-HGNN experimental setup using Python 3.7, PyTorch 1.13.1, PyG2.3, rdkit, and other packages. We particularly used PyG extensively for dealing with GNN designs and utility functions such as - neighborhood sampler and random negative sampling.

# Environment Reproducibility
- conda env create -f environment.yml # update environment name and location in environment.yml
- conda activate 

# Additional Data 
- jq for download using terminal
    - sudo apt-get install jq -y # to install using terminal
- idse-HE raw data # raw_data to run prep-data notebook
    - curl -s -H "Accept: application/vnd.github.v3+json" https://api.github.com/repos/yuliyi/idse-HE/contents/data | jq -r '.[].download_url' | while read url; do wget -P ../raw_data/idse-data "$url"; done 
- Download pre-trained mol2vec 
    - curl -s -H "Accept: application/vnd.github.v3+json" \
    https://api.github.com/repos/samoturk/mol2vec/contents/examples/models/model_300dim.pkl | \
    jq -r '.download_url' | \
    xargs -n 1 wget -P ../downloaded_models/mol2vec
- Pubchem data - PubChem Compound TOC: Drug and Medication Information - for Pubchem variant
    - wget -O raw_data/pubchem/all_comp.gz https://tinyurl.com/tjz98eyw && gunzip -c raw_data/pubchem/all_comp.gz > raw_data/pubchem/PubChem_compound.csv
- Drugbank: Prep data is avaialble - Raw data 
    - https://go.drugbank.com/releases/
- ADReCs
    - curl -s -H "Accept: application/vnd.github.v3+json" https://api.github.com/repos/zhc940702/MGPred/contents/original_data | jq -r '.[].download_url' | while read url; do wget -P ../raw_data/adrecs "$url"; done

# Variant Study
Different simpler variant are trained using notebook available in [notebook](variant-study).

# Hyper-param tuning
Script to run hyper-parameter tuning using ray-tune is available in [notebook](hyperparam/sdv-hgnn-train-cv-gatv2-hyper.ipynb).

# Model Analysis
Model analysis and case study code are available in [notebook](exp/model_analysis.ipynb).