# Nextflow Tutorial

<img src="https://github.com/nextflow-io/trademark/blob/master/nextflow2014_no-bg.png">


Tutorial for INCLUDE Workshop, on 23 March 2022, covering Nextflow, containers and CAVATICA

In this tutorial you will learn:
- [Nextflow](https://www.nextflow.io/) - how to build parallelisable & scalable computational pipelines

## Contents

- [Session 1: Nextflow](#session-1-nextflow)
    - [a) Installation](#a-installation)
    - [b) Parameters](#b-parameters)
    - [c) Processes (inputs, outputs & scripts)](#c-processes-inputs-outputs--scripts)
    - [d) Channels](#d-channels)
    - [e) Operators](#e-operators)
    - [f) Configuration](f-configuration)
    
## Setup

We are going to use [Google Shell Cloud] to walk through the building of a Nextflow script and in the next session building the containers we used to do so.

### Logging into [Google shell Cloud](https://shell.cloud.google.com/)

[Google shell cloud](https://shell.cloud.google.com/) is an ephemeral machine, but has a number of items installed that makes it easier for us to go through this exercise.

* `Docker` is installed

* `Nextflow` can be installed

In the last session we went through some basic command line skills and there are links in the course material for you to be able to go back and review.

Let's begin:  In your web browser (Chrome preferred) - navigate to (https://shell.cloud.google.com)



```bash
git clone https://github.com/adeslatt/Elements-of-Style-Workflow-Creation-Maintenance.git
cd Elements-of-Style-Workflow-Creation-Maintenance
```

## Session 1: Nextflow

<img src="https://github.com/nextflow-io/trademark/blob/master/nextflow2014_no-bg.png" width=500 align="left">


**Main outcome:** *During the first session you will build a [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/) & [MultiQC](https://multiqc.info/) pipeline to learn the basics of Nextflow including:*
- [Parameters](https://www.nextflow.io/docs/latest/getstarted.html?highlight=parameters#pipeline-parameters)
- [Processes](https://www.nextflow.io/docs/latest/process.html) (inputs, outputs & scripts)
- [Channels](https://www.nextflow.io/docs/latest/channel.html)
- [Operators](https://www.nextflow.io/docs/latest/operator.html)
- [Configuration](https://www.nextflow.io/docs/latest/config.html)


### a) Installation

Within the Google Cloud Shell we have all but Nextflow available to us.

Conda is installed so we can use the conda install process to install nextflow

```bash
conda install -c bioconda nextflow
```

### b) Parameters

Now that we have Nextflow & Docker installed we're ready to run our first script

Normally, you begin by creating a file, for our lesson we are going to use a file that has already been created on your behalf.   We will go through this file and understand its content.

But in general these files are edited with your favorite your favourite code/text editor eg VSCode or vim or emacs

Inspect the file `main.step1.nf`

Typing 

```bash
less main.step1.nf
```

You see the contents of the file is as follows:
```nextflow
// main.step1.nf
params.reads = false

println "My reads: ${params.reads}"
```

The first line initialises a new variable (`params.reads`) & sets it to `false`
The second line prints the value of this variable on execution of the pipeline.

We can now run this script & set the value of `params.reads` to one of our FASTQ files in the testdata folder with the following command:
```bash
nextflow run main.step1.nf --reads testdata/test.20k_reads_1.fastq.gz
```

The run returns the name of our file.

#### Recap
Here we learnt how to define parameters & pass command line arguments to them in Nextflow

### c) Processes (inputs, outputs & scripts)

Nextflow allows the execution of any command or user script by using a `process` definition. 

A process is defined by providing three main declarations: 
the process [inputs](https://www.nextflow.io/docs/latest/process.html#inputs), 
the process [outputs](https://www.nextflow.io/docs/latest/process.html#outputs)
and finally the command [script](https://www.nextflow.io/docs/latest/process.html#script).

In our main script we want to add the following:
```nextflow
//main.step2.nf
reads = file(params.reads)

process fastqc {

    publishDir "results", mode: 'copy'

    input:
    file(reads) from reads

    output:
    file "*_fastqc.{zip,html}" into fastqc_results

    script:
    """
    fastqc $reads
    """
}
```

This file is also in our repository and we can inspect it from the command line

```bash
less main.step2.nf
```

Here we created the variable `reads` which is a `file` from the command line input.

We can then create the process `fastqc` including:
 - the [directive](https://www.nextflow.io/docs/latest/process.html#directives) `publishDir` to specify which folder to copy the output files to 
 - the [inputs](https://www.nextflow.io/docs/latest/process.html#inputs) where we declare a `file` `reads` from our variable `reads`
 - the [output](https://www.nextflow.io/docs/latest/process.html#outputs) which is anything ending in `_fastqc.zip` or `_fastqc.html` which will go into a `fastqc_results` channel
 - the [script](https://www.nextflow.io/docs/latest/process.html#script) where we are running the `fastqc` command on our `reads` variable

We can then run our script with the following command:
```bash
nextflow run main.step2.nf --reads testdata/test.20k_reads_1.fastq.gz -with-docker pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0
```

We are using the image I had pushed to the Seven Bridges Image repository -- in the next session I will walk through how that is done.

By running Nextflow using the `with-docker` flag we can specify a Docker container to execute this command in. This is beneficial because it means we do not need to have `fastqc` installed locally on our laptop. We just need to specify a Docker container that has `fastqc` installed.


### d) Channels

Channels are the preferred method of transferring data in Nextflow & can connect two processes or operators.

<!--
There are two types of channels:
1. [Queue channels](https://www.nextflow.io/docs/latest/channel.html#queue-channel) can be used to connect two processes or operators. They are usually produced from factory methods such as [`from`](https://www.nextflow.io/docs/latest/channel.html#from)/[`fromPath`](https://www.nextflow.io/docs/latest/channel.html#frompath) or by chaining it with methods such as [`map`](https://www.nextflow.io/docs/latest/operator.html#operator-map). **Queue channels are consumed upon being read.**
2. [Value channels](https://www.nextflow.io/docs/latest/channel.html#value-channel) a.k.a. singleton channel are bound to a single value and can be read unlimited times without consuming there content. Value channels are produced by the value factory method or by operators returning a single value, such us first, last, collect, count, min, max, reduce, sum.
-->

Here we will use the method [`fromFilePairs`](https://www.nextflow.io/docs/latest/channel.html#fromfilepairs) to create a channel to load paired-end FASTQ data, rather than just a single FASTQ file.

To do this we will replace the code from [1c](https://github.com/lifebit-ai/jax-tutorial/blob/master/README.md#c-processes-inputs-outputs--scripts) with the following 

```nextflow
//main.nf
reads = Channel.fromFilePairs(params.reads, size: 2)

process fastqc {

    tag "$name"
    publishDir "results", mode: 'copy'
    container 'pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0'

    input:
    set val(name), file(reads) from reads

    output:
    file "*_fastqc.{zip,html}" into fastqc_results

    script:
    """
    fastqc $reads
    """
}
```

The `reads` variable is now equal to a channel which contains the reads prefix & paired-end FASTQ data. Therefore, the input declaration has also changed to reflect this by declaring the value `name`. This `name` can be used as a tag for when the pipeline is run. Also, as we are now declaring two inputs the `set` keyword has to be used. Finally, we can specify the container name within the processes as a directive.

To run the pipeline:
```bash
nextflow run main.nf --reads "testdata/test.20k_reads_{1,2}.fastq.gz" -with-docker pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0
```

#### Recap
Here we learnt how use to the [`fromFilePairs`](https://www.nextflow.io/docs/latest/channel.html#fromfilepairs) method to generate a channel for our input data.

### e) Operators

Operators are methods that allow you to manipulate & connect channels.

Here we will add a new process `multiqc` & use the [`.collect()`](https://www.nextflow.io/docs/latest/operator.html#collect) operator

Add the following process after `fastqc`:
```nextflow
//main.nf
reads = Channel.fromFilePairs(params.reads, size: 2)

process fastqc {

    tag "$name"
    publishDir "results", mode: 'copy'
    container 'pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0'

    input:
    set val(name), file(reads) from reads

    output:
    file "*_fastqc.{zip,html}" into fastqc_results

    script:
    """
    fastqc $reads
    """
}
process multiqc {

    publishDir "results", mode: 'copy'
    container 'pgc-images.sbgenomics.com/deslattesmaysa2/multiqc:v1.0'

    input:
    file ('fastqc/*') from fastqc_results.collect()

    output:
    file "*multiqc_report.html" into multiqc_report
    file "*_data"

    script:
    """
    multiqc . -m fastqc
    """
}
```

Here we have added another process `multiqc`. We have used the `collect` operator here so that if `fastqc` ran for more than two pairs of files `multiqc` would collect all of the files & run only once.

The pipeline can be run with the following:
```bash
nextflow run main.nf --reads "testdata/test.20k_reads_{1,2}.fastq.gz" -with-docker pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0
```

#### Recap
Here we learnt how to use operators such as `collect` & connect processes via channels

### f) Configuration

Configuration, such as parameters, containers & resources eg memory can be set in `config` files such as [`nextflow.config`](https://www.nextflow.io/docs/latest/config.html#configuration-file).

For example our `nextflow.config` file might look like this:
```
docker.enabled = true
params.reads = false

process {
  cpus = 2
  memory = "2.GB"

  withName: fastqc {
    container = "pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0"
  }
  withName: multiqc {
    container = "pgc-images.sbgenomics.com/deslattesmaysa2/multiqc:v1.0"
  }
}
```

Here we have enabled docker by default, initialised parameters, set resources & containers. It is best practice to keep these in the `config` file so that they can more easily be set or removed. Containers & `params.reads` can then be removed from `main.nf`.

The pipeline can now be run with the following:
```bash
nextflow run main.nf --reads "testdata/test.20k_reads_{1,2}.fastq.gz"
```

#### Run a container in interactive mode using bash

Launching a BASH shell in the container allows you to operate in an interactive mode 
in the containerised operating system. For example: 

```
docker run -it pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0 bash 
``` 

Once the container is launched you will notice that's running as root (!). 
Use the usual commands to navigate in the file system.

To exit from the container, stop the BASH session with the `exit` command.

#### Run a container in interactive mode mounting local directory

One can run a container also from the command line - mounting the current directory.

Mounting means that we are making the directory we are in available to the container.

To do this we can do as follows - first define an environment variable for convenience

```bash
PWD=$(pwd)
echo $PWD
``` 
Next we will run in an interactive mode but mounting our directory

```bash
docker run -it -v $PWD:$PWD -w $PWD pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0 fastqc -h
```

## Return to the Agenda

[Main Agenda](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance#readme)
