# Real-Time Object Detection with YOLOv8s and Live Object Counter

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![YOLOv8s](https://img.shields.io/badge/YOLOv8s-00FFFF?style=flat&logo=yolo&logoColor=black)](https://github.com/ultralytics/ultralytics)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white)](https://opencv.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)

---

## About

Professional real-time object detection system using **YOLOv8s** with an integrated **live object counter**. Features dynamic random colors for each detected class, fullscreen HD display (1920×1080), and real-time object counting in each frame.

**Key Features:**
- Real-time detection at 30-40 FPS
- **Live object counter** - displays total objects in current frame
- Dynamic random colors for each class (consistent across frames)
- High resolution (1920×1080) fullscreen display
- Confidence scores for each detection
- YOLOv8s model (balanced speed/accuracy)
- Frame statistics (FPS, average objects)

---

## What's Special?

### Object Counter Feature
- **Real-time count** of all detected objects in each frame
- **Yellow text display** in top-left corner
- **Updates every frame** automatically
- **Easy to track** object density in scene

### Dynamic Colors
Each object class gets a unique random color:
- First detection → color assigned
- Subsequent detections → same color used
- Makes tracking specific categories easier

### Fullscreen HD Display
- 1920×1080 resolution for immersive experience
- Automatic fullscreen mode
- Professional presentation quality

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| **Deep Learning** | YOLOv8s (Ultralytics) |
| **Computer Vision** | OpenCV 4.8+ |
| **Language** | Python 3.8+ |
| **Framework** | PyTorch 2.0+ |

---

## Installation

### Prerequisites
- Python 3.8+
- Webcam
- 4GB+ RAM

### Quick Setup
```bash
git clone https://github.com/username/yolov8-realtime-object-counter.git
cd yolov8-realtime-object-counter
pip install -r requirements.txt
```

---

## Usage

### Run the Script
```bash
python main.py
```

### What You'll See
1. **Fullscreen display** (1920×1080)
2. **Bounding boxes** around detected objects
3. **Class labels** with confidence scores
4. **Unique colors** per class (assigned randomly)
5. **Live counter** in yellow (top-left corner)
6. **Statistics** in console output

### Controls
- **Q key** - Quit program

---

## Key Features

### 1. Object Counter
```python
object_count = 0
for r in results:
    boxes = r.boxes
    object_count += len(boxes)

cv2.putText(frame, f'Total objects: {object_count}', (30, 50), ...)
```

### 2. Dynamic Colors
```python
if cls not in class_colors:
    class_colors[cls] = [random.randint(0, 255) for _ in range(3)]
color = class_colors[cls]
```

### 3. Fullscreen Mode
```python
cv2.setWindowProperty(window_name, cv2.WND_PROP_FULLSCREEN, cv2.WINDOW_FULLSCREEN)
```

### 4. High Resolution
```python
cap.set(3, 1920)  # Width
cap.set(4, 1080)  # Height
```

---

## Performance

| Metric | Value |
|--------|-------|
| **Model** | YOLOv8s |
| **FPS** | 30-40 (CPU) / 60+ (GPU) |
| **Resolution** | 1920×1080 |
| **Confidence** | 0.5 |
| **Classes** | 80 (COCO) |

---

## Customization

### Adjust Confidence
```python
results = model.predict(frame, conf=0.7)
```

### Change Resolution
```python
cap.set(3, 1280)
cap.set(4, 720)
```

### Disable Fullscreen
```python
# Comment out:
# cv2.setWindowProperty(...)
```

### Different Model
```python
model = YOLO("yolov8n.pt")  # Faster
model = YOLO("yolov8m.pt")  # Balanced
```

### Counter Position
```python
cv2.putText(frame, f'Total objects: {object_count}', 
           (50, 100),  # x, y
           cv2.FONT_HERSHEY_SIMPLEX, 1.5, (0, 255, 255), 3)
```

---

## 🐛 Troubleshooting

### Low FPS
- Use `yolov8n.pt` (nano)
- Reduce resolution
- Increase confidence threshold

### Webcam Issues
```bash
python -c "import cv2; print(cv2.VideoCapture(0).isOpened())"
```

### Memory Issues
```bash
pip install --upgrade torch torchvision
```

---

## Resources

- [YOLOv8 Docs](https://docs.ultralytics.com/)
- [OpenCV Tutorials](https://docs.opencv.org/)
- [YOLO Paper](https://arxiv.org/abs/2004.10934)
- [COCO Dataset](https://cocodataset.org/)

---

## Next Steps

- Add class filtering (count only specific classes)
- Add history graph of object counts
- Add recording functionality
- Add statistics dashboard
- Add export to CSV

---

## Contributing

Got ideas for improvements? I'd love to collaborate!

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**YOLOv8 Model:** Licensed under the AGPL-3.0 License by Ultralytics

---

## Author

**Fiby Ehab** - AI Engineer

**Fiby Ehab** - AI Engineer

**Email:** febeehab3@gmail.com

**LinkedIn:** [Fiby Ehab](https://www.linkedin.com/in/fiby-ehab-270b55286/)

**GitHub:** [@FibyEhab](https://github.com/FibyEhab)  

---

## Acknowledgments

- [Ultralytics](https://github.com/ultralytics) for YOLOv8
- [OpenCV](https://opencv.org/) for computer vision tools
- [COCO Dataset](https://cocodataset.org/) for pre-trained weights

---

## ⭐ If this project helped you, please star it!

Made with ❤️ for the AI community
