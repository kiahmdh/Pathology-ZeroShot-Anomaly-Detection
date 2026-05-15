# Pathology Zero-Shot Anomaly Detection
## Implementation of Ano-NAViLa
This repository provides a comprehensive pipeline for detecting anomalies in histopathology Whole Slide Images (WSIs) using a zero-shot approach. By leveraging the Ano-NAViLa framework and the CONCH vision-language model, this tool identifies metastatic tumor regions without the need for additional training or fine-tuning.

## Project Overview
Detection of cancerous tissues in high-resolution medical imagery typically requires large labeled datasets. This project implements a Vision-Language Model (VLM) alignment strategy to perform anomaly detection by comparing image patches against specialized medical descriptions.

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

### Setup Instructions
1. Clone the repository:
   git clone https://github.com/YourUsername/Pathology-ZeroShot-Anomaly-Detection.git
   cd Pathology-ZeroShot-Anomaly-Detection

2. Install dependencies:
   pip install -r requirements.txt

3. Acquire Model Weights:
   Place the 'pytorch_model.bin' (CONCH) and 're_trained_weights.pth' (Ano-NAViLa) in the project root directory.

## Usage
The entire pipeline is available in the provided Jupyter Notebook. It covers:
- Loading the CONCH and Ano-NAViLa architectures.
- Running patch-level inference on WSI tiles.
- Generating and saving high-resolution anomaly heatmaps.

## Performance and Results
The framework demonstrates high sensitivity in detecting tumor clusters within lymph node sections. The separation between normal lymphocytes and metastatic carcinoma is clearly visible in the generated anomaly scores.

## Acknowledgments
This implementation is based on the research provided by the Mahmood Lab (CONCH) and the QuIIL research group (Ano-NAViLa). We thank the contributors to the Camelyon16 challenge for providing the benchmarking data.
