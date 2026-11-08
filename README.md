# Building a Task-Specific Small Language Model (SLM) from Scratch

This project trains a small GPT-style language model on a Project Gutenberg
text collection and records experiments on training settings and model
architecture.

## Repository structure

```text
.
├── .github/       # Repository-specific Copilot instructions
├── dataset/       # Project Gutenberg training text
├── model/         # Saved model and model/optimizer checkpoints
├── notebooks/     # Model implementation and experiment workflow
├── reports/       # Research report and loss plot
├── results/       # Experiment metrics (CSV)
├── .gitattributes # Git LFS tracking rules for model checkpoints
├── .gitignore
├── README.md
└── requirements.txt
```

The checkpoints in `model/` are stored with Git LFS. Install [Git LFS](https://git-lfs.com/)
before cloning if you need to download the checkpoint contents. The local
`.venv/`, `.idea/`, Python caches, and notebook checkpoint folders are excluded
from version control.

## Dataset

The repository includes
`dataset/Project_Gutenberg_10_New_Releases.txt`. The notebook currently looks
for a copy named `Project_Gutenberg_10_New_Releases.txt` in the
`LLMResearchAssignment` folder in Google Drive. Confirm the dataset's source
URL, access date, and applicable usage terms before redistributing it or
finalizing the research report.

## Experiments and results

The committed CSV files in `results/` are:

- `baseline_history.csv`
- `experiment1_lr_epochs.csv`
- `experiment2_depth.csv`
- `experiment3_heads.csv`
- `experiment4_ablations.csv`

The notebook also defines outputs for learning-rate runs and intermediate
results that are not currently present in the repository. Treat only the
committed CSVs as available results.

In the supplied five-epoch runs, the lowest observed validation loss was
**4.4227** for the **7-layer** depth configuration at epoch 5, and **4.4621**
for the **8-head** configuration at epoch 5. These are observations from the
provided runs, not claims of globally optimal configurations.

## Environment setup

Create an isolated Python environment and install dependencies:

### Windows

```powershell
py -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

For GPU training, install the PyTorch build compatible with your CUDA setup
using the [official PyTorch selector](https://pytorch.org/get-started/locally/).
Installing `requirements.txt` alone does not guarantee GPU support.

## Running the notebook

The notebook currently targets **Google Colab**: it imports `google.colab`,
mounts Google Drive, and uses the fixed output directory
`/content/drive/My Drive/LLMResearchAssignment`. To run it as written:

1. Open the notebook in Google Colab.
2. Put `Project_Gutenberg_10_New_Releases.txt` in the `LLMResearchAssignment`
   folder in your Google Drive.
3. Run the cells in order. The notebook installs `tiktoken` in its second cell
   and saves generated files to the Drive output directory.

The local environment instructions above install the listed dependencies, but
do not make the notebook directly runnable outside Colab. For local execution,
adapt the Drive-mount cell and set the input/output paths to locations on your
machine first.

## Reports and reproducibility

`reports/` contains the research report in PDF and DOCX formats and the
`loss-plot.pdf` figure. Before submission, verify that the report describes
the exact committed data and runs, and records the dataset source, training
configuration, hardware, software environment, and any relevant limitations.
