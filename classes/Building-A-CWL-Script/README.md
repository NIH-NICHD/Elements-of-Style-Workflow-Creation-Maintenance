# Building A [Common Workflow Language (CWL) Workflow](https://www.commonwl.org/)

Here we now show how the same containers may be used in a CWL workflow.


## Showing the CWL workflow with the same containers

Navigate now to the proper directory for the lesson.

```bash
cd ~/Elements-of-Style-Workflow-Creation-Maintenance/classes/Building-A-CWL-Script
```

Looking at the directory we type the command:

```bash
ls -l
```

And now we see:

```bash
(eos) ad376@cloudshell:~/Elements-of-Style-Workflow-Creation-Maintenance/classes/Building-A-CWL-Script$ ls -l
total 12
drwxr-xr-x 2 ad376 ad376 4096 Mar 31 13:28 cwl_tools
-rw-r--r-- 1 ad376 ad376 1236 Mar 31 13:28 fastqc_multiqc_wf.cwl
-rw-r--r-- 1 ad376 ad376 3808 Mar 31 13:28 README.md
```

By convention, the bioinformaticians at `Childrens Hospital of Philadelphia` put their tools, their pieces for a workflow in a subdirectory they name `cwl_tools`.   This is a good convention.

We can see what is put in this directory by typing:

```bash
ls -l cwl_tools
```

We see that there are two files:

```bash
-rw-r--r-- 1 ad376 ad376 1053 Mar 31 13:28 fastqc.cwl
-rw-r--r-- 1 ad376 ad376 1004 Mar 31 13:28 multiqc.cwl
```

We can inspect that file either by opening it in an editor or by typing at the terminal
```bash
less cwl_tools/fastqc_cwl
```

Which we see now as:

```bash
cwlVersion: v1.0
class: CommandLineTool
id: fastqc
requirements:
  - class: ShellCommandRequirement
  - class: DockerRequirement
    dockerPull: 'pgc-images.sbgenomics.com/deslattesmaysa2/fastqc:v1.0'
  - class: InlineJavascriptRequirement
  - class: ResourceRequirement
    ramMin: ${ return inputs.ram * 1024 }
    coresMin: $(inputs.cores)

baseCommand: [mkdir]
arguments:
  - position: 1
    shellQuote: false
    valueFrom: >-
      $(inputs.outdir)
  - position: 2
    shellQuote: false
    valueFrom: >-
      && fastqc

inputs:
  input_reads: { type: 'File[]', inputBinding: {position: 99}, doc: "Input fastq files" }
  outdir: { type: 'string?', default: "results", inputBinding: { position: 2, prefix: "--outdir"} }
  noextract: { type: 'boolean?', default: true, inputBinding: { position: 2, prefix: "--noextract"} }
  cores: { type: 'int?', default: 2 , inputBinding: { position: 2,  prefix: "--threads" } }
  ram: { type: 'int?', default: 2 }
outputs:
  fastqc_results:
    type: Directory
    outputBinding:
      glob: $(inputs.outdir)
```

We see many of the same pieces.   While I will not go into detail, the point is that the `cwl` script is using the same containers as we did in the `nextflow` script.

We can also inspect the `multiqc.cwl` file in that way or in the editor.

### Installing cwltool

In the same way that we installed `nextflow`, we can install `cwltool`.


To run the pipeline:
```bash
conda install -c bioconda cwltool -y
```

### Executing with cwltool


## Return to the Agenda

[Main Agenda](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance#readme)
