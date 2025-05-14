
---

# Jailbreaking Deep Models: Adversarial Attack Exploration

This repository contains the code and experiments for demonstrating the vulnerability of a **pre-trained ResNet-34 model to adversarial attacks**. The project focuses on compromising model performance by generating **subtle, imperceptible perturbations** to input images, thereby leading to incorrect classifications. We evaluate the effectiveness of several attack techniques, including **Fast Gradient Sign Method (FGSM)**, **Projected Gradient Descent (PGD)**, and **Patch-based attacks**. We also explore the **transferability** of these adversarial examples to a different model architecture (DenseNet-121), highlighting the security challenges in deep learning models.

## Features

* Implements various **adversarial attack techniques**:

  * **FGSM**: Fast Gradient Sign Method for \$L\_{\infty}\$ pixel-wise attacks.
  * **PGD**: Iterative attack method for improved adversarial example generation.
  * **Patch-based attacks**: Localized perturbations targeting small regions.
* Evaluates the **transferability** of adversarial examples between models.
* Uses **PyTorch** and **TorchVision** for model training and evaluation.
* Includes visualization of attack examples and performance metrics.

## Installation

To set up the environment, install the required dependencies:

```bash
pip install torch torchvision matplotlib numpy
```

Here’s the updated section with the additional point on downloading and unzipping the test dataset:

---

## Running the Code

1. Clone the repository:

   ```bash
   git clone https://github.com/kiritgpillai/dl-adversarial-attacks.git
   cd dl-adversarial-attacks
   ```
2. Download and unzip the test dataset:

   ```bash
   wget https://github.com/kiritgpillai/dl-adversarial-attacks/blob/main/TestDataSet.zip
   unzip dataset.zip -d data
   ```
3. Run the main script to:

   * Download and preprocess the **ImageNet-1K** test dataset.
   * Train or load the pre-trained **ResNet-34** model.
   * Generate adversarial examples using FGSM, PGD, and patch-based methods.
   * Evaluate model accuracy under different attack scenarios.
   * Assess transferability to **DenseNet-121**.

---
## Adversarial Attack Techniques

The following attack methods are implemented and evaluated:

* **Fast Gradient Sign Method (FGSM)**:

  * Simple one-step attack to create adversarial images.
  * \$L\_{\infty}\$ constraint: \$\epsilon=0.02\$

* **Projected Gradient Descent (PGD)**:

  * Iterative method to refine adversarial perturbations.
  * Parameters: 15 iterations, step size of 0.004, \$\epsilon=0.02\$

* **Patch-Based Attack**:

  * Localized attack affecting a 32x32 patch.
  * Parameters: 120 iterations, step size of 0.1, \$\epsilon=0.5\$

## Results

The performance of the **ResNet-34** model under various attacks and transferability to **DenseNet-121** is summarized below:

### Accuracy Reduction on ResNet-34

| Attack Type | Top-1 Accuracy | Top-5 Accuracy |
| ----------- | -------------- | -------------- |
| Baseline    | 76.00%         | 94.20%         |
| FGSM        | 6.20%          | 35.40%         |
| PGD         | 0.00%          | 9.60%          |
| Patch       | 10.40%         | 47.00%         |

### Transferability to DenseNet-121

| Attack Type | Top-1 Accuracy | Top-5 Accuracy |
| ----------- | -------------- | -------------- |
| FGSM        | 43.00%         | 67.40%         |
| PGD         | 42.00%         | 65.20%         |
| Patch       | 44.80%         | 70.20%         |

### Visualization of Attack Effectiveness

#### FGSM Attack Example:

![fgsm_examples](https://github.com/user-attachments/assets/70180f29-7bd7-46ab-bda6-73a3e01afec8)

#### PGD Attack Example:

![pgd_examples](https://github.com/user-attachments/assets/874ada1b-f31d-4fe4-b59a-7d4caa4b87a5)

#### Patch Attack Example:

![patch_attack_examples](https://github.com/user-attachments/assets/d63bb7c3-5866-4319-bfe6-eb242e28a71c)

### Transferability Plot:

![transferability_results](https://github.com/user-attachments/assets/f83db622-6300-4e0a-81b2-ff727da3ee5c)

## Key Findings

* **PGD** was the most effective, completely defeating the ResNet-34 model (Top-1 accuracy dropped to 0%).
* **FGSM** balanced efficiency and effectiveness, making it a practical choice for quick attacks.
* **Patch attacks** proved that localized perturbations can significantly affect model performance.
* **Transferability** analysis revealed that adversarial examples tend to be model-specific, with **PGD** showing the highest transfer rate to DenseNet-121.

---

### Authors

* Kirit Govindaraja Pillai - [kx2222@nyu.edu](mailto:kx2222@nyu.edu)
* Ruochong Wang - [rw3760@nyu.edu](mailto:rw3760@nyu.edu)
* Saketh Raman Ramesh - [sr7714@nyu.edu](mailto:sr7714@nyu.edu)

---

