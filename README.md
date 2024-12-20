# Federated Learning on Medical Images

**By Harmke Alkemade and Andreas Kopp**

![Federated Learning on Medical Images](path/to/image.jpg)

In December 2021, we published several assets to support Medical Imaging with Azure Machine Learning. The great interest and numerous inquiries have shown how AI applications are becoming increasingly vital in medical practice.

With **Federated Learning**, we introduce an exciting addition to our portfolio that holds significant importance inside and outside healthcare, protecting both data and intellectual property.

## Overview of Use Cases

The following illustration provides an overview of our demo use cases, including our latest addition of Federated Learning.

![Use Cases Illustration](path/to/illustration.jpg)

In our demo scenario, you can build a global Federated Learning system with simulated participating hospitals in the United States, Europe, and Asia to develop a common ML model for detecting pneumonia in X-ray images. This repository provides the conceptual basis of Federated Learning and guides you through the key elements of the demo.

### Try It Yourself!
Explore the repository to try out this use case or adapt it for your business scenarios.

---

## The Federated Learning Concept

Critical success factors for generalizable deep learning models include access to extensive and heterogeneous training data. For example, a reliable cancer detection model must be trained on thousands of medical images representing diverse demographics, imaging techniques, and real-world variations.

However, collaboration among hospitals often faces challenges due to strict data protection laws. Federated Learning addresses this issue by allowing multiple parties to collaboratively train machine learning models **without sharing data**.

![Federated Learning Concept](path/to/concept-diagram.jpg)

### Key Features:
- **Central Server for Aggregation:** Aggregates model parameters and orchestrates the training process.
- **Privacy-Preserving Local Training:** Local data stays with the clients, and only model parameter updates are shared.
- **Secure Aggregation:** Ensures individual updates are protected and visible only in aggregate.

Federated Learning supports enterprise scenarios with strict security and compliance requirements. For example:
- IT infrastructure and powerful GPUs can be used for medical imaging tasks.
- Differential Privacy can be applied to protect the resulting model from model inversion attacks.

---

## Demo Architecture

The demo setup enables hospitals to train a central model using their private datasets. Key architectural elements include:
- **Central Server**: Hosted on an Azure Data Science Virtual Machine.
- **Hospitals as Clients**: Represented by Azure Machine Learning Workspaces in different regions.
- **Framework**: Utilizes the NVIDIA NVFlare package for configuration and orchestration.

The training process uses a public Kaggle dataset containing X-ray images of patients with and without pneumonia. A binary classification model is trained to classify X-ray images into 'pneumonia' or 'normal' categories.

---

## How to Run the Demo

### 1. Set Up Infrastructure
Use GitHub Actions workflows to:
- Create Azure resources, including a Data Science Virtual Machine and three Azure Machine Learning Workspaces.
- Download and prepare the pneumonia dataset from Kaggle.
- Split and register private datasets for each client.

### 2. Initialize Federated Learning
1. Clone the repository on the Azure VM.
2. Configure the `project.yml` file for server and client settings.
3. Run the provisioning tool to generate client and server startup kits:
   ```bash
   provision -p project.yml
