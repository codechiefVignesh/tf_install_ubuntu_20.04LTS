# tf_install_ubuntu_20.04LTS
> Installing Tensorflow in Ubuntu 20.04 LTS with GPU support
### Summarisation of steps
> 1) Installing CUDA ToolKit 10.1
> 2) Install the cuDNN version compatible with CUDA ToolKit 10.1
> 3) Source Environment Variables
> 4) Downgrade the Numpy and
> 5) Install TensorFlow with GPU support
## 1) Installing CUDA ToolKit 10.1
In Ubuntu 20.04LTS install a proprietary Nvidia Driver from the Additional Drivers software
> Preferred versions are <= 535.x
> Then install the CUDA ToolKit by running the following command

'''bash
$ sudo apt install nvidia-cuda-toolkit
