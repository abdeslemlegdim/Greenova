# Garbage Classification with YOLOv5

This project focuses on training a YOLOv5 model to classify different types of garbage. The goal is to create an efficient and accurate model that can identify various categories of waste, helping in effective waste management and recycling efforts.

## Dataset

The dataset used for this project consists of images categorized into six classes:
- BIODEGRADABLE
- CARDBOARD
- GLASS
- METAL
- PAPER
- PLASTIC

### Dataset Structure

```
train: ../train/images
val: ../valid/images
test: ../test/images

nc: 6
names: ['BIODEGRADABLE', 'CARDBOARD', 'GLASS', 'METAL', 'PAPER', 'PLASTIC']

roboflow:
  workspace: material-identification
  project: garbage-classification-3
  version: 2
  license: CC BY 4.0
  url: https://universe.roboflow.com/material-identification/garbage-classification-3/dataset/2
```

## Training

The YOLOv5 model is trained using the provided dataset. The training process involves the following steps:
1. Setting up the YOLOv5 environment and dependencies.
2. Preparing the dataset and organizing it into training, validation, and test sets.
3. Configuring the dataset using a YAML file.
4. Training the model using specified parameters such as image size, batch size, and number of epochs.

### Training Command

```bash
python train.py --img 640 --batch 16 --epochs 50 --data ../data.yaml --weights yolov5s.pt
```

### Validation Command

```bash
python val.py --data ../data.yaml --weights runs/train/exp/weights/best.pt --img 640
```

## Results

After training, the best model weights are saved and can be used for inference. The performance metrics for the model are evaluated based on precision, recall, and mAP (mean Average Precision).

### Example Metrics

```
Class     Images  Instances          P          R      mAP50   mAP50-95
all       2098      18916       0.44      0.367      0.382      0.217
BIODEGRADABLE       2098      13637      0.627      0.518      0.563      0.274
CARDBOARD           2098       1292      0.622      0.422      0.494      0.302
GLASS               2098       2380      0.743      0.556      0.642        0.4
METAL               2098       1360      0.437       0.51      0.436      0.226
PAPER               2098         33     0.0317     0.0606     0.0566      0.054
PLASTIC             2098        214      0.194      0.134      0.103     0.0454
```

## Usage

To use the trained model for inference, run the following command:

```bash
python detect.py --weights runs/train/exp1_gpu/weights/best.pt --source your_test_images_folder
```

## Future Work

- Collect more data to improve model performance, especially for underrepresented classes.
- Implement data augmentation techniques to enhance training.
- Experiment with different model architectures and hyperparameters.

## License

This project is licensed under the CC BY 4.0 License.

## Acknowledgements

- The dataset and initial project setup were provided by Roboflow.
- YOLOv5 repository by Ultralytics.
