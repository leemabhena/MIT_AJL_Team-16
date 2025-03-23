# MIT AJL Team 16

👥 **Team Members**

| Name             | GitHub Handle       | Contribution                                               |
|------------------|-----------------------|------------------------------------------------------------|
| Lee Mabhena      | @leemabhena         | Built more accurate model for submission                  |
| Shahadah Manzer  | @shahadah-manzer     | Project Manager, tested with EfficientB0/B2 models         |
| Ha Linh Nguyen   | @halinhnguyen28     | Tested with CNN model                                      |

## 🎯 **Project Highlights**

* Developed a **transfer learning** pipeline using **Keras** and **Xception** to classify 21 skin conditions across diverse skin tones.
* Achieved a **weighted F1 score of 0.59045** and ranked **#16** on the final Kaggle Leaderboard.
* Incorporated preliminary **fairness considerations** (e.g., balanced sampling, targeted data augmentation) to address performance discrepancies across skin tones.
* Implemented **explainability** techniques (e.g., Grad-CAM) to interpret model decisions and visualize important regions.
* Employed **data preprocessing** (rescaling, image resizing, minimal quality filtering) to maximize performance within constrained compute resources.

**Key Links**

* [Equitable AI for Dermatology | Kaggle Competition](https://www.kaggle.com/competitions/equitable-ai-for-dermatology)
* [WiDS Datathon 2025 | Kaggle Competition](https://www.kaggle.com/competitions/equitable-ai-for-dermatology)

## ⚙️ **Setup & Execution**

1.  Clone this repository:

    ```bash
    git clone https://github.com/leemabhena/MIT_AJL_Team-16.git
    cd MIT_AJL_Team-16
    ```

2.  Download the dataset from the Kaggle competition page and place it in your working directory (e.g., in your Google Drive if you plan to train in Google Colab).
3.  Open the Colab notebook (`mit-ajl-team-16.ipynb`).
4.  Update paths in the notebook to point to where your dataset is stored.
5.  Install dependencies (the notebook will typically install needed packages such as `tensorflow`, `keras`, etc.).
6.  Run the notebook. Model training will produce logs and a final `submission.csv` file containing predictions for the test set.
7.  Submit `submission.csv` to the Kaggle competition to see your score on the leaderboard.

**Reproducibility Note:**

We set consistent random seeds in the notebook to reduce variation between runs, but small discrepancies may occur due to GPU hardware differences.

## 🌍 **Project Overview**

This project is part of the **Break Through Tech (BTT) AI Studio 2025** in collaboration with the **Algorithmic Justice League (AJL)**. The central challenge is to build an **AI-driven dermatology model** that:

* Classifies 21 different skin conditions from provided images.
* Performs **equitably** across **diverse skin tones**, mitigating potential biases that adversely affect historically marginalized communities in healthcare.

**Real-World Significance:**

AI models in healthcare, particularly in dermatology, have been known to **underperform on darker skin tones** due to non-representative training data.

Our aim is to **reduce such disparities** by ensuring the model performs well across the broad spectrum of skin tones, ultimately informing better diagnostic tools.

📊 **Data Exploration**

The competition dataset includes image metadata and labels for each image. Key columns:

* `md5hash` (str): Unique identifier for each image (used when generating final submissions).
* `fitzpatrick_scale` (int): Self-reported Fitzpatrick Skin Type (FST), ranging [1..6] (also includes -1, 0 for missing).
* `fitzpatrick_centaur` (int): FST assigned by Centaur Labs.
* `label` (str): The specific dermatological condition (21 possible classes).
* `nine_partition_label` (str): A coarse categorization into 9 groups.
* `three_partition_label` (str): An even broader categorization (3 groups).
* `qc` (str): Quality control indicator from a board-certified dermatologist.
* `ddi_scale` (int): Reconciliation column with an external dataset.

**Data Preparation & Preprocessing**

* **Filtering**
    * Removed rows with invalid or missing `md5hash` or `label`.
    * Paid special attention to `qc` flags (although we ended up including almost all images that were at least of minimal quality).
* **Image Processing**
    * Resized images to a fixed shape (e.g., 224x224) to align with standard Keras model input.
    * Normalized pixel intensity values from [0..255] to [-1..1] for Xception compatibility.
* **Balancing**
    * Applied targeted **data augmentation** (e.g., random rotations, flips) for underrepresented classes or underrepresented skin tones to help address class imbalances.
* **Train-Validation Split**
    * Split the data 80%/20% (train/validation) while ensuring representation of various skin tones and conditions in both sets.

These steps helped ensure that our training pipeline was robust, consistent, and mindful of **equitable representation**.

## 🧠 **Model Development**

We experimented with multiple CNN-based architectures, including:

* EfficientNet B2 / EfficientNet B0
* ResNet50
* Custom CNN from scratch
* Xception (final choice)

**Why Xception?**

* Xception (Extreme Inception) is known for **depthwise separable convolutions**, making it both performant and efficient.
* Pretrained on ImageNet, providing a strong feature extractor base for transfer learning.

**Training Setup & Hyperparameter Tuning**

* **Transfer Learning Approach**
    * Froze most initial layers to retain ImageNet representations.
    * Unfroze final blocks for domain-specific fine-tuning on dermatology images.
* **Loss Function & Optimizer**
    * Used `categorical_crossentropy` for multi-class classification.
    * Chose `Adam` with a lower learning rate (e.g., 1e-4) to stabilize training.
* **Batch Size**
    * Experimented with 16, 32, and 64. Settled on **batch size of 32** for an optimal speed-to-accuracy ratio.
* **Data Augmentation**
    * Varied transformations (rotation, flips, zoom) to simulate realistic variations.
* **Model Monitoring**
    * Monitored `val_loss` and `val_accuracy` for early stopping to avoid overfitting.

**Final Architecture:**

`Input Layer` -> `Xception Base` (frozen initial layers) -> `GlobalAveragePooling2D` -> `Dense(21, activation='softmax')`

## 📈 **Results & Key Findings**

* Validation Accuracy stabilized around ~48% with a corresponding **weighted F1 score** of ~0.59 on the held-out validation set.
* On the competition’s **public leaderboard**, we achieved an F1 score of **0.59045**, placing us at **#16** near the end of the challenge.

**Performance Analysis**

* **Stronger performance** on more common skin conditions (e.g., acne-vulgaris) and on images with lighter skin tones.
* **Weaker performance** on certain rarer conditions and images with darker skin tones – revealing potential underlying **dataset bias** that we partially mitigated but did not fully overcome.

**Key Insight:** The variability in image quality, distribution of Fitzpatrick skin types, and condition similarity posed classification challenges. Future steps include obtaining more **representative data** and employing **fairness-driven data augmentation** or rebalancing.

## 🖼️ **Impact Narrative (AJL)**

In line with the Algorithmic Justice League’s mission to combine **art, research, and advocacy**, we asked ourselves:

1.  **Steps Taken to Address Model Fairness**
    * Balanced Sampling: We intentionally sampled more heavily from underrepresented classes and darker skin tones for each batch.
    * Penalized Misclassification: Considered using a higher loss penalty on misclassifications of darker skin tones (though we only partially implemented this due to time constraints).
    * Visual Explanations (Grad-CAM): Helped identify whether the model was focusing on spurious background features vs. the actual lesion, potentially uncovering biases.

    In poetic form, we might say:

    "Through every hue and tone,
    A story, a lesion, a life—
    Not just data alone.”

2. **Broader Impact**
* Reducing Healthcare Disparities: By validating on diverse Fitzpatrick scales, our work can help close diagnostic gaps.
* Empowering Telemedicine: Equitable AI-based image classification could improve dermatological care in remote, underserved areas, especially for individuals with limited access to specialists.
* Advocating for Transparency: Sharing model explanations fosters trust and encourages open dialogue about AI's potential risks and benefits for marginalized communities.

## 🚀 **Next Steps & Future Improvements**

* **Expand Dataset**
    * Acquire or curate additional images reflecting broader demographic representation (skin tones, geographies, conditions).
* **Advanced Fairness Techniques**
    * Integrate specialized libraries (e.g., Fairlearn, Aequitas) for systematic fairness metrics.
    * Implement advanced weighting or re-sampling strategies to ensure equitable performance across subgroups.
* **Stronger Data Augmentation**
    * Incorporate domain-specific augmentations, such as realistic lesion transformations, lighting variations, and synthetic data generation (e.g., GANs).
* **Hyperparameter Optimization**
    * Automate with tools like Optuna or Keras Tuner to systematically search learning rates, batch sizes, and deeper layer unfreezing strategies.
* **Model Interpretability**
    * Use LIME or SHAP for more granular, per-pixel or per-feature interpretability and to highlight potential model biases in real time.

By continuing to refine these approaches, we hope to make dermatology-focused AI models ever more transparent, equitable, and clinically robust.

Thank you for exploring our project!
