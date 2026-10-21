# 🐶 Dog Detection with YOLOv8 — Just Dogs

## 📌 Overview

This project explores computer vision for dog detection as part of the Just Dogs project. It uses [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics), a real-time object detection model, to identify dogs in images and video footage.

The project aims to establish a foundation for a computer vision system that can support dog monitoring in a grooming salon. Future extensions may include tracking dogs across video frames, recognizing grooming activities, and helping verify services against billing records.

The current focus is on experimenting with YOLOv8, evaluating its detection performance, and identifying opportunities for further development.

## 🎯 Objectives

- Detect dogs in images using YOLOv8.
- Experiment with pretrained object detection models.
- Evaluate detection performance using standard metrics.
- Explore the potential for applying computer vision to grooming salon workflows.
- Establish a foundation for future dog tracking and activity recognition.

## 🛠️ Tech Stack

- **Language:** Python
- **Computer Vision:** Ultralytics YOLOv8
- **Dataset Preparation:** Roboflow
- **Deep Learning:** PyTorch (used by Ultralytics)
- **Development Environment:** Python virtual environment

## 📂 Project Structure

```text
YOLO/
├── datasets/
│   └── my_roboflow_data/
│       ├── images/
│       │   ├── train/
│       │   ├── valid/
│       │   └── test/
│       ├── labels/
│       │   ├── train/
│       │   ├── valid/
│       │   └── test/
│       └── data.yaml
├── runs/
│   └── detect/
│       └── train2/
│           └── weights/
│               ├── best.pt
│               └── last.pt
├── main.py
└── README.md
```

*Note: The structure above represents the expected project layout. Actual folders and generated training files may vary.*

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_REPOSITORY_FOLDER>
```

Replace the placeholders with the actual repository URL and folder name.

### 2. Create a Virtual Environment

```bash
python -m venv yolo-env
```

Activate it on Windows:

```powershell
.\yolo-env\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install ultralytics
```

### 4. Prepare the Dataset

Obtain an appropriately licensed dog detection dataset from [Roboflow Universe](https://universe.roboflow.com/) or use the dataset already provided for the project.

Ensure the dataset contains images, corresponding YOLO-format annotations, and a correctly configured `data.yaml` file.

### 5. Train the Model

Run the following command from the project root:

```bash
yolo task=detect mode=train model=yolov8n.pt data=datasets/my_roboflow_data/data.yaml epochs=50 imgsz=640
```

This command initializes YOLOv8 using pretrained weights and fine-tunes the model on the specified dataset.

Training outputs, model checkpoints, and evaluation metrics are saved under `runs/detect/`, typically in a newly created training directory.

## 🔍 Run Inference

To test the trained model on an image:

```bash
yolo task=detect mode=predict model=runs/detect/train2/weights/best.pt source=path/to/image.jpg
```

Replace `path/to/image.jpg` with the path to the image you want to test.

To run inference on a video:

```bash
yolo task=detect mode=predict model=runs/detect/train2/weights/best.pt source=path/to/video.mp4
```

Update the model path to match the actual training run. Prediction outputs are generally saved under `runs/detect/predict/`.

## 📊 Model Evaluation

The model can be evaluated using metrics such as:

- **Precision:** Measures the proportion of predicted detections that are correct.
- **Recall:** Measures the proportion of actual objects successfully detected.
- **mAP@0.5:** Measures detection performance using an intersection-over-union threshold of 0.5.

Actual results should be recorded after running evaluation on the project's dataset.

## 🚀 Future Scope

Potential extensions for the Just Dogs project include:

- **Dog Tracking:** Track individual dogs across video frames.
- **Activity Recognition:** Explore recognition of grooming activities such as bathing, brushing, and haircuts.
- **Service Monitoring:** Analyze video footage to help determine which services were performed.
- **Billing Verification:** Compare detected service events with recorded billing information.
- **Performance Optimization:** Evaluate detection accuracy under different camera angles, lighting conditions, and occlusions.

These features require additional development, suitable datasets, and testing under real-world salon conditions.

## 📦 Dataset

The project uses a labeled dog detection dataset. Dataset source, version, annotation details, and licensing information should be documented once finalized.

## 📄 License

The license for this project should be specified according to the repository owner's decision and the licenses of the code and datasets used.

## 👥 Project Context

This work is part of the Just Dogs computer vision project, exploring how object detection can contribute to automated monitoring in dog grooming salons.

