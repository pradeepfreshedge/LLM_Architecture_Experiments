# Building a Task-Specific Small Language Model (SLM) from Scratch

This repository contains the implementation, experiment logs, and
supporting materials for the **Build LLM from Scratch Research
Assignment**.

The project trains a small GPT-style language model on a text dataset
from Project Gutenberg and studies how selected training and
architecture choices affect training and validation loss.

## Project objectives

-   Implement and train a small language model from scratch.
-   Observe training and validation loss during training.
-   Investigate the effect of learning rate and training duration.
-   Compare model configurations with different numbers of transformer
    layers.
-   Compare model configurations with different numbers of attention
    heads.
-   Run ablation experiments and analyze their results.

## Repository structure

``` text
LLMResearchAssignment/
├── .github/
├── notebooks/
│   └── LLM_Research_Assessment_Reference_Code_Extended_Proj_Gutenberg.ipynb
├── results/
│   ├── baseline_history.csv
│   ├── experiment1_lr_1e-3_temp.csv
│   ├── experiment1_lr_1e-4_final.csv
│   ├── experiment1_lr_1e-4_temp.csv
│   ├── experiment1_lr_epochs.csv
│   ├── experiment2_depth.csv
│   ├── experiment3_heads.csv
│   └── experiment4_ablations.csv
├── reports/
│   ├── research_assessment_report.pdf
│   └── loss-plot.pdf
├── data/
│   └── Project_Gutenberg_10_New_Releases.txt
├── scripts/
│   ├── build_research_report.py
│   └── build_word_report.py
├── README.md
└── requirements.txt
```

The directory names above are a suggested organization. If the files are
kept in the repository root, update the paths in this README
accordingly. Temporary CSV files may be retained for reproducibility,
but the final CSV files should be clearly identified.

## Dataset

The experiments use the text file:

`Project_Gutenberg_10_New_Releases.txt`

The dataset is associated with Project Gutenberg. Include the exact
source URL, access date, any applicable license or usage notes, and the
preprocessing steps in the final report. The dataset file is not
required to be committed to GitHub if its size or redistribution terms
make that unsuitable; provide instructions for obtaining it instead.

## Experiments

The experiment logs in this repository cover the following areas:

  -----------------------------------------------------------------------------
  Experiment              Variable investigated   Results file
  ----------------------- ----------------------- -----------------------------
  Experiment 1            Learning rate and       `experiment1_lr_epochs.csv`
                          training epochs         and other learning-rate CSV
                                                  files

  Experiment 2            Number of transformer   `experiment2_depth.csv`
                          layers (model depth)    

  Experiment 3            Number of attention     `experiment3_heads.csv`
                          heads                   

  Experiment 4            Ablation configurations `experiment4_ablations.csv`
  -----------------------------------------------------------------------------

### Selected observations from the recorded runs

**Model depth:** In the supplied five-epoch depth runs, the lowest
observed validation loss was **4.4227** for the **7-layer**
configuration at **epoch 5**.

**Attention heads:** In the supplied five-epoch head runs, the lowest
observed validation loss was **4.4621** for the **8-head** configuration
at **epoch 5**.

These are the best values observed in the supplied runs, not a claim
that they are globally optimal. The learning rate used for these
particular depth and head runs should be read from the
notebook/configuration; it is not specified in the corresponding console
logs.

Add the final learning-rate experiment and ablation findings here after
confirming them against the final CSV files and report.

## Environment setup

Python version and library versions should be aligned with the notebook
runtime. The following commands create an isolated environment and
install the listed dependencies.

### Windows

``` powershell
py -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### macOS / Linux

``` bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

For GPU training, install the PyTorch build compatible with the
machine's CUDA version using the official PyTorch installation selector:
https://pytorch.org/get-started/locally/

A `pip install -r requirements.txt` command does not guarantee GPU/CUDA
support. Verify the selected PyTorch build and hardware before starting
a long training run.

## Running the notebook

1.  Clone or download this repository.

2.  Install the dependencies.

3.  Place the dataset in the location expected by the notebook, or
    update the dataset path in the notebook.

4.  Open the notebook:

    ``` bash
    jupyter notebook
    ```

5.  Run the cells in order. If using Google Colab, upload or mount the
    dataset and update file paths for the Colab environment.

6.  Save the generated experiment CSV files and plots in the `results/`
    and `reports/` directories.

Training time and available accelerator hardware depend on the
environment. Set the random seed and record the hardware, batch size,
context length, optimizer, learning rate, and other relevant
hyperparameters when reporting results.

## Reproducibility and reporting

For each experiment, record:

-   The parameter being varied.
-   The values tested.
-   All fixed parameters.
-   Optimizer and learning rate.
-   Batch size, context length, and number of epochs.
-   Training and validation loss.
-   Hardware and software environment.
-   The checkpoint or configuration that produced the reported result.

The final report should explain the experimental method, show the
relevant result tables/plots, discuss observations, and state
limitations. Do not compare runs as if only one variable changed unless
all other relevant settings were held constant.

## Code and report

-   **Notebook:** contains the model implementation and experiment
    workflow.
-   **CSV files:** contain recorded training/validation metrics and
    experiment summaries.
-   **Report PDF:** contains the written methodology, results,
    discussion, and conclusions.

Add the final Overleaf-compiled PDF to `reports/` and include the public
GitHub repository URL in the report before submission.

## Large and generated files

Avoid committing the following unless there is a specific reason:

-   `.venv/` --- local Python environment.
-   `__pycache__/` and notebook checkpoint directories.
-   `model.pth` and `model_and_optimizer.pth` --- large model
    checkpoints (use a release or external storage if sharing is
    necessary).
-   Temporary or duplicate CSV files when a final result file is
    available.

A suitable `.gitignore` should exclude virtual environments, Python
cache files, notebook checkpoints, and large local checkpoints.

## Notes

This README describes the project based on the files and experiment
summaries currently identified. Before publishing, verify the notebook's
actual imports, Python version, dataset source and license, final
experiment results, and file paths. Update this document if the
repository layout differs from the suggested structure.
