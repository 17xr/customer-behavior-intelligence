# Customer Behavior Intelligence

This project implements a computer vision pipeline for analyzing customer movement and engagement in retail environments. Developed during my summer school at KAUST, the system goes beyond simple counting by using spatio-temporal filtering to distinguish between passive passers-by and actively engaged customers.

## 🛠️ Advanced Pipeline Architecture

The system utilizes a multi-stage approach to ensure identity persistence even during occlusions:

- Object Detection: Leverages YOLOv8l for high-accuracy person detection.
- Primary Tracking: Uses DeepSORT with an OSNet (ReID) backbone to handle frame-to-frame associations.
- Post-Tracker Re-Association: A custom PostTracker class manages ID switches and "lost" tracks using a weighted cost function of Cosine Similarity (appearance) and Euclidean Distance (spatial proximity).
- Spatial Logic: Defines multiple Polygonal ROIs (Regions of Interest) to monitor specific store sections.
- Dwell-Time Analytics: Calculates the precise time spent within a zone, filtering out any interactions below a specific temporal threshold (e.g., 3.5 seconds).

## 📊 Key Features

- Robust Re-Identification: Optimized to maintain consistent IDs for customers even if they temporarily leave a camera's field of view.
- Dynamic Heatmapping: Generates both live decaying heatmaps and cumulative "Master" heatmaps to visualize store-wide traffic patterns.
- Automated Reporting: Finalizes analytics by exporting dwell-time logs for each ROI to CSV files for business intelligence integration.
- Flexible Zone Configuration: Support for multiple concurrent zones (e.g., Track_1, Track_2) with independent entry/exit logic.

## 💻 Tech Stack

- Core: Python, Jupyter Notebook
- CV Frameworks: ultralytics (YOLO), deep-sort-realtime, torchreid
- Math & Stats: NumPy, SciPy (Cosine distance), OpenCV
- Hardware Acceleration: CUDA-enabled for real-time processing

## 🎓 Acknowledgments

This project was developed during the **KAUST AI Summer School 2025** under the supervision of **Dr. Muhammad Mubashar**. It serves as a comprehensive customer behavior study for a local retail partner, utilizing advanced computer vision to derive spatial insights.

**Project Team:**
- Hassan Mohammed Nasr – Project Lead
- Abderrahmene Mehenni
- Khalid Alkaabi
