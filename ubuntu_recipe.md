# **Ubuntu, CUDA, VSCode recipe**

## **Install Ubuntu 22.04**
During installation, choose *Minimal installation* and *Install third-party software for graphics and Wi-Fi hardware and additional media formats*.

After installation, in application *Additional Drivers*, choose a Nvidia proprietary driver (not open kernel).

## **Remote connection**

To be able to connect to the machine using **ssh**, install openssh-server

```
sudo apt install openssh-server
```
Enable ssh service
```
sudo systemctl enable ssh
```
Start ssh service
```
sudo systemctl start ssh
```
To login from another computer (on the same network)
```
ssh username@hostname.local
```

Top be able to remote control the machine with **RDP** (Remote Desktop), open *Settings*->*Sharing* and then *Screen sharing*. Enable *Remote Desktop* **and** *Remote Control*. To be able to use this, you must first login to the desktop environment on the server, then connect to the server with a RDP client.

## **Python environment**

Install **pyenv**, a tool that can install multiple Python version and quickly let you switch between them.

Install pyenv build dependencies
```
sudo apt-get update; sudo apt-get install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```
```
curl https://pyenv.run | bash
```
Add these lines to **~/.bashrc**
```
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```
Restart the shell
```
exec $SHELL
```

To install specific Python version
```
pyenv install 3.10.6
```
Set version as global default
```
pyenv global 3.10.6
```

I use **venv** to create virtual environments. To set up a virtual environment inside a folder, just run
```
python venv name-of-virtual-environment
```
Then activate the environment
```
source name-of-virtual-environment/bin/activate
```

## **VSCode with SSH**
Install **VSCode**
```
sudo snap install code
```
On local computer/client: Open **VSCode**, open command palette (Command+Shift+P on Mac or Ctrl+Shift+P on Windows), type `Remote-SSH: Connect to host` and
connect with `username@hostname.local` and enter your password.

To be able to reconnect to a broken SSH-pipe, use **tmux**. 

On remote machine
```
sudo apt install tmux
```

When logged in to remote VSCode, open *Settings->Features->Terminal* and go to *Terminal>Integrated>Automation Shell: [OPERATING SYSTEM]* and <u>Edit in settings.json</u>

Add the follwing rows at the end of the settigns dict
```
    "terminal.integrated.shell.linux": "/usr/bin/tmux",
    "terminal.integrated.shellArgs.linux": [
        "new-session",
        "-A",
        "-s",
        "main"
    ],
```
Save and restart VSCode

Source: https://12ft.io/proxy?&q=https%3A%2F%2Fcppdev.medium.com%2Fvs-code-and-tmux-intergation-for-reliable-remote-development-e26594e6757a

## **Torch with Cuda**
To install **PyTorch** with CUDA support, just let pip install it as usual
```
pip install torch torchvision
```
Verify the install with the following
```
$ python
>>>import torch
>>>torch.cuda.is_available()
True
```

## **CPU and GPU monitor**
```
sudo apt install nvtop htop
```
Run `htop` or `nvtop` in terminal to view load, memory usage and temperatures.