# 🎵 Music Generation using Unsupervised Learning

> A deep learning project that generates music using unsupervised and generative models —
> LSTM Autoencoder, VAE, and Transformer — trained on MIDI data.

---

## 👥 Group Members & Contributions

| Name | Student ID | Contribution |
|------|------------|--------------|
| Parisa Rahman | 23101400 | Preprocessing, LSTM Autoencoder, VAE |
| Maahpara Masroor Melica | 24241247 | Baseline Models, Transformer model, Final Comparison |

---

## 📁 Project Structure

```
music-generation-unsupervised/
│
├── README.md                        # Project overview and documentation (this file)
├── requirements.txt                 # All Python dependencies
│
├── data/                            # Dataset stored on Google Drive (link below)
│
├── notebooks/
│   ├── CSE425_Project.ipynb         # Preprocessing + LSTM AE + VAE + Baseline
│   └── Transformer.ipynb            # Tokenization + Transformer model + Model Comparison
│
├── outputs/
│   ├── generated_midis/             # All model-generated MIDI files (see Drive link below)
│   └── plots/                       # All plots (see the Drive Link Below)
│
└── report/
    ├── final_report.tex             # LaTeX source for final report
```

---

## 🗂️ Notebook Descriptions

### `notebooks/CSE425_Project.ipynb`
This is the **main notebook**. It covers the full pipeline:
- Loads and parses raw MIDI files using `pretty_midi`
- Converts MIDI to **piano roll** representation (pitch × time matrix)
- Prepares train/test splits
- Implements and trains:
  - **LSTM Autoencoder** — compresses piano roll into latent space and reconstructs
  - **VAE (Variational Autoencoder)** — learns structured latent space for controllable generation
  - ** Baseline models** 
- Evaluates all models using Pitch Similarity, Rhythm Diversity, Repetition Ratio

### `notebooks/Transformer.ipynb`
This notebook handles **token-based** music generation:
- Loads raw MIDI files and converts events to **integer token sequences**
- Prepares sequential train/test data
- Implements and trains a **Transformer model** with self-attention
- Evaluates using Pitch Similarity, Rhythm Diversity, and Perplexity
- Evaluates All Models

---

## 🎧 Dataset & Generated MIDI Files

All data and generated MIDI outputs are stored on Google Drive:

https://drive.google.com/drive/folders/1NMcJaT_hW93N5Q8syrajja4aJJIJxfDy?usp=sharing

---

## 🚀 How to Run (Google Colab)

Both notebooks are designed to run on **Google Colab** — no local setup needed.

### Step 1: Open the notebook in Colab

- Go to [colab.research.google.com](https://colab.research.google.com)
- Click **File → Open Notebook → GitHub tab**
- Paste the repo URL: `https://github.com/yourusername/music-generation-unsupervised`
- Select either `CSE425_Project.ipynb` or `Transformer.ipynb`

> ⚠️ Replace `yourusername` with your actual GitHub username.

### Step 2: Mount Google Drive & load data

Run the Drive mount cell at the top of each notebook:

```python
from google.colab import drive
drive.mount('/content/drive')
```

Then update the `DATA_PATH` variable in the notebook to point to your MIDI folder in Drive.

### Step 3: Install dependencies

**For `CSE425_Project.ipynb`** — run the second cell:
```python
!pip install pretty_midi miditok music21
```

**For `Transformer.ipynb`** — run the first cell:
```python
!pip install pretty_midi -q
```

### Step 4: Run all cells

- Click **Runtime → Run All**
- The notebook will preprocess, train, evaluate, and generate MIDI files automatically
- Generated MIDIs will be saved to your Google Drive

---

## 📦 Requirements

All dependencies are installed inside the notebooks via `!pip install`. For local runs:

```bash
pip install -r requirements.txt
```

| Library | Purpose |
|---------|---------|
| `pretty_midi` | MIDI parsing and export |
| `miditok` | MIDI tokenization for Transformer |
| `torch` | PyTorch — all deep learning models |
| `numpy` | Numerical computation, piano roll arrays |
| `pandas` | Data handling and results tables |
| `matplotlib` | Plotting loss curves and piano rolls |
| `music21` | Music theory analysis |

---

## 📊 Results

### Final Model Comparison

| Model | Pitch Similarity ↑ | Rhythm Diversity ↑ | Repetition Ratio ↓ | Perplexity ↓ |
|-------|:-----------------:|:-----------------:|:-----------------:|:------------:|
| Random (baseline) | 0.2756 | 0.0150 | 0.0000 | — |
| Markov Chain | 0.2918 | 0.0750 | 0.0000 | — |
| LSTM Autoencoder | 0.0882 | 0.0659 | 0.0000 | — |
| VAE | **0.7369** | **0.5000** | 0.0000 | — |
| Transformer | 0.5183 | 0.3942 | 0.0014 | **1.1062** |

---
## Plots

All Plots are stored on Google Drive:

https://drive.google.com/drive/folders/1a7jL5_nY15QeaPTbBMLRYnP1vUH91dnv?usp=sharing

---

## 📝 Report

The final report is in `report/final_report.tex`

