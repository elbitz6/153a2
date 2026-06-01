# Setup Instructions

## 1. Install dependencies

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
pip install pretty_midi miditok music21 notebook nbformat nbconvert ipywidgets tqdm pandas matplotlib
```

> If you don't have a CUDA GPU, replace `cu128` with `cpu` in the PyTorch install URL.

## 2. Download datasets

### MAESTRO v3.0.0 (piano MIDI, ~57 MB)

Download the **MIDI only** zip from:
https://magenta.tensorflow.org/datasets/maestro#download

Direct link:
```
https://storage.googleapis.com/magentadata/datasets/maestro/v3.0.0/maestro-v3.0.0-midi.zip
```

Extract into the project root so the folder is named `maestro-v3.0.0/`:
```bash
unzip maestro-v3.0.0-midi.zip
```

Expected structure:
```
maestro-v3.0.0/
  maestro-v3.0.0.csv
  maestro-v3.0.0.json
  2004/
  2006/
  ...
  2018/
```

### Lakh MIDI Dataset — matched subset (~1.5 GB)

Download from:
http://hog.ee.columbia.edu/craffel/lmd/lmd_matched.tar.gz

Or via command line:
```bash
# Linux/Mac
wget http://hog.ee.columbia.edu/craffel/lmd/lmd_matched.tar.gz
tar -xzf lmd_matched.tar.gz

# Windows (PowerShell)
Invoke-WebRequest -Uri "http://hog.ee.columbia.edu/craffel/lmd/lmd_matched.tar.gz" -OutFile "lmd_matched.tar.gz"
tar -xzf lmd_matched.tar.gz
```

Expected structure:
```
lmd_matched/
  A/
  B/
  C/
  ...
```

## 3. Run the notebook

Open `music_generation.ipynb` in VS Code or Jupyter and run cells top to bottom.

- **Task 1 training** (~1–2 hours on a GPU)
- **Task 2 training** (~15–30 minutes on a GPU)
- The final demo cell generates `outputs/demo_piano_plus_drums.mid`

## Project structure

```
.
├── music_generation.ipynb   # Main notebook
├── SETUP.md                 # This file
├── .gitignore
├── maestro-v3.0.0/          # (not in repo — download above)
├── lmd_matched/             # (not in repo — download above)
└── outputs/
    ├── *.png                # Training curves and analysis plots
    ├── *.mid                # Generated MIDI files
    └── *.pt                 # Model weights (not in repo — retrain locally)
```
