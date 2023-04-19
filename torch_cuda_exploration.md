# Exploration of PyTorch with CUDA...

### **TensorRT**
https://medium.com/pytorch/accelerating-pytorch-inference-with-torch-tensorrt-on-gpus-896e06ff1637

3-4x performance boost on CUDA-GPU:s

### **Optimize PyTorch for speed and memory efficiency**
https://towardsdatascience.com/optimize-pytorch-performance-for-speed-and-memory-efficiency-2022-84f453916ea6

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
