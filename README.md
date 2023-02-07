# Snakephlyo

Snakemake workflow to create phylogenetic trees using supertree and supermatrix approach from gene sequences in fasta format.

The workflow conducts the following steps:

* Multiple sequence alignment using MAFFT (https://github.com/GSLBiotech/mafft)
* Alignment trimming with ClipKIT (https://github.com/JLSteenwyk/ClipKIT)
* Genetree creation using IQ-TREE (https://github.com/Cibiv/IQ-TREE)
* Supertree creation with ASTRAL (https://github.com/smirarab/ASTRAL) 

## Installation

Clone the repository:

```
git clone https://github.com/LKress/snakephylo.git
```

```
cd snakephylo
```

Install snakemake (see https://snakemake.readthedocs.io/en/stable/getting_started/installation.html)

```
conda create -n snakemake -c conda-forge -c bioconda snakemake
```

## Usage

Create a workdirectory with the following directory structure:

```
<workdir>/
├── data/
    ├── <dataset1>/
    │    ├── <gene1>.fasta
    │	 ├── <gene2>.fasta
    ├── <dataset2>/
         ├── <gene1>.fasta
         ├── <gene2>.fasta
```

All names in in brackets (`<>`) can be chosen freely.

To run a dry run execute:

```
snakemake --cores 2 --use-conda --directory /path/to/workdir -n
```

To execute the pipeline:

```
snakemake --cores 2 --use-conda --directory /path/to/workdir
```

## Output

The resulting supertree is stored at `/path/to/workdir/results/trees/SUPERTREE.nwk`.

It can be viewed e. g. on https://itol.embl.de/.
