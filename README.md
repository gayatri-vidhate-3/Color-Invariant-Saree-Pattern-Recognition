
# Color Invariant Saree Pattern Recognition

A computer-vision portfolio project exploring saree pattern classification, embedding-based image retrieval, and pairwise similarity verification using a publicly available Kaggle dataset.

## Objective

Develop a computer-vision pipeline that represents saree images as compact feature embeddings and retrieves visually similar patterns using cosine similarity. Colour-focused augmentation is used to reduce reliance on colour and encourage attention to pattern structure.

**Important:** The current evaluation is category-level. It does not prove exact same-design recognition across different colourways.

## Dataset

- **Name:** Indian Saree Patterns
- **Source:** [Kaggle — Indian Saree Patterns](https://www.kaggle.com/datasets/div456/indian-saree-patterns)
- **Images detected:** 1,468 readable images
- **Data split:** 1,293 training, 115 validation, 60 test images
- **Categories:** Banarasi, Bandhani, Ikat, Pichwai

Download the dataset from Kaggle and configure the dataset path in the notebook. Check the dataset licence and terms before redistribution.

## Methodology

- **Backbone:** Pretrained EfficientNet-B0
- **Embedding:** 256-dimensional, L2-normalised vector
- **Classifier:** Four-category classification head
- **Loss:** Cross-entropy with label smoothing
- **Optimiser:** AdamW with learning-rate scheduling and early stopping
- **Augmentation:** Colour jitter, hue/saturation changes, grayscale and spatial transformations
- **Similarity:** Cosine similarity
- **Evaluation:** Classification accuracy, Recall@K, mean Average Precision (mAP), verification ROC-AUC and Equal Error Rate (EER)

## Results

Results recorded from the executed notebook:

| Metric | Result |
|---|---:|
| Best validation accuracy | 95.65% |
| Test classification accuracy | 91.67% |
| Recall@1 | 85.00% |
| Recall@3 | 95.00% |
| Recall@5 | 97.50% |
| mAP | 89.49% |
| Verification ROC-AUC | 0.9502 |
| Verification EER | 0.1050 |
| Trainable parameters | 4.40 million |
| Embedding size | 256 dimensions |
| Single-image CPU latency | Approximately 43.19 ms |

**Interpretation:** Retrieval and verification metrics are based on pattern categories, not verified design identities. The test set contains only 60 images, so results should be interpreted cautiously.

## How to Run

1. Create a Python environment.
2. Install the required dependencies.
3. Download the dataset from Kaggle.
4. Update the dataset root path in the notebook.
5. Execute the notebook cells in order.

The notebook uses PyTorch, torchvision, timm, scikit-learn, pandas, NumPy, Matplotlib, Pillow and tqdm. Pin compatible package versions for reproducibility.

## Limitations and Future Improvements

- Collect identity-level labels linking the same design across different colourways.
- Separate training and gallery/query sets by design identity to prevent data leakage.
- Evaluate exact-design retrieval separately from category classification.
- Test on a larger and more diverse dataset.
- Benchmark inference speed on the intended deployment hardware.

## Disclaimer

This repository presents an independent computer-vision portfolio project using a public dataset. 
