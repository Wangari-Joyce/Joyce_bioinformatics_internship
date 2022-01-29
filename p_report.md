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



## INTRODUCTION
Variant calling intuition
1. The starting point is the raw reads
2. Align the sequences to a reference genome,
3. Identify where the aligned reads differ from the reference genome

 ### A typical variant calling workflow
 





## Project achievements 
We managed to test the following pipelines during the project duration:
   - [nf-core/sarek](https://github.com/nf-core/sarek)
   - [CalliNGS-NF](https://github.com/CRG-CNAG/CalliNGS-NF)
   - [h3avarcall](https://github.com/h3abionet/h3avarcall)
   -  [nf-core/viralrecon](https://github.com/nf-core/viralrecon)
   -  [mbbu/variant-calling-pipeline](https://github.com/mbbu/variant-calling-pipeline)
   -   [variant-calling-pipeline-gatk4](https://github.com/gencorefacility/variant-calling-pipeline-gatk4)

## Project scope
We managed to provide a summary of the work we did on every pipeline on the basis of what we did and what we managede to achieve with each pipeline.
Below is a documentation of individual pipelines in accordance to our project objectives, providing detailed achievements for each and as well as recommendation for each.    


  ### [nf-core/sarek](https://github.com/nf-core/sarek)
  Pros | Cons
  -------------- | ------------------------
  Great effort put in the work by the team to provide detailed documentation on how to use the pipeline | There is however limited information on how to create the input  ```TSV``` file, we encountered an erro of lack of files in the directories provided and now errors with row formating
  The pipeline and many other pipelines work effortlessly with the test dataset | There is quite more to do to run the pipeline with your own dataset
  The pipeline was designed initially for Human and Mouse WGS data analysis, hence more inclined to analysing verterbrate sequence data | The default purpose  makes it tricky to use in analyzing invertebrate data, for our case pathogen and is=nsect data
  
  **NOTE:** ```nf-core pipelines involve some good work done to ensure ease of reproduction. This is supported by extensive documentation of the work and a big community connected via a slack channel where you can get most if not all of the possible errors with the pipeline attended to. Also, the pipeline is regularly maintained, thus you are sure everything is up to date.```    
  
  **WARNING:** ```The above note is based on the extensive reading and search we performed as far as the pipeline is concerned. However, we never got to run the pipeline on our dataset, not so much to report on the power, functionality among others.```
  
 [persistent error with sarek](https://github.com/mbbu/Assessing-Variant-Calling-Pipelines/blob/main/sarek%20persistent%20error.png)
  
---------------------------------------------------------
  
  
  [CalliNGS-NF](https://github.com/CRG-CNAG/CalliNGS-NF)     
  
  Pros | Cons 
  ------- | ----
  Works effortlessly with the test dataset, with expected output files | The pipeline however keeps throwing errors of ```incompatible contigs``` on multiple test daataset, that however runs well on other pipelines
  Designed for variant analysis of RNAseq data | Might not be a great choice for use with WGS data for that matter
  
  
  
  **NOTE:** ```Based on the initial purpose of the pipeline, we can hypothetically recommend use with RNAseq data rather than WGS data```
  
  **WANRNING:** ```We encountered errors trying to run the pipelien on our own dataset which is WGS data. We intended to compare the output varinat files with the successful pipelien, but due to the peristent error, we could not assertain its power. 
We intend to try it on an RNAseq data for better reporting.```

[CalliNGS persistent error](https://github.com/mbbu/Assessing-Variant-Calling-Pipelines/blob/main/CalliNGS%20error.png)
  
-----------------------------------------------------------------
  
 [h3avarcall](https://github.com/h3abionet/h3avarcall)    
 
 Pros | Cons 
 ------- | ----
 Great documentation with an additional tutorial for the working of the pipeline | The pipeline container is a huge one and requires a machine with higher power
 Designed for human WGS data for the analysis of variants | Default parameters are human data, hence requires modification
 
 
**NOTE:** ```We could not completely run the pipeline even on the test dataset, due to the huge computational power requirement of the image```

**WARNING:** ```Due to the huge computational rewuirement, we recommend running the work on a cluster```
              ```We are working on exploring more avenues for better computational power to test the pipeline in future.```
              
-----------------------------------------------------
              
 [nf-core/viralrecon](https://github.com/nf-core/viralrecon)    
 
 Pros | Cons 
 ----------- | --------------
 Designed initially for variant analysis of RNAseq data | In most cases it wll not work well for WGS data
 
 ------------------------
 
 
 [variant-calling-pipeline-gatk4](https://github.com/gencorefacility/variant-calling-pipeline-gatk4)    
 
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
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

 
  
