# AI-Enhanced Video Editing: User-Driven Arbitrary Video-to-Video Style Transfer

This repository contains the implementation of a novel video-to-video style transfer pipeline. The system applies the visual style of one video onto the content of another while maintaining temporal consistency across frames. It integrates **deep learning-based style transfer (Magenta)** with **optical flow estimation (RAFT)**, and includes additional enhancements like denoising, stabilization, and quantitative evaluation metrics (SSIM, TWE).

---

## Features

- Arbitrary Video Style Transfer  
  Transfer artistic styles from a style video to a target video using TensorFlow Hub’s Magenta model.

- Temporal Consistency  
  RAFT optical flow ensures frame-to-frame coherence, reducing flickering artifacts.

- Pre-Processing  
  Includes frame denoising and video stabilization with OpenCV.

- Audio Preservation  
  Extracts and reinserts the original audio track to the final styled output.

- Quantitative Evaluation  
  - **SSIM** (Structural Similarity Index): Measures similarity between original and styled video.  
  - **TWE** (Temporal Warping Error): Estimates temporal smoothness using optical flow.

---

## Installation

Clone the RAFT repository and download pretrained weights:

```bash
git clone https://github.com/princeton-vl/RAFT.git
cd RAFT
bash download_models.sh
