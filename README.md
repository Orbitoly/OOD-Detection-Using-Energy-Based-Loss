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

## Results

The application of our model to the MNIST dataset and subsequent testing against OOD datasets like CIFAR-10 and Fashion-MNIST demonstrated promising results. These outcomes highlight the potential of energy-based models in tackling the challenges of OSR.


## Key Takeaways

- Our implementation reaffirms the effectiveness of energy-based models for open set recognition as discussed in the referenced paper.
- The project underlines the importance of parameter tuning in optimizing the model for accurate OOD detection.
- Through practical experimentation, we explored the nuances of applying energy-based models to OSR, contributing to a deeper understanding of their potential and limitations.

## Usage

For details on replicating our experiments and further information on the project setup, please refer to the documentation provided in this repository.



## License

This project is distributed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
---

