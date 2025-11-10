## 🚀 Project Overview: Evolutionary Optimization of Neural Networks

This project evaluates multiple optimization techniques—**Gradient Descent (GD)**, **Particle Swarm Optimization (PSO)**, **Covariance Matrix Adaptation Evolution Strategy (CMA-ES)**, and **Non-dominated Sorting Genetic Algorithm II (NSGA-II)**—to enhance image classification accuracy. The study uses a lightweight **ResNet-18** model on the **CIFAR-10** dataset, specifically focusing on optimizing its final layer and addressing deep learning challenges like the vanishing gradient problem and overfitting.

### ❓ Problem Statement

Image classification using deep Convolutional Neural Networks (CNNs) often faces challenges such as:
* **Overfitting** on small datasets.
* **Vanishing gradients** in deep architectures.
* High **computational cost** of optimization techniques.
* Difficulty in **hyperparameter tuning**.

This project addresses these issues by employing a targeted optimization strategy on the network's most critical section, the final fully connected layer.

---

## 🔬 Methodology

### Dataset

* **CIFAR-10**: Contains 60,000 color images (32×32) across 10 classes (50,000 for training, 10,000 for testing).

### Model: ResNet-18

* **Architecture**: An 18-layer deep CNN.
* **Key Feature**: Incorporates **residual (skip) connections** to mitigate the vanishing gradient problem. 
* **Optimization Target**: The final fully connected layer, which contains **5,130 parameters** (5120 weights + 10 biases).

### Hybrid Optimization Strategy

The weights of the entire ResNet-18 model were first pre-trained using standard methods. Crucially, all convolutional layers were then **frozen**, and only the weights of the final layer were subjected to randomization and subsequent optimization by the algorithms below.

### ⚙ Optimization Algorithms

The final layer weights were optimized over **50 Epochs/Generations** using **Cross-Entropy Loss** and a **Batch Size of 128**.

| Algorithm | Category | Accuracy (%) | Notes |
| :--- | :--- | :--- | :--- |
| **Gradient Descent (GD)** | Gradient-Based | **80.09** | Best performance and fastest convergence. |
| **Particle Swarm Optimization (PSO)** | Evolutionary/Swarm | 60.71 | Faster execution than CMA-ES, but less accurate than GD. |
| **CMA-ES** | Evolutionary Strategy | 24.06 | Computationally expensive; stable but slow improvement. |
| **NSGA-II** | Multi-Objective | 19.3 | Poor performance due to trade-offs and resource limitations. |

### Bi-Objective Optimization (NSGA-II)

NSGA-II was used to balance two conflicting objectives: **Maximizing Classification Accuracy** and **Minimizing Gaussian Regularization** (weight decay) to prevent overfitting. The resulting performance was lower because the necessary trade-offs introduced by multi-objective search led to a suboptimal result compared to the single-minded focus of GD.

---

## 📈 Key Results and Conclusion

### Performance Summary

* **Gradient Descent** demonstrated the most effective loss minimization and achieved the highest final accuracy, proving the most efficient approach for optimizing the last layer in this specific context.
* **CMA-ES** and **PSO**, while powerful in non-convex or derivative-free environments, were not computationally competitive with GD under the given constraints.
* The multi-objective nature of **NSGA-II** caused it to underperform, suggesting that for high-accuracy tasks on this dataset, a single-objective focus is optimal.

### Conclusion

**Gradient Descent is the most effective technique for optimizing ResNet-18 on CIFAR-10 in this study.** Evolutionary methods should be reserved for scenarios where derivative information is unavailable, where the search space is highly discontinuous, or when critical trade-offs between competing objectives are mandatory.

---

## 👤 Author
Ishwari Niphade | Data Scientist | MSc Data Science | https://www.linkedin.com/in/ishwari-niphade/ | https://github.com/ishwari215
