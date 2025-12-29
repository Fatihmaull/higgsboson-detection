# Impact of Circuit Depth versus Qubit Count on Variational Quantum Classifiers (VQC)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Qiskit](https://img.shields.io/badge/Qiskit-0.46.0-6133BD)
![Status](https://img.shields.io/badge/Status-Research%20Completed-success)
![License](https://img.shields.io/badge/License-MIT-green)

**Author:** Fatih Maulana¹²  
¹ *School of Computing, Universiti Utara Malaysia* ² *Faculty of Science and Technology, UIN Sunan Gunung Djati Bandung*

---

## Project Overview

This repository contains the official implementation code for the research paper: **"Impact of Circuit Depth versus Qubit Count on Variational Quantum Classifiers for Higgs Boson Signal Detection"**.

In the era of Noisy Intermediate-Scale Quantum (NISQ) computing, finding the optimal architecture for Quantum Machine Learning (QML) is a critical challenge. This study benchmarks the trade-off between **circuit depth (entanglement capability)** and **qubit count (feature width)** using the ATLAS Higgs Boson dataset.

**Key Findings:**
* **"Squeeze and Deepen" Strategy:** Prioritizing circuit depth over width yields better performance on NISQ devices.
* **Optimal Configuration:** A 4-qubit deep circuit (`reps=2`) achieved the highest accuracy (**56.2%**).
* **Barren Plateau:** Simply expanding the width to 8 qubits caused optimization failure (accuracy dropped to **50.6%**) due to vanishing gradients in the larger Hilbert space.

---

## Methodology & Stack

The project implements a full Quantum Machine Learning pipeline:

1.  **Preprocessing:** Data cleaning, normalization, and balancing (Signal vs Background).
2.  **Dimensionality Reduction:** **Principal Component Analysis (PCA)** to map 30 physical features into latent quantum spaces ($4$ and $8$ qubits).
3.  **Quantum Circuit:**
    * **Feature Map:** `ZZFeatureMap` (Second-order expansion).
    * **Ansatz:** `RealAmplitudes` (Parameterized rotation layers + CNOT entanglement).
4.  **Optimization:** `COBYLA` (Gradient-free optimizer suitable for noisy simulations).

### Tech Stack
* **Language:** Python
* **Quantum SDK:** Qiskit
* **ML Library:** Scikit-learn
* **Data Manipulation:** Pandas, NumPy

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
Expanding to 8 qubits resulted in a random-guess performance, consistent with the **Barren Plateau** phenomenon.

| Configuration | Qubits | Depth (Reps) | Accuracy | Status |
| :--- | :---: | :---: | :---: | :--- |
| **Stage III** | 8 | 1 | 50.6% |  Failed to Converge |

---

## Installation & Usage

### Prerequisites
Ensure you have Python 3.8+ installed.

### 1. Clone the Repository
```bash
git clone [https://github.com/username/quantum-higgs-classifier.git](https://github.com/username/quantum-higgs-classifier.git)
cd quantum-higgs-classifier
```

### 2. Install Dependencies
Bash

pip install -r requirements.txt

3. Download Dataset
This project uses the ATLAS Higgs Boson Machine Learning Challenge 2014 dataset.

Download training.csv from CERN Open Data Portal.

Place the file in the root directory or data/ folder.

4. Run the Experiment
You can run the Jupyter Notebook directly or execute the Python script:

Bash

jupyter notebook notebooks/Quantum_Higgs_Classifier.ipynb
