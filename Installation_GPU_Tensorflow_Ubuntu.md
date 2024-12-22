# Installation_GPU_Tensorflow_Ubuntu22.04

## Prerequest
Please make sure the hardware and software version compatability.
- GPU Compute Capability:  https://developer.nvidia.com/cuda-gpus
- Tensorflow version: [https://www.tensorflow.org/install/source_windows](https://www.tensorflow.org/install/source).
- Software requirements: [https://www.tensorflow.org/install/pip](https://www.tensorflow.org/install/pip).
- CUDA toolkit: [https://developer.nvidia.com/cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive)

Software requirements

    Python 3.9–3.12
    pip version 19.0 or higher for Linux (requires manylinux2014 support) and Windows. pip version 20.3 or higher for macOS.
    Windows Native Requires Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017 and 2019

The following NVIDIA® software are only required for GPU support.

    NVIDIA® GPU drivers
        >= 525.60.13 for Linux
        >= 528.33 for WSL on Windows
    CUDA® Toolkit 12.3.
    cuDNN SDK 8.9.7.
    (Optional) TensorRT to improve latency and throughput for inference.


  ```
   For my case I have NVidia 4060 Ti Super and install tensorflow under Ubuntu 22.04 with 
   CUDA 12.4 , cuDNN 9, Python 3.12, tensorflow-2.18.0
  ```


## Steps for GPU installation 
These steps are based on instruction in https://www.tensorflow.org/install/pip
1. After instaling Ubuntu 22.04, please check if your computer already detected your GPU driver. You can use the following command to verify it is installed.
   ```
   nvidia-smi
   ```
Install the [NVIDIA GPU](https://www.nvidia.com/en-us/drivers/) driver if you have not.

2. Install  CUDA Toolkit
   [https://developer.nvidia.com/cuda-12-4-1-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local](https://developer.nvidia.com/cuda-12-4-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local)
   foloow the instruction for Base Installer and Driver Installer

3. Install anaconda dan create environment tf
   Create a virtual environment with venv
   The venv module is part of Python’s standard library and is the officially recommended way to create virtual environments.
   Navigate to your desired virtual environments directory and create a new venv environment named tf with the following command.
   ```
   python3 -m venv tf
   ```
   You can activate it with the following command.
   ```
   source tf/bin/activate
   ```
Make sure that the virtual environment is activated for the rest of the installation.

4. Install TensorFlow
   TensorFlow requires a recent version of pip, so upgrade your pip installation to be sure you're running the latest version.
   ```
   pip install --upgrade pip
   ```
   Then, install TensorFlow with pip.
   ```
   # For GPU users
   pip install tensorflow[and-cuda]
   # For CPU users
   pip install tensorflow
   ```
   **Note:** Do not install TensorFlow with conda. It may not have the latest stable version. `pip` is recommended since TensorFlow is only officially released to PyPI.
  
5. Verify the installation
   Verify the CPU setup:
   ```
   python3 -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
   ```
   If a tensor is returned, you've installed TensorFlow successfully.

   Verify the GPU setup:
   ```
   python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
   ```
   If a list of GPU devices is returned, you've installed TensorFlow successfully. If not continue to the next step.


other python libraries (optional):
```
pip install matplotlib
pip install scikit-learn
pip install pandas
pip install seaborn
pip install opencv-python
```
