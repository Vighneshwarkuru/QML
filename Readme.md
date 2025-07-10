# 🧬 Quantum Machine Learning on Breast Cancer Dataset

This project applies principles of **Quantum Machine Learning (QML)** to the Breast Cancer Wisconsin dataset for binary classification of tumor samples. We use a **Variational Quantum Circuit (VQC)** implemented in [PennyLane](https://pennylane.ai/) with **Angle Encoding** to encode classical data into quantum states. The goal is to evaluate how quantum models perform on real-world medical datasets.

---

## 📊 Dataset

- **Source**: `scikit-learn.datasets.load_breast_cancer()`
- **Features**: 30 real-valued inputs describing tumor cell properties
- **Labels**: Binary classification — 0 for *benign*, 1 for *malignant*

---

## 🧠 What We Did

- Implemented a 4-qubit quantum classifier using PennyLane
- Used **Angle Encoding** to transform classical features into qubit rotations
- Built a VQC with **StronglyEntanglingLayers** and **Pauli-Z measurements**
- Trained the model using gradient descent over 20 epochs
- Achieved up to **89.07% accuracy** on the test set

---

## 🧮 Quantum Circuit Overview

- **Encoding Method**: `AngleEmbedding` using Ry rotation gates
- **Entanglement**: Applied using `StronglyEntanglingLayers` with trainable weights
- **Output**: Measured using `expval(PauliZ)` to map predictions to \([-1, 1]\)
- **Loss Function**: Mean Squared Error (MSE)
- **Optimizer**: Gradient descent using **Parameter Shift Rule**

---

## 📈 Results

- **Training Accuracy**: ~88%
- **Test Accuracy**: ~78.07%
- Training converged over 20 epochs
- Classical preprocessing was minimal; most transformation occurred in the quantum layer

---

## 🧪 Quantum Encoding Methods (Explored)

We studied several methods of encoding classical data into quantum systems:

| Encoding Method       | Qubit Usage     | Circuit Depth     | Implemented | Notes |
|----------------------|------------------|-------------------|-------------|-------|
| **Angle Encoding**    | Moderate         | Low               | ✅          | Practical and simple with $R_y(x)$ rotations |
| Amplitude Encoding   | Very Efficient   | Medium–High       | ❌          | Full vector in amplitudes; needs normalization |
| Basis Encoding       | Inefficient      | Low               | ❌          | Only works with binary features |
| Hybrid Encoding      | Variable         | High              | ❌          | Combines multiple schemes |
| Dense Encoding       | High             | High              | ❌          | Multiple features per qubit; complex mapping |
| Permutation Encoding | Medium           | Variable          | ❌          | Encodes info in ordering or gate sequence |

---

## 🧠 Mathematical Concepts

- **Pauli-Z Operator**: Measures qubit states in the Z-basis  
  \[
  Z = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
  \]
  
- **Rotation Gate**:  
  \[
  R_y(\theta) = 
  \begin{bmatrix}
  \cos\left(\frac{\theta}{2}\right) & -\sin\left(\frac{\theta}{2}\right) \\
  \sin\left(\frac{\theta}{2}\right) & \cos\left(\frac{\theta}{2}\right)
  \end{bmatrix}
  \]

- **Parameter Shift Rule**: Gradient computation without backprop  
  \[
  \frac{\partial L}{\partial w_j} = \frac{f(x, w + \frac{\pi}{2} e_j) - f(x, w - \frac{\pi}{2} e_j)}{2}
  \]

---

## 🚀 How to Run

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/qml-breast-cancer.git
    cd qml-breast-cancer
    ```

2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
---

## 📌 Future Work

- Implement and benchmark additional encoding strategies
- Test on more complex or larger datasets
- Hybrid classical-quantum models (QNNs + CNNs or MLPs)
- Compare performance against traditional ML baselines (SVM, RF, etc.)

---

## 👥 Authors & Mentorship

**Authors:**
- Vighneshwar Kuru
- Sloka Reddy Mandhadi

**Mentor:**  
🧑‍🏫 Dr. Raghu Indrakanti

---

## 🪪 License

This project is licensed under the **MIT License**.
