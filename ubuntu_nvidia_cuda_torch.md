# Headless Ubuntu 22.04 with CUDA

### **Nvidia headless driver server**
```
$ sudo apt install nvidia-headless-525-server nvidia-utils-525-server
```
Source: https://linuxhint.com/install-nvidia-gpu-drivers-headless-ubuntu-server-22-04-lts/


### **Pyenv**
Run the following
```
curl https://pyenv.run | bash
```
This should be in ~/.bashrc
```
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```
Restart shell
```
exec $SHELL
```
Source: https://kfields.me/blog/pyenv_on_ubuntu_22


### **PyTorch, CUDA, cuDNN ...**
```
pip install torch
```

"Yes, you just need to install the NVIDIA drivers and the binaries will come with the other libs.
If you want to build from source, you would need to install CUDA, cuDNN etc."

Source: https://discuss.pytorch.org/t/how-to-check-if-torch-uses-cudnn/21933/3


### **GPU monitor**
```
sudo apt install nvtop
```