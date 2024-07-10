# 1. Install JetPack
https://docs.nvidia.com/jetson/archives/jetpack-archived/jetpack-461/install-jetpack/index.html

`sudo apt update`\
`sudo apt install nvidia-jetpack`\
`sudo apt show nvidia-jetpack`

# 2. Install CUDA Toolkit

## 1. Download CUDA Toolkit
Visit NVIDIA CUDA Toolkit Archive: Go to the NVIDIA CUDA Toolkit Archive and find the CUDA Toolkit version 10.2 that is compatible with ARM64 architecture and specifically mentions support for the Jetson TX2.

Download the Deb (Network) Installer: For ARM64 and Ubuntu 18.04, you typically want the deb (network) installer.

Look for the appropriate version and download cuda-repo-l4t-10-2-local-10.2.89-1_arm64.deb or similar for CUDA 10.2.

## 2. Install CUDA Toolkit
Install Dependencies: Before installing CUDA, ensure you have the necessary dependencies:

```bash
sudo apt-get update
sudo apt-get install build-essential dkms
```


Install CUDA Toolkit:

```bash
sudo apt-get install cuda-toolkit-10-2
```

## 3. Set Environment Variables
Update PATH Variable: Add CUDA to your PATH variable by appending the following lines to your ~/.bashrc file:

```bash
export PATH=/usr/local/cuda-10.2/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-10.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

Reload .bashrc: After editing .bashrc, reload it to apply the changes:

```bash
source ~/.bashrc
```

4. Verify Installation
Check CUDA Version: Verify that CUDA is installed correctly by checking the CUDA version:

```bash
nvcc --version
```

This command should display the version of CUDA installed.

# 3. Rasterio
Step-by-Step Solution
Install GDAL:

On Ubuntu or Debian-based systems:

```bash
sudo apt-get update
sudo apt-get install gdal-bin libgdal-dev
```

Set GDAL_CONFIG Environment Variable:

```bash
export GDAL_CONFIG=/usr/bin/gdal-config
```

Install rasterio:
After ensuring that GDAL is installed and the GDAL_CONFIG environment variable is set, you can try installing rasterio again.

```bash
pip3 install rasterio==1.0.10
```

# 4. Install Tensorrt(TX2)
```bash
sudo apt install nvidia-tensorrt
sudo apt update
sudo apt install libboost-python-dev

 sudo find / -name "libboost_python3-py36.so.1.65.1"
```
```bash
nano ~/.bashrc
```
```bash
export LD_LIBRARY_PATH=/path/to/lib:$LD_LIBRARY_PATH
```
```bash
source ~/.bashrc
````


# 5. Reference

`https://github.com/mailrocketsystems/JetsonYoloV7-TensorRT`

# 6. Version Compatibility
numpy == 1.19.4 (1.19.5 is very bad)
rasterio == 1.0.10


# 7. Testing

For testing the Jetson TX2 environment for my custom model, I need to run
`python3 to_onnx.py`, `python3 to_trt.py`, `python3 inference.py` in `OpenEarthMap`.

`JetsonYoloV7-TensorRT` is sample project on github and you can do some other tests with that.
