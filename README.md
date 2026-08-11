# VQC-PQC-AnomalyDetector
vqclassifier-postquantum-symmetry  quantum-anomaly-detection-pqc  quantum-symmetry-classifier  pqc-vqc-graphanomaly
### 1. `vqc_input_anomaly_analysis.ipynb`
*Input Encoding & Raw Anomaly Testing*

- Simulates toy PQC traffic features (e.g., `[π/4, 3π/4]`)
- Encodes features via `RY` gates
- Applies a simple entangling + variational circuit
- Measures output bitstring probabilities over 100 shots
- Compares baseline input vs. perturbed input
- 🔍 Outcome: Shows clear probability distribution shifts indicating broken symmetry

---

### 2. `vqc_classifier_training.ipynb`
 *Brute-Force VQC Training via Grid Search*

- Trains the same circuit using brute-force parameter sweep over `θ₀` and `θ₁`
- Uses a majority vote classification scheme
- Compares predicted class (`0=Normal`, `1=Anomaly`) with true labels
-  Outcome: Achieves 100% accuracy *on training data*, but misclassifies anomaly input in some edge cases due to limited parameter resolution

---

### 3. `vqc_classifier_training_with_gradients.ipynb`
 *Gradient-Based Training using Parameter Shift Rule*

- Uses smooth parameter updates based on expectation-value shifts
- Implements manual parameter-shift gradient estimation
- Trains model to minimize squared classification loss
- Evaluates prediction confidence as probability of measuring `1`
- Plots bar graph of predicted class confidence
-  Outcome: Accurately detects anomaly with stronger generalization than brute-force; confidence plot shows clearer decision boundary

---

##  Key Takeaways

- Variational quantum circuits are **sensitive to symmetry violations** in encoded data
- **Gradient-based training outperforms brute-force search** in anomaly detection reliability
- Even with just **2 qubits**, the model captures structural shifts in feature space

---

##  Future Work

- Extend input encoding to **graph-based PQC traffic flows**
- Scale to **3–4 qubit models** for richer feature input
- Add **real PQC noise simulation** or integrate `liboqs`/Kyber traces
- Explore integration with **PennyLane** for hybrid classical–quantum pipelines

---

##  Citation

If you use this repo for academic or research work, please cite it as:
@project{vqc_pqc_anomaly_2025,
title={Quantum Symmetry-Aware Anomaly Detection using Variational Quantum Circuits},
author={Vijay the Navigator},
year={2025},
note={https://github.com/vijaysuperpositionist/VQC-PQC-AnomalyDetector}
}
##  Built With

- [Cirq](https://github.com/quantumlib/Cirq)
- [NumPy](https://numpy.org)
- [SymPy](https://www.sympy.org)
- 🧠 Human intuition meets quantum machine learning

---

##  License

MIT License. Use, fork, remix freely — especially for anything quantum and beautiful.
