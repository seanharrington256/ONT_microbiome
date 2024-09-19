# Emu for Nanopore taxonomic assignment & read counts

<br>

### UNDER ACTIVE DEVELOPMENT

<br>


Emu is a tool to assign taxonomy that is specifically designed for long reads. 

Let's do a single sample defined by a single barcode.

<br>

We need to start by installing and loading Emu:

```
# load up miniconda 
module load miniconda3/24.3.0

# if you have not already created an emu environment and installed it with conda run these lines. You only need to run this part once
conda create -n emu
conda activate emu
conda install bioconda::emu -c conda-forge
```

* Be aware that the version of minconda can change periodically, so if the module load command doesn't work, check the available versions using `module spider miniconda`. 



<br>

Then we need to download a database for Emu. This is because Emu assignes taxonomy by matching the Nanopore reads against sequences of known taxonomy

```
# Change directory to wherever you want the database:
cd /project/inbreh/ONT_microbiome/emudb

wget --content-disposition https://osf.io/tswbp/download   # get the emu database
tar -xvf emu.tar      # extract it
```




<br>


Set the working directory:

```
# Directory with all the fastq raw data
cd /project/inbreh/ONT_microbiome/capstone_ont/WaterLib/20221107_1656_MN34633_FAO61889_d063b409/fastq_pass

# go into a single barcode
cd barcode11
```

<br>

If there are multiple fastq files, we need to concatenate these into a single file. If you only have a single file, you can skip this step.

```
zcat *.fastq.gz | gzip > barcode11.fastq.gz
```





