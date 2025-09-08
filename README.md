# **Comparative Analysis of ANN and CNN Models for Leaf Pest Detection on Vegetable Images**  

## 📱 About the Project  
This project aims to develop and compare artificial neural network (ANN) and convolutional neural network (CNN) models to classify images of vegetable leaves as either affected by pests or not. The goal is to build models that can accurately detect pest infestation from images, utilizing a dataset of leaf images with and without pests. The task focuses on binary classification to support agricultural pest management.  

---  

## 🎙 Dataset  
- **Source:**  
  - Image dataset of leaves with two categories: "With Pest" and "Without Pest" 
  - Dataset subdivided into training and validation sets, with image counts ranging from 199 to 800 per set depending on experiments.
    
---  

## 📂 Data Preparation  
- Image resizing to either 64x64 or 128x128 pixels depending on model  
- Rescaling pixel values to [0, 1] range  
- Data augmentation techniques applied during training including shear, zoom, and horizontal flips (for some experiments)  
- Dataset splitting into training, validation, and testing subsets (80:20 for train-test split, and 10% validation during training in some models)
    
---  

## 📊 Model Architectures  
### ANN Model  
- Conv2D layer with 32 filters (3x3), ReLU activation  
- MaxPooling2D with pool size (2x2)  
- Flatten layer  
- Dense layer with 128 neurons, ReLU activation  
- Dropout 50%  
- Output Dense layer with 1 neuron, sigmoid activation (binary classification)  

### CNN Model  
- Conv2D layers: first with 32 filters (3x3), then 64 filters (3x3), each followed by MaxPooling2D (2x2)  
- Flatten layer  
- Dense layers: 128 and 64 neurons with ReLU activations, each followed by Dropout 50%  
- Output Dense layer with 2 neurons, sigmoid activation (binary classes)  

### Transfer Learning Model  
- MobileNetV2 pretrained on ImageNet used as feature extractor with fixed weights  
- Input resized from 128x128 to 224x224  
- Dense output layer adapted for 2-class classification
  
---  

## 🖥 Programming Languages & Libraries  
![Python](https://img.shields.io/badge/-Python-3776AB?style=flat&logo=python&logoColor=white)  
![TensorFlow](https://img.shields.io/badge/-TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)  
![Keras](https://img.shields.io/badge/-Keras-D00000?style=flat&logo=keras&logoColor=white)  
![OpenCV](https://img.shields.io/badge/-OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white)  
![Matplotlib](https://img.shields.io/badge/-Matplotlib-11557C?style=flat&logo=python&logoColor=white)  

---  

## 📚 Preprocessing Stages  
1. Loading images from directories based on pest presence  
2. Labeling: 1 for pest, 0 for no pest  
3. Resizing images to 64x64 or 128x128 pixels  
4. Normalizing pixel values  
5. Splitting into training and test sets (80:20)  
6. Data augmentation applied for some training sets  
7. Conversion to numpy arrays for model input
   
---  

## 📈 Model Performance Summary  

| Model Type        | Input Size | Epochs | Test Accuracy (%) | Notes                                   |  
|-------------------|------------|--------|-------------------|-----------------------------------------|  
| ANN (Simple)      | 64x64      | 5      | ~50               | Poor learning, accuracy near chance level |  
| CNN               | 128x128    | 15     | ~91               | Good performance with dropout regularization |  
| Transfer Learning (MobileNetV2) | 128x128 (resized to 224x224) | 15     | ~98               | Best accuracy with pretrained features |  

**Conclusions:**  
- The simple ANN model failed to learn effectively, indicated by unstable loss and near 50% accuracy.  
- The CNN model significantly improved accuracy to approximately 91%, showing benefit from convolutional architecture and deeper layers.  
- Transfer learning using MobileNetV2 pretrained on ImageNet achieved the highest accuracy (~98%), indicating strong feature extraction even without fine-tuning.
  
---  

## 🎯 Summary  
- Dataset of vegetable leaf images categorized by pest presence was prepared with normalization and augmentation.  
- Several neural network architectures were tested, with CNN and pretrained MobileNetV2 offering effective solutions.  
- The project demonstrates the advantage of advanced architectures and transfer learning in agricultural image classification tasks.  
