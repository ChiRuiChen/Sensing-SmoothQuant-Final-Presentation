# Sensing-SmoothQuant-Final-Presentation

This repository documents the setup and integration process of SmoothQuant, which is used in the final presentation of the NYCU Sensing and Intelligent System course.

## Table of Contents
- [Experiment Environment](#experiment-environment)
- [Setup Instructions](#setup-instructions)
  - [SmoothQuant](#smoothquant)
  - [torch-int](#torch-int)
- [Key Links and Resources](#key-links-and-resources)
- [SmoothQuant Workflow Demo](#smoothquant-workflow-demo)
  
## Experiment Environment
- **Operating System:** Ubuntu 22.04
- **Python Version:** 3.8
- **CUDA Toolkit:** 12.2

## Setup Instructions

### SmoothQuant
Follow the official SmoothQuant setup instructions:
- [SmoothQuant Setup](https://github.com/mit-han-lab/smoothquant)

### torch-int
Follow the official torch-int setup instructions:
- [torch-int Setup](https://github.com/Guangxuan-Xiao/torch-int/tree/main)

Important Modification:

In the `setup.py` file of `torch-int`, change the C++ compiler requirement from C++14 to C++17.


## Key Links and Resources

### CUTLASS Repository
- [NVIDIA CUTLASS](https://github.com/NVIDIA/cutlass)

### torch-int
- [pytorch linear layers](https://github.com/Guangxuan-Xiao/torch-int/blob/main/torch_int/nn/linear.py)
- [CUTCLASS linear layers](https://github.com/Guangxuan-Xiao/torch-int/blob/main/torch_int/kernels/linear.cu)

## SmoothQuant Workflow Demo
### FakeQuant Demo
- This demo does not show the latency improvement of quantization.
- Demonstrates the accuracy preservation of SmoothQuant by comparing the accuracy of the FP16 model and the SmoothQuant W8A8 quantized model. 
- [Notebook](https://github.com/mit-han-lab/smoothquant/blob/main/examples/smoothquant_opt_demo.ipynb)

### Real-INT8 Latency Improvement
Pretrained INT8 Model Demo:
- Real INT8 Demo
- [Notebook](https://github.com/mit-han-lab/smoothquant/blob/main/examples/smoothquant_opt_real_int8_demo.ipynb)
  
### Export Your Own INT8 Model
- Follow the workflow of SmoothQuant:
1. Load a pretrained model in fp16.
2. Load the activation scalings from the calibration result.
3. Apply smoothing.
4. Build an INT8 model.
5. Set the weight by quantizing the smoothed model.
6. Export the INT8 model.
- [Python Code](https://github.com/mit-han-lab/smoothquant/blob/main/examples/export_int8_model.py)
