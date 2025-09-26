# AI-Enhanced Video Editing: User-Driven Arbitrary Video-to-Video Style Transfer

This repository implements a novel video-to-video style transfer pipeline. The system applies the visual style of one video onto the content of another while preserving temporal consistency across frames. It integrates deep learning-based style transfer (Magenta) with optical flow estimation (RAFT), and includes enhancements such as denoising, stabilization, audio preservation, and quantitative evaluation metrics (SSIM and TWE).

## Features
- Arbitrary video style transfer using TensorFlow Hub’s Magenta model  
- Temporal consistency with RAFT optical flow to reduce flickering artifacts  
- Pre-processing with denoising and video stabilization via OpenCV  
- Audio preservation by extracting and reinserting the original audio track  
- Quantitative evaluation with SSIM (similarity) and TWE (temporal smoothness)  

## Installation
Clone the RAFT repository and download pretrained weights:  
`git clone https://github.com/princeton-vl/RAFT.git`  
`cd RAFT`  
`bash download_models.sh`  

Install the required dependencies:  
`pip install tensorflow==2.15.0`  
`pip install tensorflow_hub`  
`pip install imageio[ffmpeg]`  
`pip install ffmpeg-python`  
`pip install torch torchvision opencv-python numpy matplotlib tqdm Pillow`  

## Usage
1. Mount Google Drive in Colab if working in Google Colab.  
2. Set paths for your input video, style video, output video, and RAFT weights:  
`raw_video_path = "path/to/your/raw_video.mp4"`  
`style_video_path = "path/to/your/style_video.mov"`  
`output_video_path = "styled_output.mp4"`  
`raft_weights_path = "/content/RAFT/models/raft-things.pth"`  
3. Run the processing pipeline:  
`process_video(raw_video_path, style_video_path, output_video_path)`  
The final styled video will be saved to the specified output path with the original audio preserved.  

## Evaluation
To assess the results quantitatively, the repository provides two metrics:  

- Structural Similarity Index (SSIM):  
`pre_style_ssim = calculate_average_ssim(raw_video_path, style_video_path)`  
`post_style_ssim = calculate_average_ssim(output_video_path, style_video_path)`  

- Temporal Warping Error (TWE):  
`twe = compute_TWE(output_video_path)`  

These metrics help measure both visual fidelity and temporal smoothness.  

## Project Structure
- **Denoising**: Removes noise from input and style frames  
- **Stabilization**: Applies affine transformations for smoother input videos  
- **Style Transfer**: Performs arbitrary style transfer with TensorFlow Hub Magenta model  
- **Temporal Consistency**: Ensures coherence across frames using RAFT optical flow  
- **Audio Handling**: Extracts and merges audio tracks with FFmpeg  
- **Evaluation**: Provides SSIM and TWE for quantitative analysis  

## References
- RAFT: Recurrent All-Pairs Field Transforms for Optical Flow → https://github.com/princeton-vl/RAFT  
- Magenta Arbitrary Image Stylization Model → https://tfhub.dev/google/magenta/arbitrary-image-stylization-v1-256/2  
- TensorFlow, PyTorch, OpenCV, FFmpeg  
