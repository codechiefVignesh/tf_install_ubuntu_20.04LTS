# tf_install_ubuntu_20.04LTS
> Installing Tensorflow in Ubuntu 20.04 LTS with GPU support
### Summarisation of steps
> 1) Installing CUDA ToolKit 10.1
> 2) Install the cuDNN version compatible with CUDA ToolKit 10.1
> 3) Source Environment Variables
> 4) Downgrade the Numpy and
> 5) Install TensorFlow with GPU support

# PREREQUISITES
> In Ubuntu 20.04LTS install a proprietary Nvidia Driver from the Additional Drivers software
> Preferred versions are <= 535.x
> OR one can use the traditional method of installation
> Installing nvidia graphics driver

<pre lang = "bash"><code>
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt install nvidia-driver-525 or 535
</code></pre>
>Installing pip
<pre lang = "bash"><code>
$ sudo apt install python3-pip
</code></pre>
## 1) Installing CUDA ToolKit 10.1

> Install the CUDA ToolKit by running the following command

<pre lang = "bash"><code>
$ sudo apt install nvidia-cuda-toolkit
</code></pre>

> Then run this command to verify the installation

<pre lang = "bash"><code>
$ nvcc --version
</code></pre>
> Then follow this link to install the cuDNN compatible with the CUDA ToolKit

## 2) Installing cuDNN
>Click “Download cuDNN v7.6.5 (November 5th, 2019) for CUDA 10.1”, then choose “cuDNN Library for Linux” to download cuDNN 7.6.5 for CUDA 10.1. 
>Follow this link to install : https://developer.nvidia.com/rdp/cudnn-download

> Then run the following commands in the terminal in the folder containing the downloaded file

<pre lang = "bash"><code>
$ tar -xvzf cudnn-10.1-linux-x64-v7.6.5.32.tgz
$ sudo cp cuda/include/cudnn.h /usr/lib/cuda/include/
$ sudo cp cuda/lib64/libcudnn* /usr/lib/cuda/lib64/
$ sudo chmod a+r /usr/lib/cuda/include/cudnn.h /usr/lib/cuda/lib64/libcudnn*
</code></pre>

## 3) Source the environment variables
<pre lang = "bash"><code>
$ echo 'export LD_LIBRARY_PATH=/usr/lib/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
$ echo 'export LD_LIBRARY_PATH=/usr/lib/cuda/include:$LD_LIBRARY_PATH' >> ~/.bashrc
</code></pre>

> Now load the variables sourced
<pre lang = "bash"><code>
$ source ~/.bashrc
</code></pre>

## 4) Downgrade NumPy and Protobuf
> these may be in higher versions than the supported ones for tf and CUDA so downgrading them to the last supported version will be better
<pre lang = "bash"><code>
$ pip install protobuf==3.20.0
</code></pre>
<pre lang = "bash"><code>
$ pip install numpy==1.20.0
</code></pre>

## 5) Installing Tensorflow with GPU support
<pre lang = "bash"><code>
$ pip install tensorflow==2.2.0
</code></pre>
> Then enter python3 in the shell to enter python idle shell.
> Now we will test our installation
<pre lang = "bash"><code>
>>> import tensorflow as tf
>>> tf.config.list_physical_devices("GPU")
[PhysicalDevice(name='/physical_device:GPU:0', device_type='GPU')]
</code></pre>

> These steps will ensure the successful installation of tensorflow in Ubuntu 20.04 with GPU support.
