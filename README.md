

# Pathology Zero-Shot Anomaly Detection
## Implementation of Ano-NAViLa
This repository provides a comprehensive pipeline for detecting anomalies in histopathology Whole Slide Images (WSIs) using a zero-shot approach. By leveraging the Ano-NAViLa framework and the CONCH vision-language model, this tool identifies metastatic tumor regions without the need for additional training or fine-tuning.

## Project Overview
Detection of cancerous tissues in high-resolution medical imagery typically requires large labeled datasets. This project implements a Vision-Language Model (VLM) alignment strategy to perform anomaly detection by comparing image patches against specialized medical descriptions.

<img width="900" height="541" alt="Screenshot 2026-06-18 at 12 17 22 AM" src="https://github.com/user-attachments/assets/0d622162-ec51-453c-acf6-288bcd7a3cf9" />
<img width="352" height="278" alt="Screenshot 2026-06-18 at 12 17 08 AM" src="https://github.com/user-attachments/assets/cef42a70-8a07-4db0-a002-fddd78128274" />

## Core Features
- Full end-to-end pipeline from raw WSI to heatmap visualization.
- Integration with the CONCH backbone, specifically pre-trained for pathology tasks.
- Support for complex medical prompt dictionaries (92 normal and 48 abnormal descriptors).
- Automated patch extraction and tissue-background segmentation.
- Transparent heatmap overlay for clinical interpretability.

## Technical Workflow
1. Patch Extraction: Using OpenSlide to segment tissue and extract 256x256 patches.
2. Text Embedding: Processing a specialized pathology glossary through the CONCH text encoder.
3. Anomaly Scoring: Calculating distances between patch embeddings and the normal/abnormal text clusters.
4. Visualization: Reconstructing the scores into a global heatmap and overlaying it on the original slide.

## Installation and Setup

### System Requirements
- Python 3.10 or higher
- CUDA-enabled GPU (recommended for inference)
- OpenSlide library

## Usage
The entire pipeline is available in the provided Jupyter Notebook and could be run with Google colab. It covers:
- Loading the CONCH and Ano-NAViLa architectures.
- Running patch-level inference on WSI tiles.
- Generating and saving high-resolution anomaly heatmaps.

## Acknowledgments
This implementation is based on the research provided by the Mahmood Lab (CONCH) and the QuIIL research group (Ano-NAViLa). We thank the contributors to the Camelyon16 challenge for providing the benchmarking data.
