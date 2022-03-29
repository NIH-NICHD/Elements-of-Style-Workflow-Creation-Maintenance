# Building Dockerfiles

In this way we are running the command as if we had locally installed it -- which is great for debugging one process at a time.

- [Docker](https://www.docker.com/) - how to use Docker containers - which we will show in the next hour how to build


Docker images are created by using a so called `Dockerfile` i.e. a simple text file 
containing a list of commands to be executed to assemble and configure the image
with the software packages required.    

In this step, you will create a Docker image containing the FastQC & MultiQC tools.


Warning: the Docker build process automatically copies all files that are located in the 
current directory to the Docker daemon in order to create the image. This can take 
a lot of time when big/many files exist. For this reason, it's important to *always* work in 
a directory containing only the files you really need to include in your Docker image. 
Alternatively, you can use the `.dockerignore` file to select the path to exclude from the build. 

Then use your favourite editor eg. `vim` to create a file named `Dockerfile` and copy the 
following content: 

```Dockerfile
# Full contents of Dockerfile

FROM continuumio/miniconda3
LABEL description="Base docker image with conda and util libraries"
ARG ENV_NAME="fastqc"

# Install the conda environment
COPY environment.yml /
RUN conda env create --quiet --name ${ENV_NAME} --file /environment.yml && conda clean -a

# Add conda installation dir to PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/${ENV_NAME}/bin:$PATH
```

Notice that this Docker file uses a file called `environment.yml`. 

You can edit this file in an editor and make a file called `environment.yml` and make sure it is in the same directory

```environment.yml
name: fastqc
channels:
  - bioconda
  - defaults
dependencies:
  - fastqc
```
When done save the file. 

### c) Building images

Build the Docker image by using the following command: 

```bash
docker build -t fastqc .
```

Note: don't miss the dot in the above command. When it completes, verify that the image 
has been created listing all available images: 

```bash
docker images
```

#### Using existing containers from a repository

We will go into more detail in the next session

Navigate to the top of your home directory

```bash
cd ~
```

Clone the two containers

```bash
git clone https://github.com/adeslatt/fastqc-docker.git
```

and 

```bash
git clone https://github.com/adeslatt/multiqc-docker.git
```

#### Build the Fastq image

With the `Dockerfile` from above you might want to run:
```bash
cd fastqc-docker
docker build -t fastqc .
```

#### Build the multiqc image

Navigate now to multiqc

```bash
cd ../multiqc-docker
docker build -t multiqc .
```

#### Now look at the images we have available to us

what images are available 

```bash
docker images
```


#### Inspect what images you have now available to you

You can see what you have built -- and see that we have `tag`ged our files in a certain way

```bash
docker images
```

The containers can be used in our Nextflow pipeline replacing the two different containers we currently have because it has both `fastqc` & `multiqc` installed

