# Warships Dataset

Warships is a visible-light image dataset for fine-grained military ship detection. It is designed to support the detection and recognition of military ship targets under diverse maritime scenes.

The dataset contains 5,973 images and 7,357 annotated ship instances, covering five fine-grained military ship categories: Aircraft Carrier, Submarine, Landing Ship, Auxiliary Ship, and Battle Ship.

## Dataset Overview

| Item | Description |
|---|---|
| Dataset name | Warships |
| Task | Fine-grained military ship detection |
| Image modality | Visible-light images |
| Annotation type | Horizontal bounding boxes |
| Annotation format | YOLO-style txt format |
| Number of images | 5,973 |
| Number of instances | 7,357 |
| Number of categories | 5 |

## Categories

| Class ID | Category |
|---:|---|
| 0 | Aircraft Carrier |
| 1 | Submarine |
| 2 | Landing Ship |
| 3 | Auxiliary Ship |
| 4 | Battle Ship |

## Annotation Format

Annotations are stored in YOLO-style txt format. Each image corresponds to one annotation file with the same base filename.

For example:

```text
images/000001.jpg
labels/000001.txt
```

Each line in an annotation file represents one target instance:

```text
class_id x_center y_center width height
```

where:

- `class_id` is the integer category ID.
- `x_center` and `y_center` are the normalized coordinates of the bounding box center.
- `width` and `height` are the normalized width and height of the bounding box.
- All bounding box coordinates are normalized to the range `[0, 1]`.

Example annotation:

```text
0 0.5123 0.4367 0.2845 0.1968
```

This example indicates an object of class `0`, namely Aircraft Carrier, with normalized bounding box coordinates.

## File Structure

The dataset package is organized as follows:

```text
Warships/
├── images/
├── labels/
├── splits/
│   ├── train.txt
│   ├── val.txt
│   └── test.txt
├── classes.txt
└── README.md
```

## Dataset Split

In the associated paper, the dataset is divided into training, validation, and test sets using stratified sampling with a ratio of 6:2:2.

If split files are included, they are stored as:

```text
splits/train.txt
splits/val.txt
splits/test.txt
```

Each line in a split file corresponds to the relative path of one image, for example:

```text
images/000001.jpg
images/000002.jpg
images/000003.jpg
```


## Class Names

The file `classes.txt` contains the following category names:

```text
Aircraft Carrier
Submarine
Landing Ship
Auxiliary Ship
Battle Ship
```

The category IDs correspond to the line numbers in `classes.txt`, starting from 0.

## Usage with YOLO-Style Detectors

For YOLO-style detectors, the dataset can be used with a dataset configuration file similar to the following:

```yaml
path: /path/to/Warships
train: splits/train.txt
val: splits/val.txt
test: splits/test.txt

nc: 5
names:
  0: Aircraft Carrier
  1: Submarine
  2: Landing Ship
  3: Auxiliary Ship
  4: Battle Ship
```


## Benchmark Models

The associated paper evaluates several representative object detection models on the Warships dataset, including:

- Faster R-CNN
- DETR
- YOLOv11n
- YOLOv11m

## Benchmark Results on Warships

| Model | P | R | mAP50 | mAP50-95 | Params/M | GFLOPs |
|---|---:|---:|---:|---:|---:|---:|
| Faster R-CNN | 0.852 | 0.831 | 0.857 | 0.621 | 33.24 | 52.86 |
| DETR | 0.835 | 0.845 | 0.835 | 0.629 | 36.76 | 57.12 |
| YOLOv11n | 0.944 | 0.932 | 0.966 | 0.830 | **2.62** | **3.31** |
| YOLOv11m | **0.950** | **0.941** | **0.975** | **0.868** | 20.11 | 34.26 |

## Cross-Dataset Generalization Results

The associated paper also evaluates cross-dataset generalization on the SeaShips dataset.

| Training Dataset | Model | P | R | mAP50 | mAP50-95 |
|---|---|---:|---:|---:|---:|
| SeaShips | Faster R-CNN | 0.896 | 0.882 | 0.905 | 0.652 |
| SeaShips | DETR | 0.878 | 0.865 | 0.883 | 0.638 |
| SeaShips | YOLOv11n | 0.924 | 0.917 | 0.936 | 0.785 |
| SeaShips | YOLOv11m | 0.942 | 0.935 | 0.951 | 0.827 |
| Warships | Faster R-CNN | 0.763 | 0.745 | 0.771 | 0.512 |
| Warships | DETR | 0.741 | 0.728 | 0.753 | 0.505 |
| Warships | YOLOv11n | 0.856 | 0.848 | 0.869 | 0.702 |
| Warships | YOLOv11m | 0.889 | 0.879 | 0.898 | 0.756 |

## Data Usage

This dataset is released for academic research purposes only. Users should comply with applicable copyright, security, and ethical requirements when using the dataset.

The dataset should not be used for illegal, harmful, or unauthorized purposes.


## Contact

For questions about the dataset, please contact the corresponding author.

## Version

Current version: Warships v1.0

Release date: 2026-07-05
