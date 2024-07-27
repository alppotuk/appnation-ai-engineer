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
