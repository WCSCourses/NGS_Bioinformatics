<img src="https://coursesandconferences.wellcomeconnectingscience.org/wp-content/themes/wcc_courses_and_conferences/dist/assets/svg/logo.svg" width="300" height="50"> 

# Next Generation Sequencing VM Setup Guide

About this markdown: This guide provides step-by-step instructions to set up a bioinformatics environment for the WCS NGS course, both lab and informatics.
Pre-requisites: Set up Virtual Machine with miniforge installed (refer to [Internal SOP on how to create, develop and deploy virtual machines](https://github.com/WCSCourses/WCS_Internal_Guides/blob/main/VM_Guide.md))

Also, find at the end [NGS Software Table](#ngs-software-table) and [NGS Environment](#ngs-environment) 


## **Step 1: Update System Packages**
Run the following command to ensure your system is up to date:

```bash
sudo apt-get update && sudo apt-get install -y git wget && sudo apt-get clean
```

## **Step 2: Download Course Data**
Create a directory and clone the necessary GitHub repositories:

```bash
cd $HOME
mkdir -p course_data
cd course_data
git clone http://www.github.com/WTAC-NGS/unix
git clone http://www.github.com/WTAC-NGS/data_formats
git clone http://www.github.com/WTAC-NGS/read_alignment
git clone http://www.github.com/WTAC-NGS/variant_calling
git clone http://www.github.com/WTAC-NGS/structural_variation
git clone http://www.github.com/WTAC-NGS/rna_seq
git clone http://www.github.com/WTAC-NGS/chip_seq
git clone http://www.github.com/WTAC-NGS/assembly
git clone http://www.github.com/WTAC-NGS/igv
```

To exit the course_data folder, enter the following command:
```bash
cd
```

## **Step 3: Create and Set Up a Conda Environment**
Activate Conda and create a new environment for the bioinformatics tools:

```bash
source $HOME/miniconda/etc/profile.d/conda.sh
conda create -n ngsbio breakdancer=1.4.5 -y
conda activate ngsbio
```

## **Step 4: Install Core Bioinformatics Tools**
```bash
conda install -y samtools=1.15.1
conda install -y bcftools=1.15.1
conda install -y bedtools=2.30.0
conda install -y openmpi=4.1.4
conda install -y r-base=4.0.5
conda install -y bowtie2=2.4.5
conda install -y macs2=2.2.7.1
conda install -y meme=5.4.1
conda install -y ucsc-bedgraphtobigwig=377
conda install -y ucsc-fetchchromsizes=377
conda install -y r-sleuth=0.30.0
conda install -y bioconductor-rhdf5=2.34.0
conda install -y bioconductor-rhdf5filters=1.2.0
conda install -y bioconductor-rhdf5lib=1.12.0
conda install -y hdf5=1.10.5
conda install -y hisat2=2.2.1
conda install -y kallisto=0.46.2
```
### **Testing Core Bioinformatics Tools (Within Conda Environment)**
```bash
conda activate ngsbio
samtools --version
bcftools --version
bedtools --version
mpirun --version
R --version
bowtie2 --version
macs2 --version
meme --version
ucsc-bedgraphtobigwig
ucsc-fetchchromsizes
R -e 'library(sleuth)'
R -e 'library(rhdf5)'
R -e 'library(rhdf5filters)'
R -e 'library(rhdf5lib)'
h5cc -showconfig
hisat2 --version
kallisto version
conda deactivate
```

## **Step 5: Install Read Alignment Tools**
```bash
conda install -y bwa=0.7.17
```
### **Testing Read Alignment Tools**
```bash
conda activate ngsbio
bwa
conda deactivate
```

## **Step 6: Install Genome Assembly Tools**
```bash
conda install -y assembly-stats=1.0.1
conda install -y canu=2.2
conda install -y kmer-jellyfish=2.3.0
conda install -y seqtk=1.3
conda install -y velvet=1.2.10
conda install -y wtdbg=2.5
conda install -y genomescope2=2.0
```

### **Testing Genome Assembly Tools**
```bash
conda activate ngsbio
assembly-stats --version
canu --version
jellyfish --version
seqtk
velvetg
wtdbg2
conda deactivate
```

## **Step 7: Install Variant Analysis Tools**
```bash
conda install -y freebayes=0.9.21.7
```

### **Testing Variant Analysis Tools**
```bash
conda activate ngsbio
freebayes --version
conda deactivate
```

## **Step 8: Install Java-Based Tools**
```bash
conda install -y gatk4=4.2.6.1
conda install -y picard-slim=2.27.4
```

### **Testing Java-Based Tools**
```bash
conda activate ngsbio
gatk --version
picard -h
conda deactivate
```

## **Step 9: Install Structural Variant Analysis Tools**
```bash
conda install -y minimap2=2.24
conda install -y sniffles=2.0.7
```

### **Testing Structural Variant Analysis Tools**
```bash
conda activate ngsbio
minimap2 --version
sniffles --version
conda deactivate
```

To get out of the conda environment, enter the following command:
```bash
conda deactivate
```

## **Chipseq project**
```bash
conda create -n chipseq-project r-ngsplot
conda activate chipseq-project
conda install python=2.7
conda deactivate
```

### **Test ChipSeq Environment**
```bash
conda activate chipseq-project
R --version  # Check if R is installed
python --version  # Check Python version
ngsplot --help  # Check if NGSplot is installed correctly
```
If all commands return a valid response, the **ChipSeq environment** is set up correctly.

Deactivate the environment:
```bash
conda deactivate
```

## **Step 10: Install Additional Dependencies**
```bash
conda install -y pytz edlib threadpoolctl six scipy networkx joblib cython click scikit-learn python-dateutil pandas lightgbm sortedcontainers
pip install dysgu
```

## **Step 11: Testing Software Outside Conda**
For system-wide installed tools, check version using:
```bash
samtools --version
bcftools --version
bedtools --version
bwa
minimap2 --version
```

## **Step 12: Manually Install IGV (Integrated Genomics Viewer)**
```bash
cd $HOME
wget https://data.broadinstitute.org/igv/projects/downloads/2.14/IGV_Linux_2.14.1_WithJava.zip
unzip IGV_Linux_2.14.1_WithJava.zip
rm IGV_Linux_2.14.1_WithJava.zip
```
### **Testing IGV**
```bash
cd $HOME/IGV_Linux_2.14.1/
./igv.sh
```

## **Step 13: Set Up a Jupyter Environment**
```bash
conda create -n jupyter jupyter=1.0.0 pandoc=2.12 -y
conda activate jupyter
pip install bash_kernel
python -m bash_kernel.install
conda deactivate
```

### **Test Jupyter Notebook**
```bash
conda activate jupyter
jupyter notebook --version  # Check if Jupyter is installed
jupyter notebook  # Start Jupyter Notebook server
```
This will open Jupyter Notebook in your web browser. If you see the Jupyter dashboard, the installation is successful.

Deactivate the environment:
```bash
conda deactivate
```

## **Step 14: Install LaTeX for Jupyter Notebook Support**
```bash
sudo apt-get install -y texlive-base texlive-xetex texlive-formats-extra texlive-fonts-extra texlive-luatex
```

## **Step 15: Ensure Conda Environment is Activated on Login**
```bash
echo "source $HOME/miniconda/etc/profile.d/conda.sh" >> ~/.bashrc
echo "conda activate ngsbio" >> ~/.bashrc
```

## **Step 16: Add IGV to System Path**
```bash
echo 'alias igv="igv.sh"' >> ~/.bashrc 
echo 'export PATH="$HOME/IGV_Linux_2.14.1:$PATH"' >> ~/.bashrc
```

## **Step 17: Install LibreOffice and other applications**
```bash
sudo apt-get install -y libreoffice
```
### **Testing LibreOffice**
```bash
libreoffice --version
```

In Firefox browser bookmark the following:
1. Course Github Repository
2. Learning and Management System (LMS) Login Page
3. Participant Access Google Drive


---

# NGS Software Table 
This table summarizes all installed software, their versions, official download links, and commands to verify installation. 

| Software               | Version  | Download Link                                           | Test Command            | Dependencies |
|------------------------|---------|--------------------------------------------------------|-------------------------|--------------|
| Samtools              | 1.15.1  | [Link](http://www.htslib.org/)                         | `samtools --version`    | None |
| Bcftools              | 1.15.1  | [Link](http://www.htslib.org/)                         | `bcftools --version`    | None |
| Bedtools              | 2.30.0  | [Link](https://bedtools.readthedocs.io/)               | `bedtools --version`    | None |
| OpenMPI               | 4.1.4   | [Link](https://www.open-mpi.org/)                      | `mpirun --version`      | None |
| R-base                | 4.0.5   | [Link](https://www.r-project.org/)                     | `R --version`           | None |
| Bowtie2               | 2.4.5   | [Link](http://bowtie-bio.sourceforge.net/bowtie2/)     | `bowtie2 --version`     | None |
| MACS2                 | 2.2.7.1 | [Link](https://github.com/macs3-project/MACS)          | `macs2 --version`       | Python, NumPy |
| MEME Suite            | 5.4.1   | [Link](http://meme-suite.org/)                         | `meme --version`        | Perl |
| UCSC BedGraphToBigWig | 377     | [Link](http://hgdownload.cse.ucsc.edu/)                | `ucsc-bedgraphtobigwig` | None |
| UCSC FetchChromSizes  | 377     | [Link](http://hgdownload.cse.ucsc.edu/)                | `ucsc-fetchchromsizes`  | None |
| R-sleuth              | 0.30.0  | [Link](https://github.com/pachterlab/sleuth)           | `R -e 'library(sleuth)'`| R, Bioconductor |
| Bioconductor-rhdf5    | 2.34.0  | [Link](https://bioconductor.org/packages/release/bioc/html/rhdf5.html) | `R -e 'library(rhdf5)'` | R, HDF5 |
| Bioconductor-rhdf5filters | 1.2.0 | [Link](https://bioconductor.org/packages/release/bioc/html/rhdf5filters.html) | `R -e 'library(rhdf5filters)'` | R, HDF5 |
| Bioconductor-rhdf5lib | 1.12.0  | [Link](https://bioconductor.org/packages/release/bioc/html/rhdf5lib.html) | `R -e 'library(rhdf5lib)'` | R, HDF5 |
| HDF5                  | 1.10.5  | [Link](https://www.hdfgroup.org/solutions/hdf5/)       | `h5cc -showconfig`      | None |
| Hisat2                | 2.2.1   | [Link](https://daehwankimlab.github.io/hisat2/)        | `hisat2 --version`      | None |
| Kallisto              | 0.46.2  | [Link](https://pachterlab.github.io/kallisto/)        | `kallisto version`      | None |
| BWA                   | 0.7.17  | [Link](http://bio-bwa.sourceforge.net/)                | `bwa`                   | None |
| Assembly-Stats        | 1.0.1   | [Link](https://github.com/sanger-pathogens/assembly-stats) | `assembly-stats`  | None |
| Canu                  | 2.2     | [Link](https://canu.readthedocs.io/)                   | `canu --version`        | Java, gnuplot |
| Kmer-Jellyfish        | 2.3.0   | [Link](https://github.com/gmarcais/Jellyfish)          | `jellyfish --version`   | None |
| Seqtk                 | 1.3     | [Link](https://github.com/lh3/seqtk)                   | `seqtk`                 | None |
| Velvet                | 1.2.10  | [Link](https://www.ebi.ac.uk/~zerbino/velvet/)         | `velveth --help`        | None |
| Wtdbg                 | 2.5     | [Link](https://github.com/ruanjue/wtdbg2)              | `wtdbg2`                | None |
| GenomeScope2          | 2.0     | [Link](http://qb.cshl.edu/genomescope/)                | N/A                     | R, Bioconductor |
| FreeBayes             | 0.9.21.7| [Link](https://github.com/ekg/freebayes)               | `freebayes --version`   | None |
| GATK4                 | 4.2.6.1 | [Link](https://gatk.broadinstitute.org/)               | `gatk --version`        | Java |
| Picard                | 2.27.4  | [Link](https://broadinstitute.github.io/picard/)       | `picard -h`             | Java |
| Minimap2              | 2.24    | [Link](https://github.com/lh3/minimap2)                | `minimap2 --version`    | None |
| Sniffles              | 2.0.7   | [Link](https://github.com/fritzsedlazeck/Sniffles)     | `sniffles -h`           | None |
| Dysgu                 | latest  | [Link](https://github.com/kcleal/dysgu)                | `dysgu --version`       | Python, scikit-learn |
| Breakdancer       | 1.4.5   | [Link](https://github.com/genome/breakdancer)          | `breakdancer-max -h`    | Perl, Samtools |
| IGV                   | 2.14.1  | [Link](https://software.broadinstitute.org/software/igv/) | `igv`               | Java |
| Jupyter Notebook      | 1.0.0   | [Link](https://jupyter.org/)                           | `jupyter --version`     | Python, IPython |
| LaTeX (for Jupyter)   | latest  | [Link](https://www.tug.org/texlive/)                   | `pdflatex --version`    | None |

---

# NGS Environment 

Bioinformatics Environments and Installed Software

| Environment Name   | Software                 | Version  |
|-------------------|-------------------------|---------|
| **ngsbio**        | Samtools                | 1.15.1  |
|                   | Bcftools                 | 1.15.1  |
|                   | Bedtools                 | 2.30.0  |
|                   | OpenMPI                  | 4.1.4   |
|                   | R-base                   | 4.0.5   |
|                   | Bowtie2                  | 2.4.5   |
|                   | MACS2                    | 2.2.7.1 |
|                   | MEME Suite               | 5.4.1   |
|                   | UCSC BedGraphToBigWig    | 377     |
|                   | UCSC FetchChromSizes     | 377     |
|                   | R-sleuth                 | 0.30.0  |
|                   | Bioconductor-rhdf5       | 2.34.0  |
|                   | Bioconductor-rhdf5filters| 1.2.0   |
|                   | Bioconductor-rhdf5lib    | 1.12.0  |
|                   | HDF5                     | 1.10.5  |
|                   | Hisat2                   | 2.2.1   |
|                   | Kallisto                 | 0.46.2  |
|                   | BWA                      | 0.7.17  |
|                   | Assembly-Stats           | 1.0.1   |
|                   | Canu                     | 2.2     |
|                   | Kmer-Jellyfish           | 2.3.0   |
|                   | Seqtk                    | 1.3     |
|                   | Velvet                   | 1.2.10  |
|                   | Wtdbg                    | 2.5     |
|                   | GenomeScope2             | 2.0     |
|                   | FreeBayes                | 0.9.21.7|
|                   | GATK4                    | 4.2.6.1 |
|                   | Picard                   | 2.27.4  |
|                   | Minimap2                 | 2.24    |
|                   | Sniffles                 | 2.0.7   |
|                   | Dysgu                    | latest  |
|                   | Breakdancer              | 1.4.5   |
| **chipseq-project**| R-ngsplot               | latest  |
|                   | Python                   | 2.7     |
| **jupyter**       | Jupyter Notebook         | 1.0.0   |
|                   | Pandoc                   | 2.12    |
| **system-wide**   | IGV                      | 2.14.1  |
|                   | LaTeX                    | latest  |

---

## Notes:
- **ngsbio**: The primary bioinformatics environment containing sequencing analysis tools.
- **chipseq-project**: Contains tools specific to **ChIP-seq analysis**.
- **jupyter**: Environment for running **Jupyter Notebooks**.
- **system-wide**: Software installed outside Conda (e.g., **IGV, LaTeX**).

---


