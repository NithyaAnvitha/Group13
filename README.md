## Enhanced BROIE with ORPL for Remote Sensing Image Segmentation

An enhanced deep learning framework for **salient object detection in remote sensing images**, combining boundary-aware segmentation and semi-supervised learning to improve object localization and segmentation quality.

## 📌 Project Overview

Remote sensing images contain complex backgrounds, objects at different scales, and unclear object boundaries, making accurate segmentation challenging. This project extends the BROIE-based segmentation framework with **Offset-guided Reliability-aware Pseudo-Labeling (ORPL)** to improve the use of unlabeled data and refine predicted object boundaries.

The framework integrates segmentation, edge detection, and offset prediction with a reliability-aware semi-supervised learning strategy.

## 🎯 Objectives

- Develop an enhanced BROIE-based segmentation framework.
- Improve boundary localization using edge and offset prediction.
- Leverage unlabeled images through pseudo-label-based semi-supervised learning.
- Refine pseudo-labels using offset information and reliability estimates.
- Evaluate segmentation performance using IoU and F1-score.

## 🏗️ Proposed Architecture

The framework consists of the following components:

1. **EfficientNet-B0 Encoder:** Extracts hierarchical features from remote sensing images.
2. **Decoder with Skip Connections:** Combines encoder features to reconstruct spatially detailed representations.
3. **Segmentation Head:** Predicts the foreground segmentation mask.
4. **Edge Prediction Head:** Learns object boundaries to support contour refinement.
5. **Offset Prediction Head:** Predicts spatial offset information associated with object boundaries.
6. **ORPL Module:** Refines pseudo-labels using offset information, confidence, and reliability estimates.
7. **Discriminator-Based Reliability Gate:** Provides an additional reliability signal for pseudo-label learning.

## 🔄 Workflow

```text
Remote Sensing Images
        |
        v
Image Preprocessing
        |
        v
EfficientNet-B0 Encoder
        |
        v
Decoder with Skip Connections
        |
        +---------------------+
        |          |          |
        v          v          v
   Segmentation   Edge      Offset
      Head        Head       Head
        |          |          |
        v          v          v
   Binary Mask  Boundaries  Offsets
        |
        v
ORPL Pseudo-Label Refinement
        |
        v
Reliability-Based Filtering
        |
        v
Discriminator Reliability Gate
        |
        v
Semi-Supervised Training
        |
        v
Final Segmentation Masks
```

## 🗂️ Dataset

This implementation uses the **EORSSD (Extended Optical Remote Sensing Salient Object Detection) dataset**.

Expected directory structure:

```text
EORSSD/
├── train-images/
├── train-labels/
├── test-images/
└── test-labels/
```

- Input images: RGB images (`.jpg`)
- Ground-truth masks: PNG images (`.png`)
- Input images and masks are resized to `512 × 512` during preprocessing.

Ensure that image and mask filenames correspond correctly.

## 🛠️ Technologies Used

- Python
- PyTorch
- Torchvision
- NumPy
- Pillow
- Matplotlib
- pandas
- Google Colab
- Google Drive

## ⚙️ Installation

Install the required Python libraries:

```bash
pip install torch torchvision numpy pillow matplotlib pandas
```

## 🚀 How to Run

1. Clone or download this repository.
2. Open `Grp13_code.ipynb` in Google Colab or Jupyter Notebook.
3. Upload or mount the EORSSD dataset.
4. Update dataset and checkpoint paths according to your environment.
5. Execute the notebook cells in order.
6. Run supervised training and save the trained model checkpoint.
7. Execute the semi-supervised training stages with ORPL.
8. Evaluate the trained model using the test dataset.
9. Inspect the predicted segmentation masks and evaluation metrics.

**Note:** Some notebook cells load previously saved checkpoints. Ensure that the corresponding checkpoint files exist before running those cells.

## 📊 Evaluation Metrics

The model is evaluated using:

- **Intersection over Union (IoU):** Measures overlap between predicted and ground-truth segmentation masks.
- **F1-score:** Measures the balance between precision and recall.

The notebook also includes visual comparisons of input images, ground-truth masks, and predicted masks.

## 📁 Expected Outputs

- Trained model checkpoints
- Predicted segmentation masks
- Segmentation visualization images
- IoU and F1-score evaluation results
- Pseudo-label refinement and offset visualizations

The notebook's default final evaluation configuration saves results under `EORSSD_Final_Results/` in Google Drive. Update the output paths as required.

## 💡 Key Contributions

- Integration of segmentation, edge, and offset prediction heads.
- Offset-guided pseudo-label refinement through ORPL.
- Reliability-aware learning for unlabeled remote sensing images.
- Discriminator-based reliability gating for semi-supervised training.
- Quantitative and visual evaluation of segmentation performance.

## 🔮 Future Work

- Evaluate generalization across additional remote sensing datasets.
- Conduct ablation studies to measure the contribution of individual modules.
- Compare the framework against the baseline BROIE model.
- Investigate improvements in boundary accuracy and pseudo-label reliability.
- Explore geospatial localization and integration with GIS applications.

## 👥 Project Information

**Project:** Enhanced BROIE with ORPL for Remote Sensing Image Segmentation  
**Team:** Group 13  
**Implementation:** Python and PyTorch


