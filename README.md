# ENA downloader tool

This tool downloads specific samples from ENA. For this, you can download the summary file from any ENA project or search result, from there, subset your target samples or add samples from other ENA summary file and use it to download all your samples with a simple command.

## Steps

Download this repo.

```
git clone https://github.com/AlejandroAb/ENA-downloader-tool.git
```
Add the Java CLASSPATH according to your download location:

```
export CLASSPATH=/your/download/location/FOA/build/classes
``` 

Display help mEnu

```
java foa.ENASync --help
```

```
#################################################################
###                     ENA Downloader                        ###
###                            v 1.0                          ###
###                                       @company       NIOZ ###
###                                       @author   A. Abdala ###
#################################################################
This program is created to download sequences from ENA archive.Usage:
        java foa.ENASync [options] -s <sumary_file> -o <output_directory>
Options:
        -s      --summary-file          File with the summary of the files to download. Final format TBD
        -o      --out                   Base directory to download the files
        --directory-per-project         It will download the files in one dedicated directory per project.
        --directory-per-sample          It will download the files in one dedicated directory per sample.
                                        If both "directory-per-XXXXX" flags are present, sample directory is created inside project directory
        --library-layout                Paires, Single.
        --library-source                Metagenome, genome, transcriptome, ...
        --library-selection             Random, PCR.
        --library-strategy              Amplicon.
        --filter-library-layout         Filter(exclude) data to download according to this value.
        --filter-library-source         Filter(exclude) data to download according to this value
        --filter-library-selection      Filter(exclude) data to download according to this value
        --filter-library-strategy       Filter(exclude) data to download according to this value
        --data-type                     Raw, functional annotation, taxonomy counts.
        --description                   Description to be applied to the datasets to be download.
        -v      --verbose               Output details during processing
```

Summary file example

|study_accession| sample_accession|experiment_accession|run_accession|tax_id|scientific_name| fastq_ftp |submitted_ftp|sra_ftp|
|---------------|-----------------|--------------------|-------------|------|---------------|----------|-------------|-------|
|PRJNA377530    |SAMN06480931    |SRX2614016  |    SRR5314314  |    1670606 | fungus metagenome |      ftp.sra.ebi.ac.uk/vol1/fastq/SRR531/004/SRR5314314/SRR5314314_1.fastq.gz;ftp.sra.ebi.ac.uk/vol1/fastq/SRR531/004/SRR5314314/SRR5314314_2.fastq.gz | |              ftp.sra.ebi.ac.uk/vol1/srr/SRR531/004/SRR5314314 |
|PRJNA377530 |    SAMN06480930 |  SRX2614017 |    SRR5314315  |   1670606 |fungus metagenome|       ftp.sra.ebi.ac.uk/vol1/fastq/SRR531/005/SRR5314315/SRR5314315_1.fastq.gz;ftp.sra.ebi.ac.uk/vol1/fastq/SRR531/005/SRR5314315/SRR5314315_2.fastq.gz| |               ftp.sra.ebi.ac.uk/vol1/srr/SRR531/005/SRR5314315|

Download fastq files into rawdata directory

```
java foa.ENASync -s PEMA_samples.tsv -o rawdata/
``` 
