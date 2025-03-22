# bttai-MIT_AJL_Team-16

### **👥 Team Members**

| Name | GitHub Handle | Contribution |
| ----- | ----- | ----- |
| Lee Mabhena | @leemabhena | Built more accurate model for submission |
| Shahadah Manzer | @shahadah-manzer | Project Manager, tested with EffctiveB0 and B2 models |
| Ha Lihn Nguyen | @halinhnguyen28 | Tested with CNN model |

---

## **🎯 Project Highlights**

* Built a transfer learning model using keras applications and Xception to solve the goal of building an AI model to classify skin conditions across diverse skin tones.
* Achieved an F1 score of 0.481 and a ranking of #23 on the final Kaggle Leaderboard
* Used \[explainability tool\] to interpret model decisions
* Implemented \[data preprocessing method\] to optimize results within compute constraints

🔗 [Equitable AI for Dermatology | Kaggle Competition Page](https://www.kaggle.com/competitions/bttai-ajl-2025/overview)
🔗 [WiDS Datathon 2025 | Kaggle Competition Page](https://www.kaggle.com/competitions/widsdatathon2025/overview)

---

## **⚙️ Setup & Execution:**
  * Clone repositiory by: git clone https://github.com/<your-repository-link>.git
  * Dowload dataset from Kaggle Competition, place in Google Drive directory
  * Dowload Colab File
  * Run file to produce output.csv file

---

## **🌍 Project Overview:**

  Break through tech AI Spring 2025 AI studio. Equitable AI for Dermatology.  
  Build an ML model to classify skin conditions across diverse skin tones.
  Advance equity by centering those historically excluded in AI.


---

## **📊 Data Exploration**

Data contains main features of, provided by Kaggle Competition Description:
  * md5hash	(Object)	-- file name of an image without .jpg
  * fitzpatrick_scale	(int64) -- Integer in the range [-1, 0) and [1, 6] indicating self-described FST
  * fitzpatrick_centaur	(int64)	-- Integer in the range [-1, 0) and [1, 6] indicating FST assigned by Centaur Labs
  * label	Object (String) -- indicating medical diagnosis; the target for this competition
  * nine_partition_label	(Object) --	String indicating one of nine diagnostic categories
  * three_partition_label	(Object) -- String indicating one of three diagnostic categories
  * qc	(Object) -- Quality control check by a Board-certified dermatologist.
  * ddi_scale	(int64)	-- A column used to reconcile this dataset with another dataset
    
  🧐 Process and Challenges: 
    - Preprocessing included removing possible null values, differentiating/limiting image sizes, and limiting a batch, epoch, and seed size for later data training. 
    - Challenges included understanding the medical labela nd their role in dataset, highlighting md5hash label for output file.  

---

## **🧠 Model Development**

After testing a variety of models based on image classification and recognition. Some models included:
  - Efficient B2
  - Efficient B0
  - ResNet50
  - CNN
  - and more...

🤖 Model Used
We used Xception, a powerful CNN pre-trained on ImageNet, for transfer learning. We fine-tuned the final layers for specific skin condition classification task.

🎯 Feature Selection & Hyperparameter Tuning

Used global average pooling to condense feature maps into meaningful representations.
Applied rescaling to normalize pixel values from (0,255) to (-1,1) for compatibility with Xception.
Experimented with dropout layers to prevent overfitting (final model excluded it for better generalization).
Adjusted the learning rate and batch size to optimize performance.

🏋️ Training Setup
Data Split: Used 80% of images for training and 20% for validation.
Evaluation Metric: Measured performance using accuracy, precision, recall, and F1-score.
Baseline Performance: Compared against a simpler CNN model, with Xception significantly improving classification accuracy.

---

## **📈 Results & Key Findings**

* Performance metrics: Score Accuracy of 0.481 leading to #23 on the Kaggle Competion
* Overall Performance: While the model effectively classified some common skin conditions, performance varied across different categories.
                       Challenges in distinguishing similar conditions.
* Model seemd to perform better on lighter tone compared to darker skin tone, thus emphasizing the inhernet bias in technology. 

---

## **🖼️ Impact Narrative**

**Answer the relevant questions below based on your competition:**

**AJL challenge:**

As Dr. Randi mentioned in her challenge overview, “Through poetry, art, and storytelling, you can reach others who might not know enough to understand what’s happening with the machine learning model or data visualizations, but might still be heavily impacted by this kind of work.”
As you answer the questions below, consider using not only text, but also illustrations, annotated visualizations, poetry, or other creative techniques to make your work accessible to a wider audience.
Check out [this guide](https://drive.google.com/file/d/1kYKaVNR\_l7Abx2kebs3AdDi6TlPviC3q/view) from the Algorithmic Justice League for inspiration!

1. What steps did you take to address Xception Fairness (https://haas.berkeley.edu/wp-content/uploads/What-is-fairness_-EGAL2.pdf)?

 ✅ Things done or taken into account to model fairness included: 
     * Using a Validation Set, that included a range of skin tones.
     * Reweighting Loss Function, adjusting penalities for misclassification

2. What broader impact could your work have?

By ensuring AI works well across all skin tones, we take a step toward reducing racial disparities in medical diagnoses, which can have larger impacts in telemedicne, medical technology/devices, and braodly medical AI fields.

---

## **🚀 Next Steps & Future Improvements**

* Improve the dataset with even more diverse images 📸
* Explore new models for better performance that can be used on larger CPU
