# Quick Start Guide

## Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd soccer-player-tracking
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Running the Notebooks

The notebooks should be run in order:

### 1. Train Models (Optional)
If you have your own training data:
```
notebooks/01_yolo_training.ipynb
```

### 2. Run Detection & Tracking
Process your video files:
```
notebooks/02_player_detection_tracking.ipynb
```
**Note**: You'll need to provide your own video files or use the Roboflow dataset.

### 3. Extract Data
Convert detections to structured data:
```
notebooks/03_data_extraction.ipynb
```

### 4. Analyze Performance
Calculate speed and distance metrics:
```
notebooks/04_speed_distance_analysis.ipynb
```

### 5. Predict Positions
Train LSTM models for position forecasting:
```
notebooks/05_lstm_data_preparation.ipynb
notebooks/06_lstm_prediction.ipynb
```

## Important Notes

- **API Keys**: Some notebooks use Roboflow API. You'll need to:
  - Sign up at [Roboflow](https://roboflow.com)
  - Get your API key
  - Replace the placeholder in the notebooks

- **GPU Recommended**: For faster training and inference, use a GPU-enabled environment

- **Data**: You'll need to provide your own video data or use the Roboflow dataset referenced in the tutorial

## Troubleshooting

### Common Issues

1. **CUDA not available**: Some notebooks use GPU. If you don't have a GPU, the code will fall back to CPU (slower).

2. **Missing dependencies**: Make sure all packages in `requirements.txt` are installed.

3. **File paths**: Update file paths in notebooks to match your local setup.

## Resources

- **Original Tutorial**: [Roboflow Football Analysis](https://www.youtube.com/watch?v=aBVGKoNZQUw)
- **YOLOv8 Docs**: [Ultralytics Documentation](https://docs.ultralytics.com)
- **Full Report**: See `docs/final_report.pdf`

## Questions?

Contact the team:
- Anikeya Aditya - aaditya@usc.edu
- Tian Sang - tians@usc.edu
- Zeyuan Wu - uwu@usc.edu
