# Impact of Circuit Depth versus Qubit Count on Variational Quantum Classifiers (VQC)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1BvhjWAd0qxb4LU3bzZUXkT6XpY-c4LD3?usp=sharing)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Qiskit](https://img.shields.io/badge/Qiskit-0.46.0-6133BD)
![Status](https://img.shields.io/badge/Status-Research%20Completed-success)
![License](https://img.shields.io/badge/License-MIT-green)

**Author:** Fatih Maulana¹²  
¹ *School of Computing, Universiti Utara Malaysia* ² *Faculty of Science and Technology, UIN Sunan Gunung Djati Bandung*

---

## Project Overview

This repository contains the official source code for the research paper: **"Impact of Circuit Depth versus Qubit Count on Variational Quantum Classifiers for Higgs Boson Signal Detection"**.

This study benchmarks the trade-off between **circuit depth** and **qubit count** on Noisy Intermediate-Scale Quantum (NISQ) devices using the ATLAS Higgs Boson dataset.

**Key Findings:**
* **"Squeeze and Deepen":** A 4-qubit deep circuit (`reps=2`) outperformed wider circuits, achieving **56.2% accuracy**.
* **Barren Plateau:** The 8-qubit model failed to converge due to vanishing gradients in high-dimensional Hilbert space.

---

## Quick Start (Run in Browser)

You do **not** need to install anything on your local machine. The entire experiment is designed to run in the cloud via Google Colab.

### Step 1: Open the Notebook
Click the badge below to open the interactive notebook:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1BvhjWAd0qxb4LU3bzZUXkT6XpY-c4LD3?usp=sharing)

### Step 2: Upload the Dataset
The notebook requires the dataset file to run.
1. Download `training.csv` from the [CERN Open Data Portal](http://opendata.cern.ch/collection/ATLAS-Higgs-Challenge-2014) or from the `data/` folder in this repository.
2. In Google Colab, click the **Folder Icon** (left sidebar).
3. Drag and drop the `training.csv` file into the sidebar.

### Step 3: Run All Cells
In the Colab menu, go to **Runtime** > **Run all**.
* *Note:* The first cell will automatically install the required libraries (`qiskit`, `qiskit-machine-learning`, etc.) into the cloud environment.

---

## Key Results

### 1. Optimal Result (4-Qubit Deep Circuit)
With increased entanglement depth, the VQC successfully separates the Signal (Higgs) from the Background.

| Configuration | Qubits | Depth (Reps) | Accuracy | Status |
| :--- | :---: | :---: | :---: | :--- |
| **Stage II** | **4** | **2** | **56.2%** | **Optimal** |

![PCA Projection](assets/deep_circuit_result_projection.png)

*Figure 1: PCA Projection of the decision boundary. Red points are Higgs Signals, Blue points are Background.*

### 2. The Failure of Width (8-Qubit)
Expanding to 8 qubits resulted in optimization failure, consistent with the **Barren Plateau** phenomenon.

| Configuration | Qubits | Depth (Reps) | Accuracy | Status |
| :--- | :---: | :---: | :---: | :--- |
| **Stage III** | 8 | 1 | 50.6% | Failed to Converge |

---

## Tech Stack
* **Language:** Python
* **Quantum SDK:** Qiskit (IBM Quantum)
* **Optimization:** COBYLA (Scikit-learn / Qiskit Algorithms)
* **Data Processing:** Pandas, NumPy, PCA

---

## Citation

If you use this code or findings in your research, please cite:

```bibtex
@article{Maulana2025HiggsQML,
  title={Impact of Circuit Depth versus Qubit Count on Variational Quantum Classifiers for Higgs Boson Signal Detection},
  author={Maulana, Fatih},
  journal={arXiv preprint},
  year={2025},
  institution={Universiti Utara Malaysia and UIN Sunan Gunung Djati Bandung}
}
