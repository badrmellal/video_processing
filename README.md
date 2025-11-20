# Video Processing - Motion Detection

A Python-based video processing tool that detects and visualizes motion in video files using OpenCV. This application processes video files frame by frame, identifies areas of movement, and outputs an annotated video with motion detection overlays.

## Features

- **Real-time Motion Detection**: Analyzes video frames to detect movement using frame differencing techniques
- **Visual Feedback**: Draws bounding boxes around detected motion areas
- **Motion Statistics**: Displays motion detection percentage and frame count
- **Live Preview**: Shows both the processed video and threshold mask in separate windows
- **Configurable Threshold**: Adjustable sensitivity for motion detection
- **Progress Tracking**: Real-time feedback on processing progress

## Requirements

- Python 3.x
- OpenCV (cv2)
- NumPy

## Installation

1. Clone this repository:
```bash
git clone https://github.com/badrmellal/video_processing.git
cd video_processing
```

2. Install the required dependencies:
```bash
pip install opencv-python numpy
```

## Usage

### Basic Usage

1. Update the `input_video` path in the script to point to your video file:
```python
input_video = "/path/to/your/video.mp4"
```

2. Run the script:
```bash
python playing_around.py
```

3. The processed video will be saved as `motion_detected_output.mp4` by default.

### Configuration Options

You can customize the motion detection behavior by modifying the following parameters in the `main()` function:

- **input_video**: Path to the input video file
- **output_video**: Path for the output video (default: `motion_detected_output.mp4`)
- **detection_threshold**: Sensitivity threshold for motion detection (default: 25)
  - Lower values = more sensitive (detect smaller movements)
  - Higher values = less sensitive (only detect larger movements)

```python
if __name__ == "__main__":
    input_video = "/path/to/your/video.mp4"
    output_video = "motion_detected_output.mp4"
    detection_threshold = 25  # Adjust as needed
    
    main(input_video, output_video, detection_threshold)
```

## How It Works

The motion detection algorithm follows these steps:

1. **Frame Capture**: Loads the video and extracts individual frames
2. **Grayscale Conversion**: Converts frames to grayscale for processing efficiency
3. **Frame Differencing**: Computes the absolute difference between consecutive frames
4. **Thresholding**: Applies binary thresholding to isolate motion areas
5. **Noise Reduction**: Uses morphological operations (dilation) to reduce noise
6. **Contour Detection**: Identifies contours of motion areas
7. **Filtering**: Filters out small contours (noise) using minimum area threshold (500 pixels)
8. **Visualization**: Draws green bounding boxes around detected motion areas
9. **Annotation**: Adds "DETECTED MOUVEMENT" text and frame counter to the output

## Output

The script generates:
- An output video file with motion detection overlays
- Real-time display windows showing:
  - Processed video with motion detection boxes
  - Binary threshold mask showing motion areas
- Console statistics including:
  - Video properties (width, height, fps, frame count)
  - Processing progress
  - Motion detection percentage

## Interactive Controls

While the script is running:
- **Press 'q'**: Quit the processing and save the current progress

## Example Output

When motion is detected, the output video will show:
- Green bounding boxes around moving objects
- Red text "DETECTED MOUVEMENT" at the top
- White frame counter at the bottom
- Final statistics showing the percentage of frames with detected motion

## Project Structure

```
video_processing/
├── playing_around.py           # Main script for motion detection
├── video0.mp4                  # Sample input video
├── motion_detected_output.mp4  # Sample output video
└── README.md                   # This file
```

## Functions Overview

- `load_video(video_path)`: Loads and validates the input video file
- `get_details(capture)`: Extracts video properties (dimensions, fps, frame count)
- `create_video_writer(output_path, width, height, fps)`: Creates the output video writer
- `detect_motion(capture, out, threshold)`: Main motion detection algorithm
- `main(input_video_path, output_path, threshold)`: Orchestrates the entire process

## Troubleshooting

- **Video not opening**: Ensure the video path is correct and the file format is supported by OpenCV
- **No motion detected**: Try lowering the `detection_threshold` value
- **Too many false positives**: Increase the `detection_threshold` value or adjust the minimum contour area (currently 500)
- **Output file error**: Ensure you have write permissions in the output directory

## Future Enhancements

Potential improvements for this project:
- Command-line argument support for easier configuration
- Support for multiple video formats
- Background subtraction algorithms (MOG2, KNN)
- Object tracking across frames
- Email/SMS alerts when motion is detected
- Region of Interest (ROI) selection
- Video saving optimization

## License

This project is available for educational and personal use.

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests.

## Author

Created by [badrmellal](https://github.com/badrmellal)
