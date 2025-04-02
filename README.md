# Crime Detection System using Vision Transformer

A robust crime detection system leveraging Vision Transformer (ViT) models to detect and classify criminal activities in videos and images.

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Features](#features)
- [Models](#models)
- [Installation](#installation)
- [Usage](#usage)
- [Workflow](#workflow)
- [Technical Details](#technical-details)
- [License](#license)

## Overview

This project implements a crime detection system using Vision Transformer (ViT) models to analyze video footage and images for potential criminal activities. The system can process both video files (analyzing 20-frame chunks) and individual images to detect various criminal actions.

## Project Structure

- [`Sever.ipynb`](c:\Users\pvmkt\OneDrive\Desktop\CrimeDetectionusingViTwith20framesinput\Sever.ipynb): Main model initialization and processing logic
- [`CrimeDetection_PyNgrok.ipynb`](c:\Users\pvmkt\OneDrive\Desktop\CrimeDetectionusingViTwith20framesinput\CrimeDetection_PyNgrok.ipynb): Notebook for running the system with PyNgrok
- [`index.html`](c:\Users\pvmkt\OneDrive\Desktop\CrimeDetectionusingViTwith20framesinput\index.html): Web interface for the system

## Features

- **Video Analysis**: Process video files to detect criminal activities
- **Image Analysis**: Analyze single images for crime detection
- **Real-time Processing**: Efficient frame extraction and analysis
- **Multi-class Detection**: Identifies 14 different action types
- **Web Interface**: User-friendly drag-and-drop interface

## Models

The system uses two pre-trained Vision Transformer models from Hugging Face:

1. **Video Processing Model**: [`mata01/crime-20frame-detection-vit-model`](https://huggingface.co/mata01/crime-20frame-detection-vit-model)
   - Processes chunks of 20 frames for temporal analysis
   - Detects criminal activities across video sequences

2. **Image Processing Model**: [`mata01/crime_action_cctv_image_detection`](https://huggingface.co/mata01/crime_action_cctv_image_detection)
   - Analyzes single images
   - Detects criminal activities in static frames

## Installation

1. Clone this repository
2. Install required dependencies:
   ```
   pip install transformers torch torchvision opencv-python pillow tqdm
   ```
3. Set up your Hugging Face token

## Usage

### Using the Web Interface

1. Run the server notebook:
   ```
   jupyter notebook Sever.ipynb
   ```
2. Open `index.html` in your browser
3. Choose between image or video processing
4. Upload your file or use drag-and-drop
5. View the results with detected crime labels

### Using the Notebooks Directly

#### For Video Processing:
```python
# Initialize processor
processor = VideoProcessor()

# Process a video file
input_video_path = 'path/to/your/video.mp4'
output_video_path = 'path/to/output/video.mp4'
processor.process_video(input_video_path, output_video_path)
```

#### For Image Processing:
```python
# Load models
model_img, processor_img = loadimgprocessor()

# Process an image
predict_image('path/to/your/image.jpg')
```

## Workflow

For a detailed workflow diagram, please visit our [Project Workflow Sheet](https://docs.google.com/spreadsheets/d/your-sheet-id).

The workflow includes:
1. **Input Stage**: Video/Image upload
2. **Pre-processing**: Frame extraction, resizing
3. **Model Inference**: ViT model processing
4. **Post-processing**: Label application and visualization
5. **Output Generation**: Labeled video/image output

## Technical Details

### Supported Crime Categories

The system can detect 14 different actions:
- Abuse
- Arrest
- Arson
- Assault
- Burglary
- Explosion
- Fighting
- Normal (No crime)
- Road Accident
- Robbery
- Shooting
- Shoplifting
- Stealing
- Vandalism

### Video Processing Pipeline

Video processing is done in the [`VideoProcessor`](c:\Users\pvmkt\OneDrive\Desktop\CrimeDetectionusingViTwith20framesinput\Sever.ipynb#L46) class, which:
1. Extracts frames from video input
2. Groups frames into chunks of 20
3. Processes each chunk through the ViT model
4. Aggregates predictions and confidence scores
5. Renders an output video with labels

### Image Processing Pipeline

Image processing is handled by the [`predict_image`](c:\Users\pvmkt\OneDrive\Desktop\CrimeDetectionusingViTwith20framesinput\Sever.ipynb#L252) function, which:
1. Loads and preprocesses the image
2. Passes it through the ViT model
3. Retrieves prediction and confidence score
4. Renders the labeled output image

## License

This project is licensed under the MIT License - see the LICENSE file for details.
