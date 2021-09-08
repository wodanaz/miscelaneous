# miscelaneous
here I post scripts (not necessarily optimal) but do the work 


To mount a shared folder in Desktop Ubuntu Guest



```bash

sudo mount -t vboxsf Shared_genomic MyShare

```


How to set up a conda environment"

```bash
cd

nano .condarc
channels:
  - bioconda
  - defaults
pkgs_dirs:
  - /data/yourlab/conda/conda_cache
envs_dirs:
  - /data/yourlab/conda/conda_envs


```


now... create your own environment

```bash
cd /data/yourlab/conda

nano environment.yml
name: aleconda
channels:
  - bioconda
  - conda-forge
dependencies:
  - seqtk
  - iqtree
  - bedtools
  - perl
  - hyphy
  - paml
  - phast
  - biopython
  - bedops
  - raxml-ng

```

final set up:

```bash
module load Anaconda3
conda env create --file environment.yml #--prefix /data/wraycompute/alejo/aleconda/singlecell
conda activate /data/yourlab/alejo/aleconda/

```

to update, modify your environment.yml and then do:

```bash
conda env update -f environment.yml --prune

```




