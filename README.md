# Mask Detection Model

This project implements a deep learning model for detecting whether a person is wearing a mask correctly, incorrectly, or not wearing a mask at all. The model leverages transfer learning using the MobileNetV2 architecture and is trained on a dataset containing images of people with and without masks.

## Table of Contents
- [Project Overview](#project-overview)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Model Details](#model-details)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

The objective of this project is to create a reliable model that can classify images into three categories:
1. **With Mask**: The person in the image is wearing a mask correctly.
2. **Without Mask**: The person in the image is not wearing a mask.
3. **Mask Worn Incorrectly**: The person in the image is wearing a mask but not correctly.

The model is based on the MobileNetV2 architecture, which is pre-trained on the ImageNet dataset. The pre-trained base model is fine-tuned with the new dataset specific to the mask detection task.

## Installation

To run this project locally, follow these steps:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/mask-detection.git
    cd mask-detection
    ```

2. **Install the required dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Download the dataset**:
    The dataset used in this project should be organized into the following structure:
    ```
    data/
    ├── with_mask/
    ├── without_mask/
    └── mask_weared_incorrect/
    ```

4. **Run the notebook**:
    Open the Jupyter notebook and execute the cells step-by-step:
    ```bash
    jupyter notebook notebooks/mask_detection_model.ipynb
    ```

## Usage

1. **Data Preprocessing**: 
    The images are first resized to 128x128 pixels and normalized. The `ImageDataGenerator` is used for data augmentation, which helps improve the model's generalization.

2. **Model Training**: 
    The MobileNetV2 model is fine-tuned on the mask dataset. The model is trained using categorical cross-entropy loss and Adam optimizer. The training is carried out for 10 epochs with a batch size of 32.

3. **Model Evaluation**: 
    After training, the model's performance is evaluated on the validation set. Accuracy and loss are tracked during training to monitor the model's progress.

## Project Structure

```plaintext
/mask-detection
│
├── data/                  # Folder for storing datasets (images)
│   ├── with_mask/
│   ├── without_mask/
│   └── mask_weared_incorrect/
│
├── notebooks/             # Jupyter Notebooks
│   └── mask_detection_model.ipynb
│
├── src/                   # Source code
│   ├── data_preprocessing.py  # Functions for data loading and preprocessing
│   ├── model.py               # Model architecture and training code
│   ├── utils.py               # Utility functions (e.g., visualization, error handling)
│   └── evaluate.py            # Model evaluation scripts
│
├── requirements.txt       # Required libraries and dependencies
├── README.md              # Documentation for your project
├── LICENSE                # License for your project
└── .gitignore             # Files and directories to ignore in version control
```

## Model Details

The model is built using the following architecture:
- **Base Model**: MobileNetV2 pre-trained on ImageNet, with the top layers removed.
- **Custom Layers**: 
  - Global Average Pooling layer.
  - Dense layer with ReLU activation.
  - Output Dense layer with softmax activation for three classes.

### Training Configuration:
- **Optimizer**: Adam
- **Loss Function**: Categorical Crossentropy
- **Metrics**: Accuracy
- **Epochs**: 10
- **Batch Size**: 32

## Results

The model achieved satisfactory accuracy on the validation set, with training and validation accuracy being tracked over the epochs. Further fine-tuning and hyperparameter optimization can enhance the model's performance.

## Contributing

Contributions are welcome! Please open an issue first to discuss what you would like to change. You can also fork the repository and submit a pull request. Please make sure to follow the [contributing guidelines](CONTRIBUTING.md).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
