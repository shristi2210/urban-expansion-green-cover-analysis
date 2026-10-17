# Urban Expansion and Green Cover Analysis 🌍

## About the Project

This project explores how satellite images can be used to identify different types of land cover and understand patterns related to urban expansion and green cover.

I used the EuroSAT dataset and applied transfer learning with MobileNetV2 to classify satellite images into three broader categories: Agriculture, Forest, and Urban.

The project also includes visualizations comparing green cover and urban land, along with a simple trend simulation to explore how these categories could change over time.

## Problem Statement

How can satellite image classification help identify agricultural, forest, and urban areas, and how can the resulting categories be used to explore land-cover patterns?

## Dataset

The project uses the EuroSAT land-use and land-cover satellite imagery dataset.

I grouped the original dataset classes into three categories:

- **Agriculture:** Annual Crop, Permanent Crop, Pasture, and Herbaceous Vegetation.
- **Forest:** Forest.
- **Urban:** Residential, Industrial, and Highway.

The images were resized to 160 × 160 pixels, normalized, and prepared for training. The final dataset contained 9,000 images, divided into 7,200 training images and 1,800 validation images.

## What I Worked On

### 1. Data Preparation

I organized the original satellite image classes into three broader categories and balanced the dataset by limiting each category to a maximum of 3,000 images.

### 2. Image Preprocessing and Augmentation

I used ImageDataGenerator to normalize pixel values and apply data augmentation techniques such as rotation, zoom, and horizontal flipping.

The dataset was divided into 80% training data and 20% validation data.

### 3. Transfer Learning with MobileNetV2

Instead of training a deep learning model entirely from scratch, I used MobileNetV2 with pretrained ImageNet weights as a feature extractor.

I added a custom classification head containing global average pooling, a dense layer, dropout, and a softmax output layer for the three land-cover categories.

### 4. Fine-Tuning

After the initial training, I unfroze the final 30 layers of the pretrained model and continued training with a smaller learning rate.

This allowed the model to adjust some of its pretrained features to the satellite image classification task.

### 5. Evaluation and Visualization

I explored the model's performance using training and validation accuracy, loss curves, a confusion matrix, and a distribution of predicted land-cover categories.

I also compared the predicted green-cover categories (Agriculture and Forest) with the Urban category.

### 6. Land-Cover Trend Simulation

I created a simple simulated trend in which green cover decreases and urban land increases over time. I then used Linear Regression to extend these simulated trends to 2025.

**Note:** This is a demonstration of trend modeling, not an actual measurement of historical urban expansion or a satellite-based forecast. The trend values are manually defined in the notebook.

## Model Results

The model was trained in two stages.

| Training stage | Validation accuracy |
|---|---:|
| Best initial training epoch | 92.00% |
| Final epoch after fine-tuning | 91.61% |

The initial training phase achieved the highest recorded validation accuracy of 92.00%. Fine-tuning did not improve on that peak in the recorded results.

These values represent validation accuracy on the prepared dataset, rather than proof that the model will achieve the same accuracy on every satellite imagery dataset.

## Technologies Used

- Python
- TensorFlow and Keras
- MobileNetV2
- NumPy
- Matplotlib and Seaborn
- scikit-learn
- Google Colab

## How to Run the Project

1. Open the notebook in Google Colab.
2. Enable GPU acceleration if available.
3. Upload the EuroSAT ZIP dataset when prompted.
4. Extract the dataset and run the preprocessing cells to create the three land-cover categories.
5. Run the data generator and MobileNetV2 model cells.
6. Train the model and run the evaluation and visualization cells.
7. Run the final trend simulation cells to reproduce the green-cover and urban-land plots.

The EuroSAT dataset is not included in this repository by default, so you will need to provide it before running the notebook. Check the ZIP filename used in the extraction cell and update it if necessary.

## What I Learned

This project helped me understand how transfer learning can be applied to satellite image classification without building an entire deep learning model from scratch.

I learned how to organize image datasets, apply data augmentation, fine-tune pretrained models, and evaluate classification performance using different visualizations.

I also explored how machine learning outputs can be used for further analysis, while understanding the difference between image classification results and actual evidence of changes in land cover over time.

## Limitations and Future Scope

The model classifies images into three broad categories, so it does not capture every type of land use in the original EuroSAT dataset.

The simulated green-cover and urban-expansion trends are not based on actual multi-year satellite observations. A more reliable study would use georeferenced satellite imagery from multiple years and measure changes in land cover directly.

In the future, I would like to work with multi-temporal satellite images, improve the model's generalization, and explore more rigorous methods for measuring urban expansion and green-cover loss.

---

This project was a hands-on learning experience in deep learning, transfer learning, satellite image classification, and environmental data analysis.
