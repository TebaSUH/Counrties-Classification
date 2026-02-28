# Countries Classification – Machine Learning Project

## Overview
Image classification project focused on distinguishing between three countries—Japan, France, and Mexico—using street-level imagery from a Hugging Face dataset.  

The project fine-tunes a Vision Transformer (ViT) model to learn geographic and environmental visual patterns while maintaining strong generalization performance on a relatively small dataset.

---

## Dataset
Source: marcelomoreno26/geoguessr 
Classes: Japan, France, Mexico  
Split: 70% Train / 15% Validation / 15% Test  

Preprocessing:
- Images resized to match ViT input size (224×224)
- Normalization using standard ImageNet statistics
- Data augmentation applied during training

---

## Architecture

Base Model: Vision Transformer (ViT)  

Model Pipeline:
1. Images are divided into fixed-size patches.
2. Patches are embedded into a vector space.
3. Positional embeddings are added.
4. Multi-head self-attention layers extract global relationships.
5. A classification token ([CLS]) is used for final country prediction.

The transformer attention mechanism enables the model to capture long-range spatial dependencies across the image.

---

## Training Configuration

Optimizer: AdamW  
Loss Function: CrossEntropyLoss  
Learning Rate: 1e-4  
Data Augmentation:
- Random Horizontal Flip (p=0.5)
- Random Rotation (±15°)
- Color Jitter
- Random Resized Crop  

Training and validation losses were monitored to evaluate convergence and detect overfitting.

---

## Results

- Training loss decreased steadily across epochs.
- Validation loss followed a similar trend, indicating good generalization.
- The gap between training and validation loss remained controlled, suggesting limited overfitting.

The model successfully learned discriminative geographic features from visual cues such as architecture, road structure, vegetation, and environmental characteristics.

---

## How to Use (Google Colab)
1. **Open the Notebook:** Click the "Open in Colab" badge above.
2. **Enable GPU:** Go to `Runtime` > `Change runtime type` and select a **T4 GPU**.
3. **Execute:** Click `Runtime` > `Run all`.
   At the end you can test it yourself by adding an image from the dataset in this section:<img width="1422" height="334" alt="image" src="https://github.com/user-attachments/assets/e891b652-e9c2-40d9-9311-18206e5066ef" />
5. **View Inference:** Scroll to the bottom to see training/validation loss plots and generated captions for validation images.



