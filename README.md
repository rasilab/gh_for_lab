
# Template for Laboratory Research

## Getting Started

1. **Create a GitHub Account**  by visiting this [site]( [here](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github))

2. **Set Up Your Repository**  
   After verifying your email, return to this repository and click `Use this template` > `Create a new repository`.  
   - **Repository Name:** Choose a brief, descriptive name for your project, such as `opsin_evolution`.  
   - **Privacy Setting:** Select the `private` option to keep your repository secure.
  
2. **Edit files**
   You have multiple options:
   - Edit any file on the GitHub.com website by clicking the <img src="https://github.com/user-attachments/assets/2e2320f1-8102-436c-bb04-76d6a04b462d" width=20px/> icon in the page displaying the file.
   - You can use a cloud version of VScode to edit file in a more "editor"-like environment. To do this, substitute `github.com` by `github.dev` in the file URL keeping everything else the same.
   - You can also edit the file in any other text editor on your local computer. Instructions for using VScode locally are provided below. 

4. **Download Visual Studio Code**  
   Install [Visual Studio Code](https://code.visualstudio.com/download) on your computer.

5. **Sign In to GitHub in VS Code**  
   Open Visual Studio Code and log in with your GitHub account credentials.

6. **Install Git**  
   **For Mac Users:**  
   Open the terminal and run:

   ```bash
   xcode-select --install
   ```
   Verify the installation by running:

   ```bash
   git --version
   ```

7. **Clone Your Repository**  
   To import (clone) your repository to your local computer:  
   - Open the Command Palette in VS Code (Cmd+Shift+P on macOS or Ctrl+Shift+P on Windows/Linux).  
   - Type "Git: Clone" and select it.  
   - Paste your repository URL and choose a local directory for saving the project.
   - Refer to this [guide](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_clone-a-repository-locally) for help.

8. **Track Changes and Synchronize Repositories**  
   Use the Source Control panel in VS Code (Ctrl+Shift+G) to manage changes. A detailed step-by-step guide is available [here](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_staging-and-committing-code-changes)

## How to use this template

- In each project's repository, open an Issue to discuss ideas, experiments, analyses, or literature.
  - Create or edit Issue templates (e.g. for Literature, Ideas, Experiments, Analyses) to streamline this process.
  - Find a step-by-step guide [here](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue)
- Experiments, Analyses, Grants, Presentations, and Manuscripts go into separate folders.
- Each project contributor creates a sub-folder within the above folders to store their work.
- Do not store data files in the repository. Instead, create symbolic links from where the data is stored (e.g. server or cloud-based storage) so it can be easily accessed in the future.
- The described structure allows all users to be able push to the ```main``` branch without introducing merge conflicts, so we do not generally find added benefit in using branches.

### Experiments

```
experiments
    |--LABMEMBER_A
        |--ISSUENUMBER_1_lab_notebook_ngs_short_desc.md
    |--LABMEMBER_B
        |--ISSUENUMBER_2_lab_notebook_flow_short_desc.md
```

### Analysis

```
analysis
    |--LABMEMBER_A
        |--ANALYSIS_TYPE (eg. NGS)
            |--ISSUENUMBER_1_short_desc
                |--data 
                    |--data_type_1 (eg. genome)
                        |--chromosome.fasta
                    |--data_type_2 (eg. sra)
                        |--SRRnnnnnn.fastq
                |--scripts
                    |--analyze_in_R_python.ipynb
                    |--snakemake_workflow.smk
                    |--download_data_from_remote_folder.sh
                |--annotations 
                    |--sample_metadata.csv
                |--tables
                    |--processed_summary_table.csv
                |--figures
                    |--summary_fig.png
    |--LABMEMBER_B
        |--ANALYSIS_TYPE (eg. flow)
            |--ISSUENUMBER_2_short_desc
                |--data 
                    |--data_type_1 (eg. facs)
                        |--sample_1.fcs
                        |--sample_2.fcs
                |--scripts
                    |--analyze_in_R_python.ipynb
                |--annotations 
                    |--sample_metadata.csv
                |--tables
                    |--processed_summary_table.csv
                |--figures
                    |--summary_fig.png
```

### Manuscripts

```
manuscripts
    |--LABMEMBER_A
        |--manuscript_short_name
            |--maintext
                |--maintext.md
                |--bibliography.yaml
                |--latex_template.tex
                |--bibliography_style.csl
                |--svg
                    |--figure_1.svg
                    |--figure_2.svg
            |--cover_letter
                |--cover_letter.md
                |--latex_template.tex
```


### Grants & Fellowships

```
grants
    |--LABMEMBER_A
        |--YYYY_grant_short_name
            |--research_proposal.md
            |--bibliography.yaml
            |--latex_template.tex
            |--bibliography_style.csl
            |--svg
                |--figure_1.svg
                |--figure_2.svg
            |--project_abstract.md
            |--budget_justification.md
```

### Presentations

```
presentations
    |--LABMEMBER_A
    |--USER
        |--YYYYMMDD_presentation_short_desc
            |--presentation.md
            |--html_style.css
            |--svg
                |--figure-1.svg
                |--figure-2.svg
```

## Software Installation

- Install [Docker](https://docs.docker.com/engine/install/) and [VSCode](https://code.visualstudio.com/download).
- In VSCode, install the [Remote Tunnels](https://code.visualstudio.com/docs/remote/tunnels) extension.
- Use Docker to pull the containers necessary for your analyses. Commonly used containers from our registry include:
  - [R](https://github.com/rasilab/r/pkgs/container/r)
  - [Python](https://github.com/rasilab/python/pkgs/container/python)
  - [R and Python](https://github.com/rasilab/r_python/pkgs/container/r_python)
  - [Pandoc-latex](https://github.com/rasilab/pandoc-latex/pkgs/container/pandoc-latex)
- To start a container from the command line on your computer, do:

```bash
docker pull ghcr.io/rasilab/pandoc-latex:1.3.0
docker run -i -d --name pandoc-latex -v $HOME:$HOME ghcr.io/rasilab/pandoc-latex:1.3.0
```

- You can also use any of the above containers from within VSCode. For example, we commonly use the [R and Python](https://github.com/rasilab/r_python/pkgs/container/r_python) container for interactive analyses (e.g. Jupyter notebooks) in VSCode from our institution's cluster. See instructions [here](https://github.com/rasilab/r_python/pkgs/container/r_python#how-to-use-the-singularity-container-for-interactive-data-analysis-in-r-and-python) for how to set this up.

## Presentations

- Write your presentations as markdown files following the template [here](https://github.com/rasilab/github_demo/blob/main/presentations/kchen/20241214_thesis_defense/presentation.md).
- Use [vscode-reveal](https://marketplace.visualstudio.com/items?itemName=evilz.vscode-reveal) extension to open or export the markdown file as a reveal.js presentation.

