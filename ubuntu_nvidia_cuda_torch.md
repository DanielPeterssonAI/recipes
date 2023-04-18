# Headless Ubuntu 22.04 with CUDA

## Nvidia headless driver server
<code>$ sudo apt install nvidia-headless-525-server nvidia-utils-525-server
</code>

From: https://linuxhint.com/install-nvidia-gpu-drivers-headless-ubuntu-server-22-04-lts/


## torch, cuda, cudnn ...
<code>pip install torch</code>

"Yes, you just need to install the NVIDIA drivers and the binaries will come with the other libs.
If you want to build from source, you would need to install CUDA, cuDNN etc."

From: https://discuss.pytorch.org/t/how-to-check-if-torch-uses-cudnn/21933/3


## GPU monitor
<code>sudo apt install nvtop</code>