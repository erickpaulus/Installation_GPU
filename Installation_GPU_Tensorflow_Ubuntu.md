# Installation_GPU_Tensorflow_Ubuntu22.04

Steps for GPU installation :
1. please make sure the  version compatability.
choose the relevan version https://www.tensorflow.org/install/source_windows, for my case I will install tensorflow-gpu under Windows OS 

CUDA 11.2 , cuDNN 8.1, Python 3.8, tensorflow_gpu-2.10.0

2. download and install
download  CUDA via the official website  https://developer.nvidia.com/cuda-11.0-download-archive
install CUDA and follow the instruction

download cuDNN via the official website https://developer.nvidia.com/cudnn
create account first to get access to download page
Download cuDNN v8.9.3 (July 11th, 2023), for CUDA 11.x
choose the dowloaded file according your OS.  Local Installer for Windows (Zip)
unzip cudnn-windows-x86_64-8.9.3.28_cuda11-archive.zip, then copy and paste to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0

or you can follow this guideline
https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#install-zlib-windows

3. Install anaconda dan create environment py38
Use anaconda to manage python library
create environtment using conda , follow this instruction https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html
conda create -n py38 python=3.8
pip install keras
pip install tensorflow-gpu==2.10.0

4. Troubleshooting
if you have an issue with "cusolver64_11.dll not found", then the solution
1. Move to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\bin
2. Rename file cusolver64_10.dll  To  cusolver64_11.dll 
it works for me

if you have an issue with ZLIB or zlibwapi.dll
Save zlibwapi.dll, follow this instruction
https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#install-zlib-windows
save as link ZLIB DLL
unzip zlib123dllx64.zip. then copy all files in ..\zlib123dllx64\dll_x64 to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\bin

other python libraries (optional):
```
pip install matplotlib
pip install scikit-learn
pip install pandas
pip install seaborn
pip install opencv-python
```
