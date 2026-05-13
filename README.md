# YOLOv8s Advanced Real-Time Detection System

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![YOLOv8s](https://img.shields.io/badge/YOLOv8s-00FFFF?style=flat&logo=yolo&logoColor=black)](https://github.com/ultralytics/ultralytics)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white)](https://opencv.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)

---

## About

Enterprise-grade real-time object detection system built with **YOLOv8s**. Features live object counter, dynamic class colors, fullscreen HD display (1920×1080), FPS monitoring, professional statistics, and production-ready error handling.

**Perfect for:**
- Real-time monitoring systems
- Security surveillance
- Traffic analysis
- Crowd counting
- Research and development
- Educational purposes

**Key Features:**
- Real-time detection (30-40 FPS on CPU)
- Live object counter with frame statistics
- Dynamic random colors per class (consistent)
- High-definition fullscreen display (1920×1080)
- FPS monitoring and performance metrics
- Confidence scores for each detection
- Professional UI with styled text
- Error handling and graceful shutdown
- Structured code with functions
- Comprehensive logging

---

## Quick Start

### Prerequisites
```bash
Python 3.8+
Webcam
4GB+ RAM
```

### Installation
```bash
git clone https://github.com/username/yolov8s-advanced-detection-system.git
cd yolov8s-advanced-detection-system
pip install -r requirements.txt
```

### Run
```bash
python main.py
```

### Exit
Press **Q** to quit gracefully

---

## Features Explained

### 1. Real-Time Object Counter
```python
Displays total objects detected in current frame
Located at top-left in yellow text
Updates every frame automatically
```

### 2. Dynamic Class Colors
Each detected class gets a unique random color:
- First detection → random color assigned
- All subsequent detections → same color
- Makes tracking easier visually

### 3. FPS Monitoring
```python
Calculates frames per second in real-time
Displayed on top-left of frame
Helps monitor performance
```

### 4. Frame Statistics
Shows:
- Object count per frame
- Frame number
- FPS
- Final statistics on exit

### 5. Professional Display
- 1920×1080 HD resolution
- Automatic fullscreen mode
- Text with background for readability
- Color-coded information

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| **Deep Learning** | YOLOv8s (Ultralytics) |
| **Computer Vision** | OpenCV 4.8+ |
| **Language** | Python 3.8+ |
| **Framework** | PyTorch 2.0+ |
| **Performance** | 30-40 FPS (CPU) |

---

## Performance Metrics

| Metric | Value |
|--------|-------|
| **Model** | YOLOv8s |
| **FPS** | 30-40 (CPU) / 60+ (GPU) |
| **Resolution** | 1920×1080 HD |
| **Confidence Threshold** | 0.5 |
| **Detectable Classes** | 80 (COCO) |
| **Model Size** | 42MB |
| **Memory Usage** | ~1.5GB |

---

## Customization

### Change Resolution
```python
# In main.py, modify initialize_camera()
cap = initialize_camera(1280, 720)  # Lower resolution = faster
```

### Adjust Confidence Threshold
```python
results = model.predict(frame, stream=True, verbose=False, conf=0.7)
```

### Use Different Model
```python
# YOLOv8 variants:
model = YOLO("yolov8n.pt")  # Nano - Fastest
model = YOLO("yolov8s.pt")  # Small - Balanced (current)
model = YOLO("yolov8m.pt")  # Medium
model = YOLO("yolov8l.pt")  # Large
model = YOLO("yolov8x.pt")  # Extra Large - Accurate
```

### Disable Fullscreen
```python
# Comment out in setup_window():
# cv2.setWindowProperty(...)
```

### Change Colors
```python
# In draw_statistics():
cv2.putText(frame, ..., (200, 0, 200), ...)  # Change BGR color
```

---

## Troubleshooting

### Low FPS
```bash
1. Use smaller model: yolov8n.pt
2. Reduce resolution: 1280x720
3. Increase conf threshold: 0.6 or 0.7
4. Close other applications
```

### Webcam Not Found
```bash
python -c "import cv2; print(cv2.VideoCapture(0).isOpened())"
```

### CUDA Memory Error
```bash
# Use CPU or smaller model
model = YOLO("yolov8n.pt")
```

### High CPU Usage
```bash
1. Skip frames: process every 2nd frame
2. Reduce resolution
3. Use GPU acceleration
```

---

## Learning Resources

- **[YOLOv8 Official Documentation](https://docs.ultralytics.com/)** - Complete guide
- **[OpenCV Tutorials](https://docs.opencv.org/)** - Computer vision basics
- **[YOLO Research Paper](https://arxiv.org/abs/2004.10934)** - Technical details
- **[COCO Dataset](https://cocodataset.org/)** - 80 detectable classes
- **[PyTorch Documentation](https://pytorch.org/)** - Deep learning framework

---

## 📁 Project Structure
yolov8s-advanced-detection-system/
├── main.py                 # Main detection script
├── requirements.txt        # Python dependencies
├── README.md              # This file
├── LICENSE                # MIT License
├── .gitignore             # Git ignore rules
└── images/
└── demo.png           # Demo screenshot (optional)

---

## Advanced Usage

### Process Video File
```python
# In main.py, modify initialize_camera():
cap = cv2.VideoCapture("video.mp4")
```

### Save Output Video
```python
# Add to main.py:
fourcc = cv2.VideoWriter_fourcc(*'mp4v')
out = cv2.VideoWriter('output.mp4', fourcc, 30.0, (1920, 1080))
out.write(frame)  # In main loop
out.release()  # At end
```

### Add Class Filtering
```python
# Only detect specific classes
allowed_classes = [0, 2, 5]  # Person, Car, Dog
if cls not in allowed_classes:
    continue
```

### Add Frame Skipping (Faster)
```python
frame_count = 0
skip_frames = 2
if frame_count % skip_frames == 0:
    results = model.predict(...)
```

---

## Contributing

Found a bug? Have suggestions?

1. Fork the repository
2. Create feature branch: `git checkout -b feature/improvement`
3. Commit changes: `git commit -m 'Add improvement'`
4. Push to branch: `git push origin feature/improvement`
5. Open Pull Request

---

## License

MIT License - See [LICENSE](LICENSE) file for details

**YOLOv8:** Licensed under AGPL-3.0 by Ultralytics

---

## Author

**Fiby Ehab** - AI Engineer

**Email:** febeehab3@gmail.com

**LinkedIn:** [Fiby Ehab](https://www.linkedin.com/in/fiby-ehab-270b55286/)

**GitHub:** [@FibyEhab](https://github.com/FibyEhab)  

---

## Support

- **Issues:** Open GitHub issues for bugs
- **Questions:** Contact via email or LinkedIn
- **Discussions:** Use GitHub discussions

---

## ⭐ Show Your Support

If this project helped you:
- ⭐ **Star** this repository
- **Fork** for your own use
- **Share** with others
- **Provide feedback**

Every star motivates me to create more projects! 

---

## 🔗 Related Projects

- [Real-Time YOLO Color Detection](https://github.com/username/real-time-yolo-color-detection)
- [YOLOv8 Object Counter](https://github.com/username/yolov8-realtime-object-counter)

---

**Made with ❤️ for the AI Community**

Last updated: January 2025 | Version: 1.0
