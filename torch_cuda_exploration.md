# Exploration of PyTorch with CUDA...

### **TensorRT**
https://medium.com/pytorch/accelerating-pytorch-inference-with-torch-tensorrt-on-gpus-896e06ff1637

3-4x performance boost on CUDA-GPU:s

### **Optimize PyTorch for speed and memory efficiency**
Very good and straight forward: https://huggingface.co/docs/diffusers/v0.7.0/en/optimization/fp16

https://pytorch.org/tutorials/recipes/recipes/tuning_guide.html

https://towardsdatascience.com/optimize-pytorch-performance-for-speed-and-memory-efficiency-2022-84f453916ea6

https://towardsdatascience.com/7-tips-for-squeezing-maximum-performance-from-pytorch-ca4a40951259

### **NHWC (channels_last)**

Changing ton channels last in a CNN saves about 1/3 of the computation time.
```
# Converting existing model
model = model.to(memory_format=torch.channels_last)

# Need to be done for every input
input = input.to(memory_format=torch.channels_last)
output = model(input)
```

If training with channels_last, maybe 
```
x = x.to(memory_format = torch.channels_last)
```
would be desirable to have in the beginning of the forward method

### **Monitor GPU directly in python**
```
pip install nvidia-ml-py3
```
### **torch GradScaler()**
https://wandb.ai/wandb_fc/tips/reports/How-To-Use-GradScaler-in-PyTorch--VmlldzoyMTY5MDA5

Also with an interesting Twitter post

### **Disable GUI in Ubuntu**
https://linuxconfig.org/how-to-disable-enable-gui-in-ubuntu-22-04-jammy-jellyfish-linux-desktop
