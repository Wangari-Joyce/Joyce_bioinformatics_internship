## ASSESSING VARIANT CALLING PIPELINES FINAL REPORT


## ABSTRACT
Variant calling entails the process of identifying single nucleotide polymorphisms (SNPs) and small insertions and deletion (indels) from next generation sequencing data.

The aim of this mini-project was to assess existing variant calling pipelines, identify great ones and extend the workflows where there are gaps, inorder  to make them useful in insect and pathogen data.

We tested six variant calling pipelines three successfully ran with the test data provided two did not have test data, one didnot run on the hpc, Out of the five, only one ran with our test data which we successfully automated and extended where there were gaps.

Here we present the report of the pipelines we tested and the modifications of the [pipeline](https://github.com/mbbu/variant-calling-pipeline/blob/main/GATK/README.md), 
that we modified and successfully ran with Ecoli and Trypanasome data


## Objectives of the project
1. To evaluate the pipelines using the following criteria:
  - The ease of setup and use
  - Availability of proper documentation and tutorials for running the pipelines
  - The ease and speed of scalability to cloud based on computational requirements
  - Whether the pipeline allows for analysis of diverse sequence datasets e.g insect and/or pathogen data
  - Whether the pipeline is implemented latest versions of tools, for example the latest DSL 2 versions of Nextflow workflow language
  - Whether they are regularly maintained and updated.
2. To identify great pipelines, extend where there are gaps, make them useful for insect and pathogen data. 



## Introduction
Variant calling intuition
1. The starting point is the raw reads
2. Align the sequences to a reference genome
3. Identify where the aligned reads differ from the reference genome
4. Filter and annotate the variants

 ### A typical variant calling workflow
 
 ![workflow](https://github.com/mbbu/Assessing-Variant-Calling-Pipelines/blob/main/typical-workflow.png?raw=true)






## Variant calling pipelines
We tested the following pipelines:
   - [nf-core/sarek](https://github.com/nf-core/sarek)
   - [CalliNGS-NF](https://github.com/CRG-CNAG/CalliNGS-NF)
   - [h3avarcall](https://github.com/h3abionet/h3avarcall)
   -  [nf-core/viralrecon](https://github.com/nf-core/viralrecon)
   -  [nf-core/rnavar](https://github.com/nf-core/rnavar)
   -  [nf-core/vipr](https://github.com/nf-core/vipr)
   -  [variant-calling-pipeline-gatk4](https://github.com/gencorefacility/variant-calling-pipeline-gatk4)
   -  [mbbu/variant-calling-pipeline](https://github.com/mbbu/variant-calling-pipeline)





## Methodology for assessing the pipelines
![methodology](https://github.com/mbbu/Assessing-Variant-Calling-Pipelines/blob/main/methodology.png?raw=true)






## Results   


  ### [nf-core/sarek](https://github.com/nf-core/sarek)
  
 - Sarek is a workflow designed to detect germline or somaticvariants on whole genome or targeted sequencing data.
 
 - It was initially designed for Human, and Mouse.
 - It can work on any species with a reference genome. 
 - Sarek can also handle tumour / normal pairs and could include additional relapses.
  
  ### Summary
Pipeline | ease of use with test data | type of data | initially designed for |fast and easily scalable | use with variety of data | Dsl2 version | use of containers docker and singularity | regularly maintained and updated | scalable to the cloud |ease of use and following documentation| type of variants detected| 
  ----- | ----- | ----- | ----- | ----- | ----- |  ----- | ----- | ----- | ----- | ----- | ----- |
  NF-CORE SAREK | easy  |  WGS   | human and mouse |  _  | pipeline didnot work with our test data|  no    |   yes  |  yes  |  yes  |   hard  |  somatic and germline  |
  
  
 
 
  
  
 ### [CalliNGS-NF](https://github.com/CRG-CNAG/CalliNGS-NF) 
  
- This is a Nextflow pipeline for Variant Calling Analysis with NGS RNA-Seq data based on GATK best practices
  
- The RNA sequencing (RNA-seq) data, in additional to the expression information, can be used to obtain somatic variants present in the genes of the analysed organism
- The CalliNGS-NF pipeline processes RNAseq data to obtain small variants(SNVs), single polymorphisms (SNPs) and small INDELs (insertions, deletions)

- The pipeline is an implementation of the GATK best practices for variant calling on RNAseq

- This pipeline was easy to use and the documentation was short and easy to follow

- Due to the limited time we didnot test RNA-seq pipelines

- We recommend this pipeline for further analysis with RNA-seq data



### Summary 
Pipeline | ease of use with test data | type of input data | initially designed for |fast and easily scalable | use with variety of data | Dsl2 version | use of containers docker and singularity | regularly maintained and updated | scalable to the cloud |ease of use and following documentation| type of variants detected| 
  ----- | ----- | ----- | ----- | ----- | ----- |  ----- | ----- | ----- | ----- | ----- | ----- |
   CalliNGS-NF| easy  |   RNA-seq  | human |  _  | pipeline was not compatible with our test data |  yes   |   yes  |  yes  |  yes  |   easy  |  somatic  |
   
   


 ### [h3avarcall](https://github.com/h3abionet/h3avarcall)
 - This is a nextflow pipeline designed for Variant calling in human whole genome/exome sequencing data
 -  it detects SNPs and Indels giving raw sequence reads (fastq files) as input
 - This pipeline provides the best documentation which explains each step of variant calling and its importance
 - We recommend [this pipelines's documentation](https://h3abionet.github.io/H3ABionet-SOPs/Variant-Calling) to understand variant calling steps
 - This pipeline is resource intensive it requires 50GB memory 24 cpus to run the test data provided
 - This pipeline could not pull the containers required to run it in the hpc
 - We did not run this pipeline with our test data

### Summary
Pipeline | ease of use with test data | type of data | initially designed for |fast and easily scalable | use with variety of data | Dsl2 version | use of containers docker and singularity | regularly maintained and updated | scalable to the cloud |ease of use and following documentation| type of variants detected| 
  ----- | ----- | ----- | ----- | ----- | ----- |  ----- | ----- | ----- | ----- | ----- | ----- |
 h3avarcall | -  |  WGS /Exome sequencing data  | human |  _  | we didnot test it with our test data | no    |   yes |  no  |  no |  easy|germline  |
  

 
 
              
 ### [nf-core/viralrecon](https://github.com/nf-core/viralrecon) 
 - nf-core/viralrecon is a bioinformatics analysis pipeline used to perform assembly and intra-host/low-frequency variant calling for viral samples.
 - The pipeline supports both Illumina and Nanopore sequencing data.
 - This pipeline was specifically designed to analyze covid data
 - We recommend further testing of this pipeline with covid data 
 - Documentation was not easy to follow and comprehend
 
 ### Summary 
Pipeline | ease of use with test data | type of input data | initially designed for |fast and easily scalable | use with variety of data | Dsl2 version | use of containers docker and singularity | regularly maintained and updated | scalable to the cloud |ease of use and following documentation| type of variants detected| 
  ----- | ----- | ----- | ----- | ----- | ----- |  ----- | ----- | ----- | ----- | ----- | ----- |
  nf-core/viralrecon | -  |  viral sequences | covid data|  _  | pipeline was not compatible with our test data |  -   |   yes  |  yes  |  yes  |   hard  | - |
  
  
  

### [nf-core/rnavar](https://github.com/nf-core/rnavar)
- nf-core/rnavar is a bioinformatics best-practice pipeline for RNA-Seq variant analysis.
- This pipeline is currently in development and does not yet have any stable releases
- For the above reason we did not test the pipeline




### [nf-core/vipr](https://github.com/nf-core/vipr)
- nf-core/vipr is a bioinformatics best-practice analysis pipeline for assembly and intrahost / low-frequency variant calling for viral samples.
- This pipeline is archived and no longer in use
- It has been replaced by nf-core/viralrecon



 

 ### [variant-calling-pipeline-gatk4](https://github.com/gencorefacility/variant-calling-pipeline-gatk4) 
 
 
 
 
 Pros | Cons   
 ----- | ------
 The pipeline was built initially for variant analysis of *Plasmodium falciparum* and *Plasmodium vivax* sequence data something we were really forward to finding | The pipeline however assumes a number os steps that are vital for NGS sequence data prior to any type of analysis
 Well documented and easy to follow through steps of running the script |  You fisrt need to have the docker image pulled to be able to run the pipenine. The pipeline also had a an error with the flag for running it using the docker image. The initial error is with invalid ```-with``` flag
 
 
 Rinning the pipeline;
  
      docker pull gencorefacility/variant-calling-pipeline-gatk4 \
      nextflow run gencorefacility/variant-calling-pipeline-gatk4 -with-docker gencorefacility/variant-calling-pipeline-gatk4 -with docker  
     
**WARNING:** Error running pipeline     
![invalid flag](https://github.com/mbbu/Assessing-Variant-Calling-Pipelines/blob/main/Files/invalid%20flag.png)    

 **Right script:** Run the pipeline using the following ```--with``` flag
 
      docker pull gencorefacility/variant-calling-pipeline-gatk4 \
      nextflow run gencorefacility/variant-calling-pipeline-gatk4 -with-docker gencorefacility/variant-calling-pipeline-gatk4 --with docker    
        
  
  **NOTE:** You will need to do the following important steps prior to running the pipeline with your dataset    
    - You will need to ```Index``` your reference genome prior to launching the pipeline
    - You will need to perform ```sequence quality check``` 
    - You will need to perform ```adapter trimming``` in case your reads have trailing sequence ```sequence adapters```
    
 **Persistent error:** We have not managed to figure out the following error with this pipeline
  ![gencore pipeline error](https://github.com/mbbu/Assessing-Variant-Calling-Pipelines/blob/main/gencore%20error.png) 
  
  
  [mbbu/variant-calling-pipeline](https://github.com/mbbu/variant-calling-pipeline)    
  
  **WARNING:** ```The following are some of the insights we managed to figure out with the pipeline and the effort we made to improve the pipeline```
  
  - This is the pipeline that we managed to runn to completion
  - We ran through a couple of errors that we put effort on to make sure the pipeline is fully automated
  - The initial error we encountered was with the process of ```Creating Sequence Dictionary``` 
  - The error was due to parameters that were defined fixed for a particular dataset 
  - We have as well added to the pipeline a test dataset that will be used to test the functionality of the pipeline
  - Also, we modified the pipeline so that the it would be used to run analysis on both organisms with and without a snpEff database
  - We built a docker image for containerising the pipeline workflow 
  - We additionally configured the pipeline to run on both docker and singularity profiles on any cluster 
  
  
  Pros | Cons 
  ------ | ------
  An easy to run pipeline | The pipeline was initially developed to analyse variants on Trypanosome WGS dataset 
  Clear pipeline documentation | Since the pipeline was developed to analyse Trypanosome WGS dataset, so most of the parameters were defined fixed to a particular dataset The pipeline was not configured to run with the docker profile, but you have to firt pull the docker image 
  
  
  ## MBBU PIPELINE MODIFICATION
  
  
  ## A summary report for all pipelines
  
  Pipeline | ease of use with test data | type of data | initially designed for |fast and easily scalable | use with variety of data | Dsl2 version | use of containers docker and singularity | regularly maintained and updated | scalable to the cloud | type of variants detected| 
  ----- | ----- | ----- | ----- | ----- | ----- |  ----- | ----- | ----- | ----- | ----- |
  NF-CORE SAREK | easy  |  WGS   | human and mouse   |
  CRG-CNAG/ CalliNGS-NF | easy   | RNA-SEQ | human
  NF-CORE/RNAVAR |  under development |   RNA-SEQ |  |  
  H3AVARCALL | resource intensive could not run on hpc| WGS  | human |
  NF-CORE /VIPR |  archived,not in use|
  NF-CORE /VIRAL RECON | easy |  | viral |     |     | yes |  Yes | yes |    |
  GENCOREFACILTY VARIANT CALLING PIPELINE | hard | WGS | pathogen |     |  |   no  | yes | no |  |
  MBBU VARIANT CALLING PIPELINE | easy | WGS | insect and pathogen |   | yes  | yes | yes | yes |   |
  
  
  

  
  
  ## DISCUSSION/LESSONS LEARNT
  
  
  ## CHALLENGES
  
  
  
  
  ## RECOMMENDATIONS
  - scaling of the mbbu pipeline to the cloud
  - Further testing the MBBU pipeline with a variety of insect and pathogen data
  - Further testing of [CalliNGS-NF](https://github.com/CRG-CNAG/CalliNGS-NF) with RNA-seq data
  -  Further testing of Sarek with eukaryotic data
  
  
  ## REFERENCES
1. [Best practices for evaluating single nucleotide variant calling method for microbial genomics Nathan D. Olson,1,* Steven P. Lund,2 Rebecca E. Colman,3 Jeffrey T. Foster,4,† Jason W. Sahl,3,4 James M. Schupp,3 Paul Keim,3,4 Jayne B. Morrow,1 Marc L. Salit,1,5 and Justin M. Zook1
](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4493402/)


2. [Best Practices for Benchmarking Germline Small Variant Calls in Human Genomes
Peter Krusche,1 Len Trigg,2 Paul C. Boutros,3 Christopher E. Mason,4 Francisco M. De La Vega,5 Benjamin L. Moore,1 Mar Gonzalez-Porta,1 Michael A. Eberle,6 Zivana Tezak,7 Samir Lababidi,8 Rebecca Truty,9 George Asimenos,10 Birgit Funke,11 Mark Fleharty,12 Brad A. Chapman,13 Marc Salit,14,* Justin M Zook,15,* and Global Alliance for Genomics and Health Benchmarking Team](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6699627/)
  

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

 
  
