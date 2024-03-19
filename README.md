# Open Set Recognition with Energy-Based Models

This repository showcases our project on "Open Set Recognition (OSR)" using energy-based models. It focuses on enhancing machine learning models' ability to process inputs from unknown classes, a vital feature for real-world applications.

## Project Overview

In real-world settings, machine learning models often face the challenge of open set recognition (OSR) — encountering data from classes absent during the training phase. Addressing OSR is crucial for deploying robust machine learning systems capable of handling a wide range of inputs.

For our project, we employed an energy-based out-of-distribution detection approach, which utilizes energy functions to model data density. This technique distinguishes between in-distribution (known) and out-of-distribution (unknown) inputs based on their energy scores.

### Inspiration and Acknowledgment

The core methodology of our project is inspired by the work presented in the paper "Energy-based Out-of-distribution Detection" by Weitang Liu, Xiaoyun Wang, John D. Owens, and Yixuan Li. While we have not introduced novel concepts, our project aims to implement, explore, and validate the principles discussed in the paper within the context of OSR. We extend our sincerest gratitude to the authors for their pioneering work, which serves as the foundation for our exploration.

### Team Members

- Omer Geva
- Or Virt
- Ido Itach



## Data Description

- **Closed Set (Training & Validation)**: The MNIST dataset, a collection of handwritten digits from 0 to 9, serves as the core dataset for training and validation. It represents the known classes the model is expected to recognize.
- **Open Set (Testing for Unseen Classes)**: To evaluate the model's ability to generalize to unseen classes, additional datasets such as CIFAR-10 and FashionMNIST are used as stand-ins for out-of-distribution (OOD) data. These datasets include images that are significantly different from the handwritten digits of MNIST (e.g., animals, vehicles from CIFAR-10, and clothing items from FashionMNIST), challenging the model to identify these as 'Unknown'.


## Task Objectives and Evaluation Metrics

The primary focus of this project is to:
1. **Accurately Classify Known Classes**: Achieve high accuracy in classifying the 10 digits from the MNIST dataset.
2. **Identify Unseen Classes as 'Unknown'**: Correctly label inputs from unseen classes during the test phase as 'Unknown', demonstrating the model's ability to handle OOD data effectively.

### Key Performance Indicators (KPIs)
- **Accuracy on MNIST**: The model's ability to maintain high classification accuracy on the MNIST test set, serving as the baseline performance metric.
- **Accuracy on Identifying 'Unknown'**: The effectiveness of the model in recognizing and classifying inputs from unseen classes (OOD data) as 'Unknown'.
- **Trade-off Management**: Balancing the drop in accuracy relative to the baseline model while incorporating OSR capabilities, aiming to mitigate as much accuracy loss as possible.
- **Computational Efficiency**: Ensuring the OSR model does not incur prohibitive computational overhead, making practical deployment feasible.
- **Discrimination Capability**: The model's proficiency in distinguishing between low-confidence predictions (e.g., poorly-written digits) and truly OOD inputs.

  
## Methodology

We adopted the energy-based model approach as outlined in the referenced paper. This method involves mapping input data to a scalar energy value, with lower energies indicating in-distribution data and higher energies signaling OOD inputs. Our model uses this principle to effectively identify and categorize unknown classes.

### Baseline and OSR Models

Our investigation begins with a Convolutional Neural Network (CNN) as a baseline, followed by the adaptation of this model to incorporate energy-based techniques for open set recognition. The adaptation includes a regularization term to the loss function, promoting an energy gap between in-distribution and OOD data.

Based on the details provided in your project description, here is a markdown write-up about the architecture of the network you used and the energy loss function implemented for Open Set Recognition using Energy-Based Models:

## Network Architecture

Our approach to addressing the Open Set Recognition (OSR) challenge leverages a Convolutional Neural Network (CNN) architecture, specifically designed to balance performance with computational efficiency. The chosen architecture comprises the following layers and components:

- **Convolutional Layers**: The network begins with a sequence of convolutional layers, which are pivotal for feature extraction from input images. Our model includes:
  - A first convolutional layer with 16 output channels and a kernel size of 5, followed by ReLU activation and max pooling.
  - A second convolutional layer with 32 output channels and a kernel size of 3, accompanied by ReLU activation and average pooling.
  
- **Fully Connected Layers**: After the convolutional layers, the architecture transitions to fully connected layers for classification:
  - A fully connected layer with 128 neurons, incorporating a dropout mechanism to prevent overfitting, followed by ReLU activation.
  - A final fully connected layer with 10 output neurons, corresponding to the 10 digit classes from the MNIST dataset.

This structure is designed to capture the hierarchical patterns within the input data efficiently, facilitating accurate classification of known classes while remaining computationally manageable.

## Energy Loss Function

To tackle the OSR problem, we employed an energy-based loss function alongside the standard cross-entropy loss. This hybrid approach combines the benefits of traditional classification loss with the robustness of energy-based models for identifying out-of-distribution (OOD) samples. The energy loss function is formulated as follows:

$$
L = L_{\text{CE}} + \lambda L_{\text{energy}}
$$

where:
- $L_{\text{CE}}$ is the cross-entropy loss, facilitating the classification of in-distribution data.
- $L_{\text{energy}}$ is the energy-based regularization term, which aims to increase the model's ability to distinguish between in-distribution and out-of-distribution samples by manipulating the energy scores associated with each input.
- $\lambda$ is a hyperparameter that balances the contribution of the cross-entropy loss and the energy-based loss, allowing for fine-tuning the model's sensitivity to out-of-distribution samples.
  
The energy function $\(E(x)\)$ for an input $\(x\)$ is derived from the model's logits, providing a scalar representation of the input's "energy." Lower energy values are indicative of in-distribution data, whereas higher values signal potential OOD samples. By carefully adjusting $\lambda$, we ensure the model remains accurate on known classes while gaining the capacity to recognize and flag unknown classes as 'Unknown.'


## Results

The application of our model to the MNIST dataset and subsequent testing against OOD datasets like CIFAR-10 and Fashion-MNIST demonstrated promising results. These outcomes highlight the potential of energy-based models in tackling the challenges of OSR.

Confusion Matrices, for MNIST (In-Distribution), FMNIST (Out-Of-Distribution) and CIFAR (Out-Of-Distribution)
<img width="314" alt="image" src="https://github.com/Orbitoly/Open-Set-Recognition-Using-Energy-Based-Model/assets/17669444/cb1ee5b5-56d2-4bd9-a4d9-47ce0aae9d3f">
<img width="329" alt="image" src="https://github.com/Orbitoly/Open-Set-Recognition-Using-Energy-Based-Model/assets/17669444/af291992-70bf-4c53-b37f-102554cf3a9d">
<img width="317" alt="image" src="https://github.com/Orbitoly/Open-Set-Recognition-Using-Energy-Based-Model/assets/17669444/94607667-3f2e-447b-8efb-c94e7a5d1bd6">

## Model Performance Summary

The following table summarizes the accuracy of our models across different datasets. Note that the reduction in accuracy for the Energy-based Model on MNIST is a strategic trade-off to enhance the model's ability to handle Out-of-Distribution (OOD) data effectively.

| Model               | MNIST Accuracy | CIFAR-10 Accuracy | FashionMNIST Accuracy |
|---------------------|----------------|-------------------|-----------------------|
| **Base Model**      | 96.49%         | N/A               | N/A                   |
| **Energy-based Model** | 91.45%         | 91.05%            | 89.21%                |

*Note*: The CIFAR-10 and FashionMNIST datasets are used as OOD data to evaluate the model's ability to recognize and handle unknown classes.

## Key Takeaways

- Our implementation reaffirms the effectiveness of energy-based models for open set recognition as discussed in the referenced paper.
- The project underlines the importance of parameter tuning in optimizing the model for accurate OOD detection.
- Through practical experimentation, we explored the nuances of applying energy-based models to OSR, contributing to a deeper understanding of their potential and limitations.

## Usage

For details on replicating our experiments and further information on the project setup, please refer to the documentation provided in this repository.



## License

This project is distributed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
---

