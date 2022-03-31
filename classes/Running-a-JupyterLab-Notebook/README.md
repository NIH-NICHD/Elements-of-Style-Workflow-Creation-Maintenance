
<p>
<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/JupyterLabLogoWithName.png"  width="250">
</p>

# Example Volcano Plot in a JupyterLab Notebook on [CAVATICA](https://cavatica.sbgenomics.com)


## Log back in

Within your browser, navigate back to [CAVATICA](https://cavatica.sbgenomics.com) and log back in.

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICALoginWindowNumber1.png">

Authorize CAVATICA to act on your behalf.
<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICAGen3WindowNumber2.png">

Arrive at the CAVATICA window - we created a project and an analysis notebook already, you may have to select that project.

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICALoginDashboardNumber3.png" >

## Fork the GitHub Repository

We are going to fork the GitHub repository - to do so navigate in your browser to the repository for this course.

Click here [Elements of Style Workflow Creation and Maintenance](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance)

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GitHubElementsofStyleWorkflowForkClone1.png">

In the upper righthand side of the screen, select `Fork` and choose to `Fork` it into your own personal repository.

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GitHubElementsofStyleWorkflowForkClone2.png">

If you have already made a fork, it would make sense to fetch any upstream changes that may have occured since you last visted.  Your screen should look like this:

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GitHubElementsofStyleWorkflowForkClone3.png">

Next, navigate to the 🟦`Code` button on the right and select `HTTPS` and copy the link.

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GitHubElementsofStyleWorkflowForkClone4.png">

## Clone the repository in the Jupyterlab terminal window

Return to your CAVATICA Window and go back to your JupyterLab notebook.
And select the `terminal window`

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICAJupyterLabNotebookLauncher.png">

Now we want to clone the repository fork we made:

At the prompt type:

```bash
git clone https://github.com/adeslat/Elements-of-Style-Workflow-Creation-Maintenance
```

But, we might get an error.

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICAJupyterLabTerminalGitCloneError.png">

## Authenticating for GitHub in CAVATICA

Because of that, we need to authenticate to our GitHub within CAVATICA.

We need to install `GitHub Command Line Interface` - more on this in the next lesson but for now type in the terminal window.

```bash
conda install -c conda-forge gh -y
```

After completing, the installation looks like this:

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICAJupyterLabNotebookCondaInstallGH.png">

Now we need to authenticate.   We do this with our personal `GitHub Token`. 

### Generating A GitHub Authentication Token

[Generating your own GitHub Authentication Token](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/GeneratingGitHubPersonalAccessTokens.gif)

Once we have our token, we can now authenticate.

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICAJupyterLabGHAuthLoginWithToken.png">

## Clone our repository version

Now that we are authenticated, we can clone successfully.

```bash
git clone https://github.com/adeslat/Elements-of-Style-Workflow-Creation-Maintenance
```

And the result should look like this:

<img src="https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance/blob/main/assets/CAVATICAJupyterLabNotebookGitCloneSuccess.png">


## Useful Command Line Functions.


First we run the JupyterLab notebook which introduces us to some Command Line Functions that will be useful.

### Open the `1-using-the-command-line.ipynb`


Now follow the folder and select the first notebook in the directory, and we will execute all the command lines interactively.

`1-using-the-command-line.ipynb`

Note that this notebook had the `python` kernel running, normally we would have executed this in a `bash` kernel.  This Kernel is not yet available on the CAVATICA platform but soon will be.



## Open the `2-reading-data-and-plotting-in-R.ipynb`

Next, we will execute the second `jupyterlab` notebook, this one is running the `R` kernel.

Look again at the folders on the left and select the second notebook.

`2-reading-data-and-plotting-in-R.ipynb`

## Return to the Agenda

[Main Agenda](https://github.com/NIH-NICHD/Elements-of-Style-Workflow-Creation-Maintenance#readme)

## Additional resources:

- CAVATICA documentation for the JupyterLab interface: https://docs.cavatica.org/docs/editor-quick-reference
- Official documentation from project JupyterLab: https://jupyterlab.readthedocs.io/en/stable/ 
