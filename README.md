# Motion Analysis with Pose Estimation

This project processes a **YouTube video** in **Google Colab**, extracts representative motion frames, runs **pose estimation**, computes a geometric motion metric, and prepares all deliverables for GitHub submission.

---

## 🚀 Project Overview

The pipeline performs the following steps:

1. **Download YouTube video** (using Colab)
2. **Extract 5–10 representative frames** representing different motion stages
3. **Run pose estimation using MediaPipe Pose**
4. **Save pose-overlaid images**
5. **Compute Head Movement Distance** based on nose keypoint displacement
6. **Generate simple accuracy metrics** for evaluation
7. **Provide geometric interpretation of motion**
8. Store all outputs in a structured folder for GitHub submission.

---

## 🤖 Model Choice

**MediaPipe Pose** was used as the pose-estimation model because:

- Runs efficiently on CPU (no GPU needed)
- Lightweight with fast inference
- Provides 33 stable keypoints including facial landmarks
- Performs internal tracking for smooth frame-to-frame consistency
- Easy to install and visualize in Colab.

A detailed comparison with other models (MoveNet, YOLOv8-Pose, OpenPose) is included in the `report.txt`.

---

## 📏 Metric Computed

### **Head Movement Distance**
- Keypoint used: **Nose (ID 0)**
- Method: **Euclidean distance in 2D pixel space**
- Measures straight-line head displacement between motion stages.

### 📊 Numeric Results

| Frame Pair       | Nose Movement (pixels) |
|----------------|----------------------|
| 100 → 300      | 36.0 px              |
| 300 → 500      | 22.0 px              |
| 500 → 700      | 40.7 px              |
| 700 → 900      | 18.9 px              |

- **Max movement:** 40.7 px (500 → 700)
- **Min movement:** 18.9 px (700 → 900)

---

## 🔍 Interpretation (Geometry Only)

Head displacement ranges confirm noticeable 2D motion across stages. High confidence (0.89 average) and near-perfect PCK (~1.0) indicate stable keypoint tracking, meaning distances represent actual spatial shifts, not detection noise.

---

## 🛠 Installation (for local testing)

You can run the notebook in Colab directly. For local testing:

```bash
pip install mediapipe opencv-python yt-dlp
