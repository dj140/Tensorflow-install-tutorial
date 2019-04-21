# Tensorflow

## Install Tensorflow GPU
	
	Frist you need an NVIDIA GPU with a compute capability > 3.0.
	
	There are threes major steps that need to be taken, in order for all of this to work.

## 第一步：在英伟达官网下载适合你电脑的显卡驱动

	https://www.nvidia.com/Download/index.aspx?lang=en-us

选择.run文件下载，下载好后执行下面指令给文件权限

	sudo chmod +x xxx.run

接下来按键盘的ctrl + alt + F1进入终端界面，在终端界面输入下面指令关闭x server
	
	sudo server lightdm stop
	sudo ./xxx.run –no-x-check –no-nouveau-check –no-opengl-files

## Install CUDA Toolkit 
## 第二步：下载CUDA Toolkit

选择合适自己系统的安装包，建议选择.run文件下载

	https://developer.nvidia.com/cuda-downloads

下载好后，赋予文件权限，执行安装，所有参数保持默认，除了驱动不需要安装，一定不要选择安装驱动
	
	sudo chmod +x xxx.run
	sudo ./xxx.run

## 第三步：下载cuDD

Download cuDNN 4.0, adding it's contents to your CUDA director <br>
需要注册一个帐号才可以下载,需要下载runtime和develop两个deb文件

	https://developer.nvidia.com/cudnn
	sudo dpkg -i libcudnn7*.deb

## 最后一步Install GPU TensorFlow

	sudo pip3 install tensorflow-gpu

##验证安装

	python3
	import tensorflow as tf
	tf.__version__

## 没有英伟达GPU的可以安装CPU版

	sudo pip3 install tensorflow

## 其他的python依赖包

	pip install pillow
	pip install lxml
	pip install jupyter
	pip install matplotlib

## 下载tensorflow模型

	git clone https://github.com/tensorflow/models.git

## 添加环境变量（注意当重启或关闭终端时需要重新添加）

	protoc object_detection/protos/*.proto --python_out=.
	export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim

If you get an error on the protoc command on Ubuntu, check the version you are running with protoc --version, <br>
if it's not the latest version, you might want to update. As of my writing of this, we're using 3.4.0. <br>
In order to update or get protoc, head to the protoc releases page. Download the python version, extract, <br>
navigate into the directory and then do: <br>

	sudo ./configure
	sudo make check
	sudo make install





