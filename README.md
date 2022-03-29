<p>
<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/INCLUDEDataCoordinatingCenter.png"  width="250">
</p>

# Elements of Style Workflow Creation Maintenance 
#HI
## Creating an Account on CAVATICA

Please create your account on CAVATICA

Navigate to [CAVATICA](https://cavatica.sbgenomics.com)

First screen you will see:

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICACreateAnAccountNumber1.png">

You can either select `Create an account` or `Log in with eRA Commons`.

If you select `Create an account`, you will see:

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICACreateAnAccountNumber2.png">

Or if you select `Log in with eRACommons` you will see:

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICACreateAnAccountERACommonsNumber3.png">


See further documentation:
[CAVATICA Account Login Creation Documentation](https://docs.cavatica.org/docs/sign-up-for-cavatica)

## Lets Log in straight to CAVATICA

* [Log straight into CAVATICA Step-by-Step and Start a Notebook](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/LoggingIntoCAVATICA/README.md)

## Logging in From INCLUDE Data Hub

* [Log into INCLUDE Data Hub](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/LoggingIntoCAVATICAFromINCLUDEDataHub.gif)

* [Log into CAVATICA from INCLUDE Data Hub](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/LoggingInAfterEnteringINCLUDEDataHubWithORCID.gif). 

* [Start a DataCruncher Notebook](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/DataCruncherJupyterLabNotebook.gif)

While things start to cook -- let me review the Agenda and show a brief presentation

## Agenda for the day:
| Time (UTC)    | Programme       |
| ------------- | --------------------------------------------------------------------------- |
| 11.00 - 11.10 | *Welcome Address and Presentation of Tutorial Agenda* |
| 11.10 - 11.15 | 0. [A few simple rules for easier workflow maintenance and reuse](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/Elements-of-Style/A-Few-Simple-Rules-Shortened.md)<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/The_Elements_of_Programming_Style.jpg" width="100" align="right">|
| 11.15 - 11.30 | 1. [Example Volcano Plot on CAVATICA](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/Running-a-JupyterLab-Notebook)<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICALogo.png" width="100" align="right">|
| 11:30 - 12.00 | 2. [Stitching processes with a standard workflow - Nextflow](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/Building-A-Nextflow-Script/README.md)<img src="https://github.com/nextflow-io/trademark/blob/master/nextflow2014_no-bg.png" width="100" align="right"> |
| 12:00 - 12.30 | 3. [Dockerfile for each process - Docker](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/2-intro-to-conda-docker/2-build-test-share-dockerfiles-github.md) <img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/Moby-Logo.png" width="100" align="right">|
| 12.30 - 12.45 | :coffee:      *Short break - Stretch your legs! (15 minutes)*            :coffee:|
| 12:45 - 13.15 | 4. [Working with Apps on the INCLUDE DataHub](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/WorkingWithAppsOnCAVATICA/WorkingWithAppsOnCAVATICA.md)<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/INCLUDEDataCoordinatingCenter.png"  width="100" align="right">
| 13:15 - 13.30 | 5. [GitHub Actions to build, test and deposit container images](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/GitHubActions/GitHubActionsForMaintenanceTesting.md) <img src="https://github.com/ISCB-Academy/Elements-of-Style-Reproducible-Workflow-Creation-Maintenance-Tutorial/blob/main/assets/Octocat.png" width="100" align="right"> |
| 13.30 - 13.45 | 6. [Stitching processes with other workflow languages, such as Common Workflow Language](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/classes/NextflowSharedDataElements/NextflowCommonWorkFlowLanguageSharedStructureSharedElements.md) <img src="https://github.com/common-workflow-language/logo/blob/main/CWL-Logo-HD.png" width="100" align="right">|
| 13:30 - 13.35 | 5. [Zenodo for DOIs and Genomic Summary and other Data](https://github.com/sheynkman-lab/Long-Read-Proteogenomics/blob/main/README.md) <img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/Zenodo_logo.jpg" width="100" align="right">|
| 13.50 - 14.00 | *Closing remarks and future directions*|
<br/><br/>


## Background Information and other Topics of Interest
| <img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/NICHD_60Years_Innovation.png"  width="50">   |   |   |  |
|---|---|---|---|
| [Anaconda Package Jupytext](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/AnacondaPackageSearchJupytext.gif)| [CAVATICA Create Developer Token](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICACreateDeveloperAuthenticationToken.gif) | [CAVATICA Add samtools to Docker Repository](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICACreateDockerSamtoolsRepository.gif) | [Conda Create env and install GitHub CLI](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CondaEnvCreateEOSAndCondaInstallGitHubCLI.gif) |
| [CAVATICA DataCruncher JupyterLab Startup](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/DataCruncherJupyterLabNotebook.gif)|[Generate GitHub Personal Access Tokens](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GeneratingGitHubPersonalAccessTokens.gif)|[GitHub Auth Login](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GitHubAuthLoginFromCommandLine.gif) | [GitHub Clone FHIR Exercises](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GitHubCloneFHIRExercisesFromNICHD.gif) |
| [INCLUDE DataHub Login with ORCID](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/LoggingInAfterEnteringINCLUDEDataHubWithORCID.gif) | [CAVATICA Login](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/LoggingIntoCAVATICAFromINCLUDEDataHub.gif)| [GitHub Actions with STAR](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/MakingGitHubActionsWithStar-Docker.gif) | [Anaconda Search GitHub CLI](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/SearchAnacondaPackagesForGitHubCLI.gif) |
| [Shell Google Cloud](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/shellCloudGoogleCom.gif) | | | |

## About

In a short 3 hour course, the learner learned elements of style in the construction and containerization of small single-function processes that facilitate repurposable workflow creation and execution.  This hands-on-tutorial was given through a webinar with the to coincide with the launch of the [INCLUDE Data Hub](https://includedcc.org/).  This repository was used in the course and contains self-learnings to facilitate work.  In this repository, contains how these processes may be kept up-to-date and alert the creator to the functional state of these processes (working or failing) by using a feature found within GitHub called GitHub Actions.  This hands-on-course will use a small example to provide the structure, philosophy and approach to achieving this desirable outcome.  This course seeks to help to demystify and make accessible powerful methods one can use to achieve platform independence and platform interoperability.  Using a simple example to demonstrate these techniques, we will break down and walk the learner through each of the construction steps.  The learners will be introduced to Conda, Docker, GitHub and the standard workflow language, Nextflow.  If time permits, we will also show how these containerized processes can also be represented in a second standard workflow language implementation (e.g. Common Workflow Language or WDL). By the end of the course, the learner will understand these Elements of Style and will know how Conda, Docker, GitHub, Zenodo, and Nextflow enable repurposable research.  Moreover, these steps will be on GitHub for the Learner to return to and reproduce themselves after the end of the course.  In taking this course, the Learner will also be shown the power of JupyterLab notebooks to facilitate literate programming.  Through their participation in the class, learners will learn and understand FAIR (findability, accessibility, interoperability and reusability) best practices. We ask all participants to get a GitHub, Zenodo and ORCID accounts prior to the course.  We ask for minimal background knowledge of the command line, simple commands in the shell environment, we enable a bit of self-learning from the repository to facilitate the acquisition of this knowledge.   This work was powered on CAVATICA and [INCLUDE Data Portal](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/edit/main/README.md)
