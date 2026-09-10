# Deepfake Detection Application

A Streamlit web application that classifies images as **Real** or **Fake** using a trained TensorFlow/Keras convolutional neural network (CNN).

The application lets users explore the dataset, review evaluation outputs, inspect sample predictions, and upload an image for classification.

## Demo

Watch the application demonstration:

https://github.com/user-attachments/assets/b3e73751-1eb5-4d2f-a250-cc09fc999a8f

## Features

- Upload a JPG, JPEG, or PNG image for deepfake classification.
- View predicted class and confidence score.
- Explore training, validation, and test dataset statistics.
- Display real and fake image samples from each dataset split.
- View a confusion matrix and classification report.
- Inspect predictions from test-set images.

## Technology Stack

- **Python**
- **Streamlit** for the web interface
- **TensorFlow / Keras** for the CNN model and inference
- **NumPy**, **scikit-learn**, **Matplotlib**, and **Seaborn** for evaluation and visualization
- **Pillow** and **OpenCV** for image processing utilities

> This repository currently uses TensorFlow/Keras for deep learning. PySpark is not part of the implemented application.

## Project Structure

```text
Deepfake-Detection-Application/
├── app.py                              # Streamlit application entry point
├── helper.py                           # Model loading, preprocessing, and metrics helpers
├── fake_real_image_classifier_cnn.h5   # Trained CNN model
├── evaluation_results.npz              # Saved evaluation labels and predictions
├── requirements.txt                    # Python dependencies
├── trim_dataset.py                     # Utility to create a reduced dataset sample
├── Ai_Project.ipynb                    # Model training and experimentation notebook
├── Milestone1.ipynb                    # Exploratory data analysis notebook
└── Trimmed Dataset/
    ├── Train/
    │   ├── Fake/
    │   └── Real/
    ├── Validation/
    │   ├── Fake/
    │   └── Real/
    └── Test/
        ├── Fake/
        └── Real/
```

## Requirements

- Python 3.10 or newer
- pip
- Git (optional, for cloning the repository)

## Installation

Clone the repository and open its folder:

```powershell
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
cd Deepfake-Detection-Application
```

Create and activate a virtual environment:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Install dependencies:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Run the Application

From the project root, with the virtual environment activated, run:

```powershell
streamlit run app.py
```

Streamlit will start a local server, normally available at:

```text
http://localhost:8501
```

Stop the application with `Ctrl + C`.

## Using the Application

The interface has four sections:

1. **Dataset Viewer** — Shows the number of images in each split and example images by class.
2. **Model Evaluation** — Displays the saved confusion matrix and classification report.
3. **Classified Samples** — Shows model predictions for a batch of test images.
4. **Upload and Predict** — Lets you upload an image and receive a Real/Fake prediction with confidence.

## Dataset Format

The application expects the following folder layout:

```text
Trimmed Dataset/
├── Train/
│   ├── Fake/
│   └── Real/
├── Validation/
│   ├── Fake/
│   └── Real/
└── Test/
    ├── Fake/
    └── Real/
```

Images are resized to **128 × 128 pixels** and normalized to a pixel range of **0–1** before inference.

## Model Output

The model returns a binary score using a threshold of `0.5`:

- Score above `0.5` → **Real**
- Score at or below `0.5` → **Fake**

The reported confidence is the model score for the selected class. It should be interpreted as a model estimate, not proof that an image is authentic or manipulated.

## Important Notes

- The model is intended for academic and demonstration use.
- Deepfake detection results can be affected by image quality, compression, unseen generation methods, and dataset bias.
- `evaluation_results.npz` contains saved evaluation outputs. If the test dataset or model changes, regenerate this file before relying on the displayed metrics.
- The trained model and dataset can make the repository large. Consider using Git LFS or hosting the dataset/model separately if GitHub upload limits are reached.

## Security

Never commit credentials, tokens, passwords, or private keys. The included `.gitignore` excludes common local environment and credential files such as `.env`, `*.pem`, and `*.key`.

## License

No license has been specified for this project. Add a license file before distributing or reusing the code publicly.
