VQC-PQC-AnomalyDetector-Cirq
Symmetry-aware anomaly detection over abstracted post-quantum cryptographic (PQC) protocol features, using Variational Quantum Circuits implemented in Cirq.

Topics: variational quantum classifiers · post-quantum symmetry · quantum anomaly detection · PQC graph anomalies

Scope note. Exploratory research at 2-qubit scale on toy feature vectors. All results are from simulators; no hardware execution is claimed.


Notebooks
1. vqc_input_anomaly_analysis.ipynb — input encoding and raw anomaly testing
Simulates toy PQC traffic features (e.g. [π/4, 3π/4])
Encodes features via RY rotations, one qubit per feature dimension
Applies an entangling layer followed by a variational block
Measures output bitstring probabilities over 100 shots
Compares a baseline input against a perturbed input

Outcome: clear shifts in the probability distribution under perturbation, consistent with broken symmetry in the encoded state.
2. vqc_classifier_training.ipynb — brute-force training via grid search
Trains the circuit by parameter sweep over θ₀ and θ₁
Classifies by majority vote on measurement outcomes (0 = normal, 1 = anomaly)

Outcome: fits the training data exactly, but misclassifies anomalous inputs in edge cases — the grid resolution is too coarse to place a reliable decision boundary. The zero-loss figure describes fit on training data only and should not be read as generalisation.
3. vqc_classifier_training_with_gradients.ipynb — parameter-shift training
Manual parameter-shift gradient estimation
Minimises squared classification loss
Reports prediction confidence as P(measure 1), plotted as a confidence bar chart

Outcome: correctly identifies the anomalous input with better generalisation than grid search. The confidence margin is modest (roughly 0.58 vs 0.42), which is enough to separate the two classes on this toy set but is not a strong decision boundary.


Key takeaways
Variational circuits are sensitive to symmetry violations in encoded features
Gradient-based training outperforms brute-force search on this task, and the proposed reason is finer loss resolution near the boundary
Structural shifts in feature space are detectable even at 2 qubits


Limitations
Toy feature vectors, not captured PQC traffic
2-qubit circuits; conclusions may not survive scaling
Small margins on the gradient-trained model
No noise model applied; no hardware runs


Future work
Extend encoding to graph-based PQC traffic flows
Scale to 3–4 qubit models for richer feature input
Add PQC noise simulation or integrate liboqs / ML-KEM traces
Explore hybrid classical–quantum pipelines in PennyLane


Citation
@misc{somaraju_vqc_pqc_anomaly_2025,

  title  = {Quantum Symmetry-Aware Anomaly Detection in Post-Quantum Cryptographic

            Protocols Using Variational Quantum Circuits},

  author = {Somaraju, Vijay Krishna},

  year   = {2025},

  note   = {Unpublished manuscript},

  url    = {https://github.com/vijaysuperpositionist/VQC-PQC-AnomalyDetector-Cirq}

}
Built with
Cirq
NumPy
SymPy
License
MIT License © 2025 Vijay Krishna Somaraju. Use, fork, remix freely.

