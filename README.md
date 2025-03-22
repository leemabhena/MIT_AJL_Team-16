# bttai-MIT_AJL_Team-16

### **👥 Team Members**

| Name | GitHub Handle | Contribution |
| ----- | ----- | ----- |
| Lee Mabhena | @leemabhena | Built more accurate model for submission |
| Shahadah Manzer | @shahadah-manzer | Project Manager, tested with EffctiveB0 and B2 models |
| Ha Lihn Nguyen | @ | tested with CNN model |

---

## **🎯 Project Highlights**

* Built a transfer learning model using keras applications and Xception to solve the goal of building an AI model to classify skin conditions across diverse skin tones.
* Achieved an F1 score of 0.481 and a ranking of #23 on the final Kaggle Leaderboard
* Used \[explainability tool\] to interpret model decisions
* Implemented \[data preprocessing method\] to optimize results within compute constraints

🔗 [Equitable AI for Dermatology | Kaggle Competition Page](https://www.kaggle.com/competitions/bttai-ajl-2025/overview)
🔗 [WiDS Datathon 2025 | Kaggle Competition Page](https://www.kaggle.com/competitions/widsdatathon2025/overview)

---

## **⚙️ Setup & Execution: **
  * Clone repositiory by: git clone https://github.com/<your-repository-link>.git
  * Dowload dataset from Kaggle Competition, place in Google Drive directory
  * Dowload Colab File
  * Run file to produce output.csv file

---

## **🌍 Project Overview: **

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
    - Preprocessing included removing possible null values, differentiating/limiting image sizes, and limiting a batch, epoch, and seed       size for later data training. 
    - Challenges included understanding the medical labela nd their role in dataset, highlighting md5hash label for output file.  

---

## **🧠 Model Development**

**Describe (as applicable):**

🤖 After testing a variety of models based on image classification and recognition. Some models included:
  - Efficient B2
  - Efficient B0
  - ResNet50
  - CNN
  - and more...

We found that using an Xception model 
* Model(s) used 
* Feature selection and Hyperparameter tuning strategies
* Training setup (e.g., % of data for training/validation, evaluation metric, baseline performance)

---

## **📈 Results & Key Findings**

**Describe (as applicable):**

* Performance metrics (e.g., Kaggle Leaderboard score, F1-score)
* How your model performed overall
* How your model performed across different skin tones (AJL)
* Insights from evaluating model fairness (AJL)

**Potential visualizations to include:**

* Confusion matrix, precision-recall curve, feature importance plot, prediction distribution, outputs from fairness or explainability tools

---

## **🖼️ Impact Narrative**

**Answer the relevant questions below based on your competition:**

**AJL challenge:**

As Dr. Randi mentioned in her challenge overview, “Through poetry, art, and storytelling, you can reach others who might not know enough to understand what’s happening with the machine learning model or data visualizations, but might still be heavily impacted by this kind of work.”
As you answer the questions below, consider using not only text, but also illustrations, annotated visualizations, poetry, or other creative techniques to make your work accessible to a wider audience.
Check out [this guide](https://drive.google.com/file/d/1kYKaVNR\_l7Abx2kebs3AdDi6TlPviC3q/view) from the Algorithmic Justice League for inspiration!

1. What steps did you take to address [model fairness](https://haas.berkeley.edu/wp-content/uploads/What-is-fairness_-EGAL2.pdf)? (e.g., leveraging data augmentation techniques to account for training dataset imbalances; using a validation set to assess model performance across different skin tones)
2. What broader impact could your work have?

---

## **🚀 Next Steps & Future Improvements**

**Address the following:**

* What are some of the limitations of your model?
* What would you do differently with more time/resources?
* What additional datasets or techniques would you explore?

---

## **📄 References & Additional Resources**

* Cite any relevant papers, articles, or tools used in your project
