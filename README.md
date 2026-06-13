# 🚗 Lane Detection & Custom Canny Edge Detection System

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge\&logo=python)
![OpenCV](https://img.shields.io/badge/OpenCV-ComputerVision-green?style=for-the-badge\&logo=opencv)
![NumPy](https://img.shields.io/badge/NumPy-NumericalComputing-orange?style=for-the-badge\&logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-red?style=for-the-badge)

### 🛣️ Computer Vision Project for Edge Detection and Lane Violation Monitoring

</div>

---

# 📖 Project Overview

This project implements two important Computer Vision applications:

### 🔹 Part 1: Custom Canny Edge Detector

A complete implementation of the Canny Edge Detection algorithm from scratch without using OpenCV's built-in Canny function.

### 🔹 Part 2: Lane Detection & Lane Violation Monitoring

A lane detection system that identifies road lanes using:

* Edge Detection
* Region of Interest (ROI)
* Hough Transform
* Lane Line Averaging
* Lane Center Tracking

and determines whether a vehicle is maintaining its lane position.

---

# 🎯 Objectives

✅ Implement Canny Edge Detection manually

✅ Understand image processing fundamentals

✅ Detect road lanes automatically

✅ Monitor vehicle position relative to lane center

✅ Identify lane violations

---

# 🛠 Technologies Used

| Technology | Purpose              |
| ---------- | -------------------- |
| Python     | Programming Language |
| OpenCV     | Image Processing     |
| NumPy      | Matrix Operations    |
| Matplotlib | Visualization        |

---

# 🔍 Part 1: Custom Canny Edge Detector

The Canny Edge Detector was implemented from scratch using multiple image processing stages.

---

## 📌 Processing Pipeline

### 1️⃣ Noise Reduction

A Gaussian filter is applied to smooth the image and remove noise.

```text
Input Image
     ↓
Gaussian Blur
```

---

### 2️⃣ Gradient Computation

Sobel operators calculate intensity changes in both directions.

```text
Gx → Horizontal Gradient
Gy → Vertical Gradient
```

Gradient magnitude:

G = √(Gx² + Gy²)

Gradient direction:

θ = arctan(Gy / Gx)

---

### 3️⃣ Non-Maximum Suppression (NMS)

Removes weak neighboring responses and keeps only local maxima.

Benefits:

* Produces thin edges
* Eliminates thick boundaries
* Improves edge localization

---

### 4️⃣ Double Thresholding

Pixels are classified as:

| Type        | Value |
| ----------- | ----- |
| Strong Edge | 255   |
| Weak Edge   | 100   |
| Non Edge    | 0     |

---

### 5️⃣ Hysteresis

Weak edges connected to strong edges are preserved.

Disconnected weak edges are removed.

```text
Weak + Connected → Strong Edge
Weak + Isolated → Removed
```

---

# 📂 Saved Outputs

For every input image, the following results are stored:

```text
Image_1_Blurred.jpg
Image_2_Gradients.jpg
Image_3_NMS.jpg
Image_4_Final.jpg
```

---

# 🚦 Part 2: Lane Detection System

The second module performs automatic lane detection and lane violation monitoring.

---

## 📌 Lane Detection Pipeline

```text
Input Road Image
        ↓
Grayscale Conversion
        ↓
Gaussian Blur
        ↓
Canny Edge Detection
        ↓
Region Of Interest (ROI)
        ↓
Hough Transform
        ↓
Lane Detection
        ↓
Lane Violation Analysis
```

---

## 🏞 Region of Interest (ROI)

Only the road region is analyzed.

A triangular mask is applied to eliminate irrelevant areas.

Benefits:

* Faster processing
* Reduced noise
* Better lane detection

---

## 📏 Hough Transform

The Probabilistic Hough Transform detects line segments corresponding to road lanes.

```python
cv2.HoughLinesP()
```

Used Parameters:

| Parameter       | Value |
| --------------- | ----- |
| Threshold       | 50    |
| Min Line Length | 40    |
| Max Line Gap    | 150   |

---

## 📐 Lane Averaging

Detected line segments are grouped into:

### Left Lane

Negative slope

### Right Lane

Positive slope

Average slope and intercept are calculated to obtain smooth lane boundaries.

---

## 🎯 Lane Center Calculation

The system computes:

```text
Lane Center
=
(Left Lane + Right Lane)/2
```

Vehicle position is assumed to be at:

```text
Image Width / 2
```

---

# ⚠ Lane Violation Detection

The deviation between:

* Vehicle Center
* Lane Center

is calculated.

```text
Deviation = Vehicle Center − Lane Center
```

---

### Decision Rule

```text
If Deviation > Tolerance
        ↓
Lane Violation

Else
        ↓
Within Lane
```

Tolerance Used:

```text
40 Pixels
```

---

# 📊 Output Status

### ✅ Within Lane

Displayed when the vehicle remains centered.

### ❌ Lane Violation

Displayed when the vehicle drifts beyond the allowed threshold.

---

# 📸 Visualization

The system displays:

* Original Road Image
* Detected Lanes
* Lane Center
* Vehicle Center
* Violation Status

Example:

```text
Vehicle Center ●
Lane Center ●

Status:
Within Lane
```

or

```text
Status:
Lane Violation!
```

---

# 📁 Project Structure

```text
Lane-Detection-System/
│
├── images/
│     ├── road1.jpg
│     ├── road2.jpg
│
├── final_output/
│     ├── road1_1_blurred.jpg
│     ├── road1_2_gradients.jpg
│     ├── road1_3_nms.jpg
│     ├── road1_4_final.jpg
│
├── canny_edge_detector.py
├── lane_detection.py
├── README.md
```

---

# 📈 Key Features

### Edge Detection

✅ Gaussian Smoothing

✅ Sobel Gradients

✅ Non-Maximum Suppression

✅ Double Thresholding

✅ Hysteresis

---

### Lane Detection

✅ ROI Selection

✅ Hough Transform

✅ Left/Right Lane Detection

✅ Lane Center Tracking

✅ Lane Violation Monitoring

---

# 💡 Future Improvements

* Real-time Video Processing
* Webcam Integration
* Deep Learning Lane Detection
* Curved Lane Tracking
* Autonomous Driving Integration
* Night-Time Lane Detection
* Traffic Sign Recognition

---

# 🏆 Conclusion

This project successfully demonstrates both low-level and high-level Computer Vision techniques.

### Achievements

✅ Custom Canny Edge Detector from Scratch

✅ Automated Lane Detection

✅ Lane Center Estimation

✅ Lane Violation Monitoring

✅ Image Processing Pipeline Visualization

The project provides a strong foundation for understanding edge detection, lane tracking, and intelligent transportation systems used in autonomous vehicles.

---

