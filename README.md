# Case Study Documentation

## Overview

This case study details a ComfyUI workflow for transforming images into Van Gogh style paintings using Stable Diffusion and ControlNet.

## Table of Contents

1. [Introduction](#introduction)
2. [Requirements](#requirements)
3. [Setup](#setup)
4. [Usage](#usage)
5. [Workflow Explanation](#workflow-explanation)
6. [Results](#results)

## Introduction

This workflow aims to transform input images into Van Gogh style paintings using a combination of ControlNets and Stable Diffusion within ComfyUI. The workflow utilizes different types of preprocessors and ControlNets to achieve the desired effect.

## Requirements

- Python 3.x
- ComfyUI
- ControlNet models
- Stable Diffusion models

## Setup

After setting up ComfyUI on your machine, the .json file can be easily loaded into ComfyUI. I highly recommend to install ComfyUI Manager, as it is essential for using ComfyUI and allows for easy access to custom nodes. You can install the custom nodes I used from there without needing any manual downloads.

I utilized Stable Diffusion v1.5 and suitable ControlNets with different attributes. You can obtain the necessary files from the URLs below:

- [Stable Diffusion v1.5](https://huggingface.co/runwayml/stable-diffusion-v1-5)
- [ControlNet Models](https://huggingface.co/lllyasviel)

Once these steps are completed, you are ready to use the workflow.

## Usage

You can upload your images using the "Load Image" node and then press "Queue Prompt." You can expect your output image in Van Gogh style to appear at the "Save Image" node.

## Workflow Explanation

ControlNets allow us to condition diffusion models in specific ways. In this case, I used various preprocessors to extract information from the input image and use it for conditioning. Prompt conditions were used to apply Van Gogh style conditioning.

### Preprocessors

I experimented with different types of preprocessors and their combinations. The final result includes a lineart preprocessor and a segmentation preprocessor. This combination allowed the model to understand the segments of the image and apply clear lines for brush strokes. I also tried depth and pose preprocessors, but they tended to overcomplicate the output. Therefore, I chose to use the anime lineart preprocessor and segmentation preprocessor, which I found suitable based on my experiments.

### Prompt and CFG

I experimented with various prompts to see their impact on the output image and how closely I could achieve a Van Gogh style with descriptive adjectives. Although the prompt influenced the result, the impact was not significant. Therefore, I increased the CFG value on the K Sampler to make my conditioning stronger. CFG (Classifier Free Guidance) determines how closely the output fits to positive conditioning and differs from negative conditioning. Increasing the CFG to 12 significantly improved the results, achieving the desired effect.

## Results
Here is some output examples with their original images:
![me](https://github.com/user-attachments/assets/3c146cb6-6368-4621-ab55-fbd217895a42)
![ComfyUI_00076_](https://github.com/user-attachments/assets/33cfa5e3-0cf1-4461-9933-dc932d007a00)
![me2](https://github.com/user-attachments/assets/7d2cef6f-aa29-43cb-8dfd-4dcc8dec234f)
![ComfyUI_00086_](https://github.com/user-attachments/assets/de9cac88-e80c-4c3d-a10e-4865d604486c)
![train](https://github.com/user-attachments/assets/60a82387-befc-4e36-800b-7e72e1083213)
![ComfyUI_00097_](https://github.com/user-attachments/assets/14d58acf-c589-4fa0-8444-ae58c1f0dbab)
![view](https://github.com/user-attachments/assets/ba580ae6-f1b4-498a-b91f-1a7e3b3e5794)
![ComfyUI_00102_](https://github.com/user-attachments/assets/7a748834-eb0d-43c4-bfc6-04d1b5fe311a)

