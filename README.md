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

Create a workdirectory and within this directory create a directory called `data`.
In this `data` directory, copy or symlink the input orthologuous genes in fasta format with the suffix `.fasta`.
The filenames should contain the genename (`<gene>.fasta`). 

```
mkdir /path/to/workdir/
mkdir /path/to/workdir/data
cp /path/to/orthologues/*.fasta /path/to/workdir/data
```

To run a dry run execute:

```
snakemake --cores 2 --use-conda --directory /home/student7/phylogeny/testinput/ -n
```

To execute the pipeline:

```
snakemake --cores 2 --use-conda --directory /home/student7/phylogeny/testinput/
```

## Output

The resulting supertree is stored at `/path/to/workdir/results/trees/SUPERTREE.nwk`.

It can be viewed e. g. on https://itol.embl.de/.
