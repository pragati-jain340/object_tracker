# 🎯 Object Tracker - Pose Estimation with PnP and SIFT

This project estimates the 6DoF (position + orientation) pose of a planar object (e.g., gate) using a webcam or RealSense camera. It uses **SIFT feature matching**, **homography**, and **Perspective-n-Point (PnP)** pose estimation.

---

## 🧩 Modules Overview

### 📷 `tracker.py` - Real-Time Object Pose Estimation

- Allows user to select **4 corners of a planar object** (e.g., gate).
- Extracts SIFT keypoints from selected region.
- Matches keypoints in real-time against webcam input.
- Uses **Homography + PnP** to compute:
  - **Rotation** (Yaw, Pitch, Roll)
  - **Translation** (Tx, Ty, Tz)
- Displays:
  - Projected object outline on current frame.
  - Orientation and position (in cm) on screen.
  - Matched features between frames.

📌 Uses:
- `cv2.solvePnP` with IPPE method for stable results.
- Calibrated camera matrix (for RealSense or webcam).
- Draws matches and overlay info live.

---

### 🛠️ `function.py` - Utility Functions

Contains helper functions:
- `rotational_to_euler(R)`: Converts 3x3 rotation matrix to Euler angles.
- `draw_quadrilateral()`: Overlays selected corners as a quadrilateral.
- `get_four_points()`: GUI-based point selector for user to click 4 corners.

---

### 🧪 `camera_calibration/zhang.py` - Camera Calibration (Zhang's Method)

- Detects checkerboard corners in calibration images.
- Uses OpenCV's `calibrateCamera()` to compute:
  - Intrinsic matrix (Camera Matrix)
  - Distortion coefficients
  - Rotation & translation vectors for each image.
- Outputs all matrices and vectors.

📝 Note:
- You can use the **camera_calibration/capture_img_for_zhang.py** to capture checkerboard images.

---

## 📂 Folder Structure
<prev>

```
📂 object_tracker/
├── tracker.py
├── function.py
├── README.md
├── camera_calibration/
│   ├── zhang.py
│   └── capture_img_for_zhang.py

```
</prev>

## ✅ Requirements

- Python 3.x
- OpenCV (`cv2`)
- NumPy
- PyRealSense2 (optional for RealSense camera)

Install dependencies:
```bash
pip install opencv-python numpy pyrealsense2

