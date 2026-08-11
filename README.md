# image-processing-computer-vision
# Computer-Vision-Segmentation-XAI

# Computer Vision: Segmentation & Explainable AI

This repository contains the code, experiments, and documentation for a Computer Vision project developed as part of the "Image Processing for Computer Vision" course at the University of Naples Federico II.

The project explores different approaches to image segmentation, covering semantic segmentation with FCN-ResNet50, instance segmentation with YOLO11, zero-shot instance segmentation with MobileSAM, and Explainable AI through Activation Maximization. The experiments were conducted on the COCO 2017 and Cityscapes datasets.

**Authors:** Enrico Gentile, Marcello Iacovelli, Davide Schimmenti, Hamza En Nakhly.

## 📖 Project Overview

The objective of this project is to investigate different approaches to Computer Vision segmentation tasks and analyze their performance and characteristics.

The project is divided into four main components:

- **Semantic Segmentation:** training and evaluation of an FCN-ResNet50 model on a subset of COCO 2017.
- **Instance Segmentation:** fine-tuning of YOLO11 for instance segmentation on the Cityscapes dataset.
- **Zero-Shot Instance Segmentation:** evaluation of MobileSAM using bounding box prompts extracted from ground-truth annotations.
- **Explainable AI:** analysis of the features learned by the trained FCN-ResNet50 model using Activation Maximization.

## 🧠 Models, Datasets and Approaches

### Semantic Segmentation

The semantic segmentation task was addressed using an **FCN-ResNet50** architecture.

The model was trained on a subset of **COCO 2017**, considering the class imbalance and the predominance of background pixels in the dataset.

The experimental pipeline included:

- Dataset preprocessing and geometric normalization.
- Training and validation of FCN-ResNet50.
- Comparison of different loss functions.
- Sanity checks and overfitting analysis.
- Hyperparameter optimization using Random Search.
- Evaluation using **mIoU** and **F1-score**.

The loss functions investigated include Cross-Entropy, Focal Loss, Dice Loss, Jaccard Loss, and combined loss functions. The final experiments were performed over 50 training epochs while keeping the architecture, preprocessing, data split, optimizer, and training configuration fixed to isolate the effect of the loss function. :contentReference[oaicite:1]{index=1}

### Instance Segmentation

Instance segmentation was addressed using **YOLO11** and the **Cityscapes** dataset.

The experiments included:

- Conversion and preparation of the Cityscapes dataset.
- Selection of the relevant object classes.
- Hyperparameter optimization.
- Fine-tuning of the YOLO11 model.
- Freezing of the initial backbone layers.
- Evaluation using Precision, Recall, AP and mAP for both bounding boxes and masks.

The fine-tuning stage was performed after hyperparameter optimization, with the first 10 backbone levels frozen in order to retain the features learned during the original COCO training. :contentReference[oaicite:2]{index=2}

### Zero-Shot Instance Segmentation

**MobileSAM** was evaluated as a lightweight foundation model for zero-shot instance segmentation.

Unlike the trained models used in the other experiments, MobileSAM was used without additional training on the target dataset.

The experimental setup included:

- Pre-trained MobileSAM model.
- Cityscapes dataset.
- Bounding box prompts extracted from ground-truth annotations.
- Generation and evaluation of instance masks.
- Evaluation using IoU and F1-score.
- Per-class performance analysis.

The goal was to investigate the ability of a lightweight foundation model to perform instance segmentation using prompts without dataset-specific training. :contentReference[oaicite:3]{index=3}

### Explainable AI

The Explainable AI component focuses on understanding the internal representations learned by the trained **FCN-ResNet50** model.

**Activation Maximization** was used to identify the visual patterns that strongly activate selected filters while keeping the model weights frozen.

Different levels of the network were analyzed in order to investigate the evolution of learned representations:

- **Layer 1 – Edge:** simple geometric structures and local intensity variations.
- **Layer 2 – Texture:** more complex local patterns, textures and repetitive structures.
- **Layer 3 – Semantic Regions:** abstract patterns associated with semantic regions.

The implementation involved activation hooks, input optimization and regularization to generate patterns that maximize the activation of selected filters. :contentReference[oaicite:4]{index=4}

## 📊 Evaluation

Different metrics were used according to the specific segmentation task.

### Semantic Segmentation

- Mean Intersection over Union (**mIoU**)
- **F1-score**
- Pixel-wise analysis
- Qualitative comparison between predicted masks and ground truth

### Instance Segmentation

- Precision
- Recall
- Average Precision (**AP**)
- Mean Average Precision (**mAP**)
- Bounding box and mask evaluation

### MobileSAM

- Intersection over Union (**IoU**)
- F1-score
- Per-class evaluation

## 👥 Task Distribution

The project was developed as a group project, with each member focusing on a specific component:

| Contributor | Main Contribution |
|---|---|
| **Enrico Gentile** | Semantic Segmentation & Explainable AI |
| **Marcello Iacovelli** | Semantic Segmentation |
| **Davide Schimmenti** | YOLO11 / Instance Segmentation |
| **Hamza En Nakhly** | MobileSAM / Zero-Shot Segmentation |

The Semantic Segmentation component was developed jointly by Enrico Gentile and Marcello Iacovelli, while Enrico Gentile was additionally responsible for the Explainable AI component based on Activation Maximization.

## 📁 Repository Structure

- `/src/Semantic_Segmentation`: implementation of the FCN-ResNet50 semantic segmentation pipeline, training, loss functions, evaluation and hyperparameter experiments.
- `/src/YOLO_Instance_Segmentation`: implementation and experiments related to YOLO11 instance segmentation and fine-tuning on Cityscapes.
- `/src/MobileSAM`: MobileSAM inference, prompt generation and evaluation.
- `/src/Explainable_AI`: Activation Maximization experiments and analysis on FCN-ResNet50.
- `/docs`: Project presentation, documentation and additional material.
- `/media`: Inference Images, plots and qualitative results from the experiments.

## 📚 Datasets

### COCO 2017

COCO 2017 was used for the semantic segmentation experiments.

The dataset contains more than 330,000 images and 80 object categories, with annotations including object classes, bounding boxes and segmentation masks. A subset with uniform geometry was selected for the experiments. :contentReference[oaicite:5]{index=5}

### Cityscapes

Cityscapes was used for the instance segmentation and MobileSAM experiments.

The dataset consists of high-resolution street-scene images collected from 50 different cities, with annotations for multiple object categories. :contentReference[oaicite:6]{index=6}

## 🛠️ Technologies

- Python
- PyTorch / torchvision
- FCN-ResNet50
- YOLO11
- MobileSAM
- COCO 2017
- Cityscapes
- Deep Learning
- Computer Vision
- Explainable AI
- Activation Maximization

## 📄 Project Presentation

The complete project presentation is available in the `/docs` directory.

## 🎓 Course

**Image Processing for Computer Vision – 2025/2026**

University of Naples Federico II

**Professors:** Giuseppe Scarpa, Matteo Ciotola
