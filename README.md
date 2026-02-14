## Medical Image Analyzer with Anatomical Localization using google/medgemma-1.5-4b-it
A Jupyter-based tool that analyzes medical images using Google's MedGemma model, generating patient-friendly reports and bounding box coordinates for anatomical structures.

## Repository
https://github.com/sufirumii/Medical-Image-Analyzer-with-Anatomical-Localization-using-google-medgemma-1.5-4b-it


## Overview
This project implements Google's medgemma-1.5-4b-it for medical image analysis. The model processes images and returns both text descriptions and spatial coordinates that can be visualized directly on the image. The tool is designed to run locally on GPU hardware and provides immediate visual feedback.

## Features
Loads and runs google/medgemma-1.5-4b-it locally

Processes medical images including MRI, CT, X-ray, and pathology slides

Generates severity assessment (urgent, concerning, normal)

Produces plain language explanations of findings

Extracts bounding box coordinates for anatomical structures

Visualizes bounding boxes directly on the original image

Displays side-by-side comparison of original and annotated images

Saves analysis results with timestamps and report IDs

## Hardware Requirements
The model was tested on an RTX 6000 ADA with 48GB VRAM. Inference takes approximately 45 seconds per image. Lower specifications may work but performance will vary.

## Installation
bash
git clone https://github.com/sufirumii/Medical-Image-Analyzer-with-Anatomical-Localization-using-google-medgemma-1.5-4b-it.git
cd Medical-Image-Analyzer-with-Anatomical-Localization-using-google-medgemma-1.5-4b-it
pip install transformers torch pillow requests ipython
Usage
python
from your_script import analyze_with_bbox

# Analyze a local image
result, boxes, labels = analyze_with_bbox(image_path="your_medical_image.jpg")

# The function displays:
# - Original image
# - Image with bounding boxes overlaid
# - Severity assessment
# - Full text analysis
# - List of detected structures with coordinates

## How It Works
The model is prompted with a structured request that asks for bounding box coordinates in normalized format [x1,y1,x2,y2] where values range from 0 to 1000. The system parses these coordinates from the model output and scales them to match the original image dimensions.

The prompt explicitly requests the model to identify and localize anatomical structures including:

Brain structures (hemispheres, ventricles, cerebellum, brainstem)

Thoracic structures (heart, lungs, diaphragm)

Skeletal structures (spine, ribs)

Any visible abnormalities or masses

Output Format
The tool generates an HTML report containing:

The original medical image

The same image with bounding boxes drawn

Color-coded severity assessment

Full text analysis from the model

A table of detected structures with their coordinates

Timestamp and report ID for reference

## Limitations
The model sometimes generates duplicate bounding boxes for the same structure. Some anatomical boundaries may not be precisely captured. The zero-shot performance is reasonable but fine-tuning on specific datasets would improve localization accuracy. The model may also produce full-image boxes that need to be filtered out.

## Model Information
google/medgemma-1.5-4b-it is a 4 billion parameter vision-language model built on the Gemma 3 architecture. It is designed for medical applications and supports multiple domains including radiology, pathology, dermatology, ophthalmology, and clinical document understanding.

## Disclaimer
This tool is for research and informational purposes only. It is not a substitute for professional medical advice, diagnosis, or treatment. Always consult qualified healthcare providers for medical decisions.

## License
This project uses google/medgemma-1.5-4b-it which is subject to Google's Health AI Developer Foundations terms of use. Please review these terms before using the model commercially.

## Contributing
Contributions are welcome. Please open an issue first to discuss proposed changes.

## Contact
For questions or feedback, please open an issue on the GitHub repository.
