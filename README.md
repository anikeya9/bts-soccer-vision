# Soccer Player Tracking & Analysis System

**Course Project**: CSCI 566 - Deep Learning and Its Applications  
**Team**: Anikeya Aditya, Tian Sang, Zeyuan Wu  
**Institution**: University of Southern California  
**Date**: Fall 2024

---

## Overview

This project applies computer vision and deep learning techniques to analyze soccer game footage, providing quantitative feedback on player movements. The system extracts valuable performance metrics including speed, distance traveled, and predicted future positions from standard broadcast video footage.

**Motivation**: Professional soccer teams use expensive GPS tracking systems and multi-camera setups for performance analysis. This project demonstrates a cost-effective alternative using single-camera video footage and modern deep learning models, making advanced analytics accessible to lower-tier leagues with limited budgets.

---

## Approach

### Core Pipeline
1. **Player & Ball Detection**: YOLOv8 model for detecting players, goalkeepers, referees, and ball
2. **Pitch Detection**: YOLOv8 keypoint detection for field registration and homography transformation
3. **Player Tracking**: Custom distance-based tracking algorithm for consistent player IDs across frames
4. **Team Classification**: SigLIP embeddings + K-means clustering for automatic team assignment
5. **Performance Metrics**: Speed and distance calculations
6. **Position Prediction**: LSTM model for forecasting player trajectories

### Our Contributions
While the YOLO detection and tracking pipeline is based on the [Roboflow Football Analysis tutorial](https://www.youtube.com/watch?v=aBVGKoNZQUw), this project extends it with:
- **Speed and distance calculation scripts** for individual player performance analysis
- **LSTM-based position prediction** for forecasting player movements
- **Custom tracking refinements** to handle camera movement and player occlusion

---

## Results

Our system successfully:
- **Detected players, ball, and referees** with >90% accuracy using YOLOv8
- **Tracked individual players** across video frames with consistent IDs
- **Calculated performance metrics**: instantaneous speed (m/s) and cumulative distance traveled
- **Predicted future positions** using LSTM models (8 frames → 4 future frames)
- **Visualized gameplay** with bird's eye tactical view of the pitch

**Key achievement**: Converted 30-second video clips into quantitative player performance data suitable for tactical analysis.

---

## Repository Structure

```
soccer-player-tracking/
├── README.md
├── notebooks/
│   ├── 01_yolo_training.ipynb              # YOLO model training
│   ├── 02_player_detection_tracking.ipynb  # Main detection & tracking pipeline
│   ├── 03_data_extraction.ipynb            # Extract player position data
│   ├── 04_speed_distance_analysis.ipynb    # Calculate speed & distance metrics
│   ├── 05_lstm_data_preparation.ipynb      # Prepare data for LSTM training
│   └── 06_lstm_prediction.ipynb            # LSTM model for position prediction
|___Other_notebooks/
├── docs/
│   └── final_report.pdf                    # Full project report
└── data/
    └── README.md                           # Data description and sources

```

---

## Workflow

### 1. Model Training (`01_yolo_training.ipynb`)
Train YOLOv8 models on annotated soccer footage from Roboflow dataset:
- Player detection model (players, goalkeepers, referees, ball)
- Pitch keypoint detection model (field lines, corners, penalty box)

### 2. Detection & Tracking (`02_player_detection_tracking.ipynb`)
Run inference on video footage to:
- Detect all players and ball in each frame
- Apply homography transformation for pitch coordinates
- Track players across frames with consistent IDs
- Classify players into teams using SigLIP embeddings

### 3. Data Extraction (`03_data_extraction.ipynb`)
Extract structured player position data (x, y coordinates) from tracked video frames.

### 4. Performance Analysis (`04_speed_distance_analysis.ipynb`)
Calculate per-player metrics:
- Instantaneous speed between consecutive frames
- Total distance covered during the video clip

### 5. LSTM Prediction (`05_lstm_data_preparation.ipynb` + `06_lstm_prediction.ipynb`)
Train LSTM models to predict future player positions:
- Data preprocessing with standardization and normalization
- Per-player LSTM model training
- Prediction visualization (actual vs predicted trajectories)

---

## Key Technologies

- **YOLOv8**: Real-time object detection and keypoint detection
- **SigLIP**: Vision-language model for player jersey feature extraction
- **K-means Clustering**: Team classification
- **LSTM (PyTorch)**: Sequential position prediction
- **OpenCV**: Video processing and homography transformations
- **Supervision**: Tracking and annotation utilities

---

## Dataset

- **Source**: Roboflow public dataset with annotated soccer footage
- **Annotations**: Players, goalkeepers, referees, ball, and pitch keypoints
- **Training Split**: 92% training, 5% validation, 3% testing
- **Augmentation**: Hue/saturation shifts, rotation, scaling, Gaussian blur, noise injection

---

## Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Players missing from frames due to camera angle/occlusion | Custom distance-based tracking with interpolation |
| Inconsistent player IDs across frames | Maximum distance threshold (0.5m between frames) |
| Limited video data (5 videos × 30 seconds) | Data augmentation and per-player LSTM models |
| Team classification with similar jersey colors | SigLIP embeddings + UMAP dimensionality reduction |

---



---

## Credits & Acknowledgments

- **YOLO Detection Pipeline**: Based on [Roboflow's Football Analysis Tutorial](https://www.youtube.com/watch?v=aBVGKoNZQUw)
- **LSTM Implementation**: Developed with guidance from CSCI 566 Teaching Assistants
- **Dataset**: Roboflow public soccer dataset

---

## References

For detailed methodology, architecture diagrams, and comprehensive results, please see our [full project report](docs/final_report.pdf).

---


## License

This project was developed for academic purposes as part of a graduate course at USC.
