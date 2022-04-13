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
conda env create --file environment.yml #--prefix /data/yourlab/conda/aleconda
conda activate /data/yourlab/conda/aleconda/

```

to update, modify your environment.yml and then do:

```bash
conda env update -f environment.yml --prune

```


To remove a keygen for hardac

```bash
  ssh-keygen -f "/home/alejo/.ssh/known_hosts" -R "hardac-login.genome.duke.edu"
```

To update / reclone (?) a repository when github is problematic

```bash

git remote set-url origin git@github.com:wodanaz/Assembling_viruses.git

```

Renaming a gtf file to include SPU gene names

```bash
cp Lvar.braker.gene.gtf Lvar.braker.gene2.gtf

for i in `cat jg2spu2.tab`; do 
  root1=`echo ${i} | cut -d'$' -f 1`;  
   root2=`echo ${i} | cut -d'$' -f 2`; 
   sed -ri "s@${root1}@${root2}@g"  Lvar.braker.gene2.gtf ;   
done

#to edit the attribute Name to gene_name

sed -ri "s/Name/gene_name/g"  Lvar.braker.gene2.gtf


```
