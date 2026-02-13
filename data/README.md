# Data Directory

## Overview
This directory contains processed data files generated during the analysis pipeline.

## Data Files

### Expected Contents
- **Player tracking data**: Parquet files with player positions (x, y coordinates) across frames
- **LSTM training data**: Preprocessed sequences for position prediction
- **Performance metrics**: Speed and distance calculations per player

### Data Format
Player tracking data typically includes:
- `player_id`: Unique identifier for each player
- `team_id`: Team assignment (0 or 1)
- `video_id`: Source video identifier
- `t`: Frame/time index
- `x`, `y`: Pitch coordinates in meters

## Data Sources

The raw video data and annotations are sourced from:
- **Roboflow**: Public soccer dataset with labeled players, ball, and pitch keypoints
- **Custom videos**: 5 videos of 30 seconds each (approximately 750 frames per video at 25 fps)

## Note

Due to file size constraints, the actual data files are not included in this repository. 
The notebooks demonstrate the data processing pipeline and can be run on your own video footage.

## Data Generation

To generate your own data:
1. Run `01_yolo_training.ipynb` to train detection models (or use pre-trained weights)
2. Run `02_player_detection_tracking.ipynb` on your video files
3. Run `03_data_extraction.ipynb` to extract structured position data
4. Proceed with analysis notebooks (04-06)
