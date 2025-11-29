# TumorNet

Multi-class MRI tumor diagnosis using ViT, ResNet-50, and Explainable AI (Grad-CAM + Saliency Maps)

## Overview

This project builds and evaluates a deep learning–based brain tumor classification system using MRI images across four tumor types:

* Glioma
* Meningioma
* Pituitary
* No Tumor

## Two state-of-the-art architectures are compared:

* Vision Transformer (ViT-Base-Patch16-224)
* ResNet-50 (CNN)

## To improve trust and interpretability in medical AI, the project integrates:

* Grad-CAM heatmaps (for ResNet)
* Saliency maps (for both ViT and ResNet)

## Dataset

The dataset consists of brain MRI images grouped into four classes:
* glioma_tumor
* meningioma_tumor
* pituitary_tumor
* no_tumor

Dataset is split into:

* Split	Percentage	Source Folder
* Train	80%	Training/
* Validation	20% of Training	auto-split
Test	100%	Testing/

## Installation
pip install torch torchvision timm grad-cam gradio matplotlib scikit-learn

## Model Architectures
### 1. Vision Transformer (ViT-Base-Patch16-224)

* Pretrained with ImageNet-1k
* Patch embeddings + multi-head self-attention
* Strong global representation learning (ideal for MRI)

### 2. ResNet-50 (CNN)

* Deep convolutional backbone
* Strong local feature extraction
* Excellent for Grad-CAM explainability

## Training Pipeline

The notebook trains both models using:
* Image augmentation
* CrossEntropyLoss
* AdamW optimizer
* Learning rate = 1e-4
* Batch size = 16
* Epochs = 5 (can increase)

## Performance Metrics

During validation and testing, the following metrics are calculated:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

Both models are evaluated on identical splits to ensure fairness.

## Explainability 

* Grad-CAM (for ResNet-50)
* Highlights the most influential regions in the MRI, showing where the CNN focuses.
* Saliency Maps (for both models)
* Gradient-based sensitivity highlight around tumor regions.

## AI Radiologist Assistant (Gradio App)

A web-based interface where users can:

* Upload any MRI image
* Choose a model (ViT or ResNet)
* View classification results
* See heatmap explanations

Run the app:
demo.launch()


The interface looks like:

<img width="1012" height="471" alt="image" src="https://github.com/user-attachments/assets/c46fc74f-2e84-4ea4-ac17-541825892d71" />

## Results Summary

<img width="547" height="164" alt="image" src="https://github.com/user-attachments/assets/699c7d7d-f33c-4562-8e6b-a5af5df9af46" />

## Key Learnings

* Vision Transformers outperform CNNs on complex medical imaging tasks
* Explainability is essential for real-world medical AI
* Combining interpretability + accuracy makes the model clinically meaningful
* Building a Gradio UI turns the project into a usable application

## Technologies Used

* Python
* PyTorch
* Vision Transformer (ViT)
* ResNet-50
* Grad-CAM
* Saliency Maps
* Gradio
* Matplotlib
* scikit-learn
