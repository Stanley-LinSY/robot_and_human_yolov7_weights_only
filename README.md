# Human & Robot Detection — YOLOv7 Weights

Pre-trained YOLOv7 model weights for detecting **humans and robots** in real-time. This repository stores the custom-trained model file and a PyTorch Hub configuration for easy loading.

---

## Overview

This model was fine-tuned from the official [YOLOv7](https://github.com/WongKinYiu/yolov7) architecture on a custom dataset containing images of humans and industrial robots. It is designed for use in collaborative robot (cobot) safety systems, warehouse automation, or any scenario requiring simultaneous human-robot detection.

| Class   | Label |
|---------|-------|
| Human   | `0`   |
| Robot   | `1`   |

---

## Repository Contents

| File               | Description                                      |
|--------------------|--------------------------------------------------|
| `yolov7_best.pt`   | Best checkpoint from custom training (~12 MB)    |
| `hubconf.py`       | PyTorch Hub entry point for model loading        |

> The full training code, dataset configuration, and Jupyter notebooks live in the companion repo: [human_and_robot](https://github.com/Stanley-LinSY/human_and_robot)

---

## Requirements

```bash
pip install torch torchvision
pip install opencv-python
```

Clone the YOLOv7 inference codebase:

```bash
git clone https://github.com/WongKinYiu/yolov7
cd yolov7
pip install -r requirements.txt
```

---

## Usage

### Download Weights

```bash
# Clone this repo to get the weights
git clone https://github.com/Stanley-LinSY/robot_and_human_yolov7_weights_only
```

### Run Inference

```bash
# On an image
python detect.py --weights ../robot_and_human_yolov7_weights_only/yolov7_best.pt \
                 --conf 0.25 --img-size 640 --source path/to/image.jpg

# On a video
python detect.py --weights ../robot_and_human_yolov7_weights_only/yolov7_best.pt \
                 --conf 0.25 --img-size 640 --source path/to/video.mp4

# On webcam
python detect.py --weights ../robot_and_human_yolov7_weights_only/yolov7_best.pt \
                 --conf 0.25 --img-size 640 --source 0
```

### Load via PyTorch Hub

```python
import torch

model = torch.hub.load(
    'Stanley-LinSY/robot_and_human_yolov7_weights_only',
    'custom',
    path='yolov7_best.pt',
    force_reload=True
)
```

---

## Model Details

| Property        | Value        |
|-----------------|--------------|
| Base Model      | YOLOv7       |
| Input Size      | 640 × 640    |
| Classes         | 2 (Human, Robot) |
| Framework       | PyTorch      |
| Weight Format   | `.pt`        |

---

## Related Repositories

- [human_and_robot](https://github.com/Stanley-LinSY/human_and_robot) — Full training pipeline, notebooks, and dataset config
- [human_and_robot_yolov8_weight_only](https://github.com/Stanley-LinSY/human_and_robot_yolov8_weight_only) — YOLOv8 version of this model

---

## License

Based on the [YOLOv7](https://github.com/WongKinYiu/yolov7) codebase. Custom trained weights are released under [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html).
