---
comments: true
description: Discover YOLO-NAS by Deci AI - a state-of-the-art object detection model with quantization support. Explore features, pretrained models, and implementation examples.
keywords: YOLO-NAS, Deci AI, object detection, deep learning, Neural Architecture Search, Ultralytics, Python API, YOLO model, SuperGradients, pretrained models, quantization, AutoNAC
---

# YOLO-NAS

## Overview

Developed by Deci AI, YOLO-NAS is a groundbreaking object detection foundational model. It is the product of advanced Neural Architecture Search technology, meticulously designed to address the limitations of previous YOLO models. With significant improvements in quantization support and accuracy-latency trade-offs, YOLO-NAS represents a major leap in object detection.

![Model example image](https://learnopencv.com/wp-content/uploads/2023/05/yolo-nas_COCO_map_metrics.png) **Overview of YOLO-NAS.** YOLO-NAS employs quantization-aware blocks and selective quantization for optimal performance. The model, when converted to its INT8 quantized version, experiences a minimal precision drop, a significant improvement over other models. These advancements culminate in a superior architecture with unprecedented object detection capabilities and outstanding performance.

### Key Features

- **Quantization-Friendly Basic Block:** YOLO-NAS introduces a new basic block that is friendly to quantization, addressing one of the significant limitations of previous YOLO models.
- **Sophisticated Training and Quantization:** YOLO-NAS leverages advanced training schemes and post-training quantization to enhance performance.
- **AutoNAC Optimization and Pre-training:** YOLO-NAS utilizes AutoNAC optimization and is pre-trained on prominent datasets such as COCO, Objects365, and Roboflow 100. This pre-training makes it extremely suitable for downstream object detection tasks in production environments.

## Pre-trained Models

Experience the power of next-generation object detection with the pre-trained YOLO-NAS models provided by Ultralytics. These models are designed to deliver top-notch performance in terms of both speed and accuracy. Choose from a variety of options tailored to your specific needs:

| Model            | mAP   | Latency (ms) |
| ---------------- | ----- | ------------ |
| YOLO-NAS S       | 47.5  | 3.21         |
| YOLO-NAS M       | 51.55 | 5.85         |
| YOLO-NAS L       | 52.22 | 7.87         |
| YOLO-NAS S INT-8 | 47.03 | 2.36         |
| YOLO-NAS M INT-8 | 51.0  | 3.78         |
| YOLO-NAS L INT-8 | 52.1  | 4.78         |

Each model variant is designed to offer a balance between Mean Average Precision (mAP) and latency, helping you optimize your object detection tasks for both performance and speed.

## Usage Examples

Ultralytics has made YOLO-NAS models easy to integrate into your Python applications via our `ultralytics` python package. The package provides a user-friendly Python API to streamline the process.

The following examples show how to use YOLO-NAS models with the `ultralytics` package for inference and validation:

### Inference and Validation Examples

In this example we validate YOLO-NAS-s on the COCO8 dataset.

!!! Example

    This example provides simple inference and validation code for YOLO-NAS. For handling inference results see [Predict](../modes/predict.md) mode. For using YOLO-NAS with additional modes see [Val](../modes/val.md) and [Export](../modes/export.md). YOLO-NAS on the `ultralytics` package does not support training.

    === "Python"

        PyTorch pretrained `*.pt` models files can be passed to the `NAS()` class to create a model instance in python:

        ```python
        from ultralytics import NAS

        # Load a COCO-pretrained YOLO-NAS-s model
        model = NAS("yolo_nas_s.pt")

        # Display model information (optional)
        model.info()

        # Validate the model on the COCO8 example dataset
        results = model.val(data="coco8.yaml")

        # Run inference with the YOLO-NAS-s model on the 'bus.jpg' image
        results = model("path/to/bus.jpg")
        ```

    === "CLI"

        CLI commands are available to directly run the models:

        ```bash
        # Load a COCO-pretrained YOLO-NAS-s model and validate it's performance on the COCO8 example dataset
        yolo val model=yolo_nas_s.pt data=coco8.yaml

        # Load a COCO-pretrained YOLO-NAS-s model and run inference on the 'bus.jpg' image
        yolo predict model=yolo_nas_s.pt source=path/to/bus.jpg
        ```

## Supported Tasks and Modes

We offer three variants of the YOLO-NAS models: Small (s), Medium (m), and Large (l). Each variant is designed to cater to different computational and performance needs:

- **YOLO-NAS-s**: Optimized for environments where computational resources are limited but efficiency is key.
- **YOLO-NAS-m**: Offers a balanced approach, suitable for general-purpose object detection with higher accuracy.
- **YOLO-NAS-l**: Tailored for scenarios requiring the highest accuracy, where computational resources are less of a constraint.

Below is a detailed overview of each model, including links to their pre-trained weights, the tasks they support, and their compatibility with different operating modes.

| Model Type | Pre-trained Weights                                                                           | Tasks Supported                        | Inference | Validation | Training | Export |
| ---------- | --------------------------------------------------------------------------------------------- | -------------------------------------- | --------- | ---------- | -------- | ------ |
| YOLO-NAS-s | [yolo_nas_s.pt](https://github.com/ultralytics/assets/releases/download/v8.2.0/yolo_nas_s.pt) | [Object Detection](../tasks/detect.md) | ✅        | ✅         | ❌       | ✅     |
| YOLO-NAS-m | [yolo_nas_m.pt](https://github.com/ultralytics/assets/releases/download/v8.2.0/yolo_nas_m.pt) | [Object Detection](../tasks/detect.md) | ✅        | ✅         | ❌       | ✅     |
| YOLO-NAS-l | [yolo_nas_l.pt](https://github.com/ultralytics/assets/releases/download/v8.2.0/yolo_nas_l.pt) | [Object Detection](../tasks/detect.md) | ✅        | ✅         | ❌       | ✅     |

## Citations and Acknowledgements

If you employ YOLO-NAS in your research or development work, please cite SuperGradients:

!!! Quote ""

    === "BibTeX"

        ```bibtex
        @misc{supergradients,
              doi = {10.5281/ZENODO.7789328},
              url = {https://zenodo.org/record/7789328},
              author = {Aharon,  Shay and {Louis-Dupont} and {Ofri Masad} and Yurkova,  Kate and {Lotem Fridman} and {Lkdci} and Khvedchenya,  Eugene and Rubin,  Ran and Bagrov,  Natan and Tymchenko,  Borys and Keren,  Tomer and Zhilko,  Alexander and {Eran-Deci}},
              title = {Super-Gradients},
              publisher = {GitHub},
              journal = {GitHub repository},
              year = {2021},
        }
        ```

We express our gratitude to Deci AI's [SuperGradients](https://github.com/Deci-AI/super-gradients/) team for their efforts in creating and maintaining this valuable resource for the computer vision community. We believe YOLO-NAS, with its innovative architecture and superior object detection capabilities, will become a critical tool for developers and researchers alike.

## FAQ

### What is YOLO-NAS and how does it differ from previous YOLO models?

YOLO-NAS, developed by Deci AI, is an advanced object detection model built using Neural Architecture Search (NAS). It offers significant improvements over previous YOLO models, including:

- **Quantization-Friendly Basic Block:** This helps reduce the precision drop when the model is converted to INT8 quantization.
- **Enhanced Training and Quantization:** YOLO-NAS utilizes sophisticated training schemes and post-training quantization techniques.
- **Pre-trained on Large Datasets:** Utilizes the COCO, Objects365, and Roboflow 100 datasets, making it highly robust for downstream tasks.

For more details, refer to the [Overview of YOLO-NAS](#overview).

### How can I use YOLO-NAS models in my Python application?

Ultralytics makes it easy to integrate YOLO-NAS models into your Python applications via the `ultralytics` package. Here's a basic example:

```python
from ultralytics import NAS

# Load a pre-trained YOLO-NAS-s model
model = NAS("yolo_nas_s.pt")

# Display model information
model.info()

# Validate the model on the COCO8 dataset
results = model.val(data="coco8.yaml")

# Run inference with the YOLO-NAS-s model on an image
results = model("path/to/image.jpg")
```

For additional examples, see the [Usage Examples](#usage-examples) section of the documentation.

### Why should I use YOLO-NAS for object detection tasks?

YOLO-NAS offers several advantages that make it a compelling choice for object detection:

- **High Performance:** Achieves a balance between accuracy and latency, crucial for real-time applications.
- **Pre-Trained on Diverse Datasets:** Provides robust models for various use cases with extensive pre-training on datasets like COCO and Objects365.
- **Quantization Efficiency:** For applications requiring low latency, the INT8 quantized versions show minimal precision drop, making them suitable for resource-constrained environments.

For a detailed comparison of model variants, see [Pre-trained Models](#pre-trained-models).

### What are the supported tasks and modes for YOLO-NAS models?

YOLO-NAS models support several tasks and modes, including:

- **Object Detection:** Suitable for identifying and localizing objects in images.
- **Inference and Validation:** Models can be used for both inference and validation to assess performance.
- **Export:** YOLO-NAS models can be exported to various formats for deployment.

However, the YOLO-NAS implementation using the `ultralytics` package does not currently support training. For more information, visit the [Supported Tasks and Modes](#supported-tasks-and-modes) section.

### How does quantization impact the performance of YOLO-NAS models?

Quantization can significantly reduce the model size and improve inference speed with minimal impact on accuracy. YOLO-NAS introduces a quantization-friendly basic block, resulting in minimal precision loss when converted to INT8. This makes YOLO-NAS highly efficient for deployment in scenarios with resource constraints.

To understand the performance metrics of INT8 quantized models, refer to the [Pre-trained Models](#pre-trained-models) section.
