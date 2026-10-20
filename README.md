# Crop Disease Identification Using Image Analytics and Deep Learning in R

## Project Overview

Crop diseases can significantly affect plant health and agricultural productivity. Identifying disease-related patterns in plant leaves is an important step toward developing data-driven agricultural solutions.

This project explores **crop disease identification using image analytics and machine learning in R**. It analyzes plant leaf images, extracts numerical colour-based features, explores disease-class distributions, and compares machine learning models to understand their ability to classify different plant leaf categories.

The project focuses on the complete data science workflow, from dataset exploration and feature engineering to model evaluation and visualization.

## Objectives

- Analyze a plant leaf disease image dataset.
- Explore the distribution of images across different classes.
- Extract numerical features from plant leaf images.
- Perform exploratory data analysis and statistical analysis.
- Train and compare Random Forest and Decision Tree classifiers.
- Evaluate model performance using accuracy, precision, recall, and F1-score.
- Visualize class distributions, feature importance, and model comparisons.
- Identify limitations and opportunities for future improvement.

## Dataset

**Dataset name:** Plant Leaf Diseases Dataset Without Augmentation

**Source:** [Mendeley Data – Plant Leaf Diseases Dataset](https://data.mendeley.com/datasets/tywbtsjrjv/1)

**Dataset file:** `Plant_leaf_diseases_dataset_without_augmentation.zip`

The dataset contains plant leaf images organized into different categories. The project uses image-derived numerical features for classification and analysis.

| Dataset Information | Details |
|---|---|
| Total images | 55,448 |
| Training images | 38,797 |
| Validation images | 8,300 |
| Testing images | 8,351 |
| Training proportion | 69.97% |
| Validation proportion | 14.97% |
| Testing proportion | 15.06% |

The dataset is divided into training, validation, and testing subsets for model development and evaluation.

## Technologies Used

- **Programming language:** R
- **Data analysis:** Data preprocessing, exploratory data analysis, and statistical analysis
- **Image analytics:** Colour-based feature extraction
- **Machine learning:** Random Forest and Decision Tree
- **Evaluation metrics:** Accuracy, precision, recall, and F1-score
- **Visualization:** Class distribution charts, feature importance plots, and accuracy comparison charts

## Methodology

### 1. Data Collection

The plant leaf image dataset was obtained from Mendeley Data. The images were organized into categories corresponding to different plant or disease classes.

### 2. Data Preprocessing

The dataset was inspected to identify available images and class labels. Image processing was performed to extract numerical information suitable for machine learning.

### 3. Exploratory Data Analysis

The class distribution was examined to understand differences in the number of images available for each category. Visualizations were generated to identify class imbalance and variations in dataset representation.

### 4. Image Feature Extraction

Numerical features were extracted from the images to represent their colour characteristics.

The features include:

- `red_mean`, `green_mean`, and `blue_mean`
- `red_sd`, `green_sd`, and `blue_sd`
- `red_q25`, `green_q25`, and `blue_q25`
- `red_q75`, `green_q75`, and `blue_q75`
- `green_ratio` and `brown_ratio`
- `dark_ratio`
- `color_entropy`

These features summarize aspects of colour distribution and variation. They provide a compact representation of the images for the machine learning models.

### 5. Model Development

Two supervised machine learning algorithms were implemented.

**Random Forest:** An ensemble learning algorithm that combines multiple decision trees to produce a classification result. It was used to examine the effectiveness of combining several trees when classifying image-derived features.

**Decision Tree:** A tree-based classification algorithm that learns decision rules from the extracted features. It was included as a comparison model because of its straightforward structure and interpretability.

### 6. Model Evaluation

The models were compared using test-set accuracy, precision, recall, and F1-score. Feature importance was also examined for the Random Forest model to understand which numerical features contributed most to its classification decisions.

## Experimental Results

The following values were obtained from the project's model comparison results.

| Evaluation Metric | Random Forest | Decision Tree |
|---|---:|---:|
| Test accuracy | 77.68% | 30.52% |
| Precision | 75.46% | 10.01% |
| Recall | 68.99% | 14.93% |
| F1-score | 70.69% | 10.61% |

### Results Discussion

The Random Forest model achieved a test accuracy of **77.68%**, outperforming the Decision Tree model, which achieved **30.52%**. The results indicate that Random Forest performed better on this dataset when using the extracted numerical image features.

The precision, recall, and F1-score values provide additional information about classification performance beyond accuracy alone. The comparatively low scores for the Decision Tree model suggest that its predictions were less effective under the current experimental setup.

These results also show that the choice of features and classification algorithm can influence the performance of an image-based classification system.

## Feature Importance Analysis

The Random Forest feature-importance visualization highlighted the following features among the most important:

- `green_ratio`
- `brown_ratio`
- `blue_sd`
- `blue_q25`
- `blue_mean`
- `red_sd`
- `color_entropy`
- `dark_ratio`
- `green_sd`

These features describe different aspects of the images' colour distributions. Their importance scores indicate how the model used the extracted variables during classification. They do not, by themselves, establish that a particular feature is a biological cause of disease.

## Project Visualizations

The project generates visual outputs to support interpretation of the results.

Suggested screenshots to include in this repository:

| Visualization | Suggested Filename |
|---|---|
| Disease class distribution | `class_distribution.png` |
| Random Forest feature importance | `feature_importance.png` |
| Test accuracy comparison | `model_accuracy_comparison.png` |

Create a folder named `results` and place your actual generated images inside it. Then display them in this README using the following Markdown:

### Class Distribution

![Plant leaf disease class distribution](results/class_distribution.png)

### Random Forest Feature Importance

![Random Forest feature importance](results/feature_importance.png)

### Model Accuracy Comparison

![Model accuracy comparison](results/model_accuracy_comparison.png)

Make sure the filenames match the actual image files generated by your R script.

## How to Run the Project

### Prerequisites

Install the following software:

- R
- RStudio (recommended)

Install the packages required by your script. For example, if your code uses these packages:

```r
install.packages(c(
  "randomForest",
  "rpart",
  "ggplot2",
  "dplyr",
  "caret",
  "readr",
  "png",
  "jpeg"
))
```

Install only the packages used by your actual script. If your code uses additional image-processing packages, install those separately.

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

### Step 2: Open the Project

Open the downloaded project folder in RStudio.

### Step 3: Configure the Dataset Path

Update the dataset path in the R script to point to the downloaded ZIP file or the extracted dataset directory, depending on how the script loads the images.

Example Windows path:

```r
zip_path <- "C:/Users/YourUsername/Downloads/Plant_leaf_diseases_dataset_without_augmentation.zip"
```

Replace `YourUsername` with your Windows username.

### Step 4: Run the R Script

Open the main R script and execute the code from beginning to end.

The script should process the dataset, extract image features, train the models, evaluate their performance, and generate the configured result files.

## Limitations

The current implementation relies on extracted numerical image features rather than an end-to-end deep learning architecture trained directly on image pixels. Colour-based features may not capture all the visual patterns associated with plant diseases.

The reported results apply to the evaluated dataset and experimental setup. They do not guarantee the same performance on photographs collected in real agricultural fields, where lighting, backgrounds, camera quality, and plant conditions may differ.

The current evaluation does not establish that the model can identify every individual disease, including *Sclerotium oryzae*, unless that disease is represented in the dataset and has been specifically evaluated.

## Future Enhancements

Future work could explore:

- Transfer learning using MobileNet, ResNet, or EfficientNet.
- More comprehensive image features, including texture and shape.
- Class-balancing techniques where appropriate.
- Hyperparameter tuning and cross-validation.
- Per-class precision, recall, F1-scores, and confusion-matrix analysis.
- Evaluation using independent field images.
- A simple web interface for uploading leaf images and viewing model outputs.

These improvements could help determine whether more advanced approaches provide better generalization and more reliable performance.

## Conclusion

This project demonstrates an end-to-end data science workflow for plant leaf disease classification using R, image analytics, and machine learning. It combines dataset exploration, numerical feature extraction, model development, performance evaluation, and visualization in a single analytical study.

The Random Forest model outperformed the Decision Tree model in the reported experiment. The comparison provided practical experience in evaluating classification algorithms and interpreting feature importance. Further research and field validation are necessary before using the system to support real agricultural decisions.

## References

1. Mendeley Data, *Plant Leaf Diseases Dataset*. Available: https://data.mendeley.com/datasets/tywbtsjrjv/1
2. L. Breiman, “Random Forests,” *Machine Learning*, vol. 45, pp. 5–32, 2001.
3. L. Breiman, J. H. Friedman, R. A. Olshen, and C. J. Stone, *Classification and Regression Trees*. Monterey, CA, USA: Wadsworth, 1984.
4. R Core Team, *R: A Language and Environment for Statistical Computing*. Vienna, Austria: R Foundation for Statistical Computing. Available: https://www.R-project.org/

---

**Author:** Mannuru Mahesh

**Project:** Crop Disease Identification Using Image Analytics and Deep Learning in R

**Domain:** Data Science, Machine Learning, Image Analytics, and Agricultural Technology


