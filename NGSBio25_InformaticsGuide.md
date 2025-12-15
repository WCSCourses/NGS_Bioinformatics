# <img src="https://coursesandconferences.wellcomeconnectingscience.org/wp-content/themes/wcc_courses_and_conferences/dist/assets/svg/logo.svg" width="300" height="50"> Add Course Title Informatics Guide

**Software used during the course**    

VM setup guide can be found here: [NGS Virtualbox Setup Guide](https://github.com/WCSCourses/NGS_Bioinformatics_2025/blob/main/NGS_VM_Guide.md)

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


## Informatics Set-Up
For installation and setup, please refer to the following guides:

- **[Oracle VM VirtualBox Installation Guide](https://github.com/WCSCourses/index/blob/main/VM_Guide.md)** – Detailed instructions for installing and configuring VirtualBox on different operating systems. *(Note: Separate installations are needed for Intel-based and ARM-based Macs, and the VDI files will differ.)*


The Host Operating System Requirements are: <br />
- RAM requirement: 8GB (preferably 12GB) <br />
- Processor requirement: 4 processors (preferably 8) <br />
- Hard disk space: 200GB <br />
- Admin rights to the computer <br />

## Citing and Reusing Course Material

The course data are free to reuse and adapt with appropriate attribution. All course data in these repositories are licensed under the <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/">Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)</a>. <a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /> 

Each course landing page is assigned a DOI via Zenodo, providing a stable and citable reference. These DOIs can be found on the respective course landing pages and can be included in CVs or research publications, offering a professional record of the course contributions.

## Interested in attending a course?

Take a look at what courses are coming up at [Wellcome Connecting Science Courses & Conference Website](https://coursesandconferences.wellcomeconnectingscience.org/our-events/).

---

[Wellcome Connecting Science GitHub Home Page](https://github.com/WCSCourses) 

For more information or queries, feel free to contact us via the [Wellcome Connecting Science website](https://coursesandconferences.wellcomeconnectingscience.org).<br /> 
Please find us on socials [Wellcome Connecting Science Linktr](https://linktr.ee/eventswcs)

---
