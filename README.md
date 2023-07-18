# Arduino TensorFlow Lite micro-speech project

TODO: desc

# Project setup

On Windows
```
cd %USERPROFILE%\Documents\Arduino\Libraries
git clone https://github.com/tensorflow/tflite-micro-arduino-examples Arduino_TensorFlowLite
cd Arduino_TensorFlowLite
rmdir docs
rmdir .git
rmdir .github
xcopy examples examples.bak /e /i /h
```

Open project in Arduino: `File -> Examples -> Arduino_TensorFlowLite -> micro_speech`

Config git
```
git config --global user.name "wojtekgoo"
git config --global user.email .....@....
```

Create local repo
```
git init
git add .
(git rm nazwa_pliku .)
git commit -m "Initial commit"
git status
```

Create tflite-micro-speech repo on Github

Add a remote repo
```
git remote add origin https://github.com/wojtekgoo/tflite-micro-speech
(git remote rm origin)
git branch -M main   (if main is default branch, but git keeps committing to master)
git add .
git commit -m "Initial commit"
git push --set-upstream --force origin main
```

Authorize with browser
Make changes
`git push origin`


## Compatibility

This library is designed for the `Arduino Nano 33 BLE Sense` board. The framework
code for running machine learning models should be compatible with most Arm Cortex
M-based boards, such as the `Raspberry Pi Pico`, but the code to access peripherals
like microphones, cameras, and accelerometers is specific to the `Nano 33 BLE Sense`.


# Tensorflow install

## Check versions needed

`https://www.tensorflow.org/install/source#gpu`

## Download Miniconda on WSL
```
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc
```

## Conda 
```
conda create --name tf python=3.8
conda activate tf
conda install -c conda-forge cudatoolkit=11.8.0
pip install nvidia-cudnn-cu11==8.6.0.163
```

## Paths

```
CUDNN_PATH=$(dirname $(python -c "import nvidia.cudnn;print(nvidia.cudnn.__file__)"))
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/:$CUDNN_PATH/lib

mkdir -p $CONDA_PREFIX/etc/conda/activate.d
echo 'CUDNN_PATH=$(dirname $(python -c "import nvidia.cudnn;print(nvidia.cudnn.__file__)"))' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/:$CUDNN_PATH/lib' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
```

## Install TF with pip (inside conda environment)
pip install --upgrade pip
pip install tensorflow==2.12.*
python3 -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"

## Jupyterlab

```
pip install jupyterlab ipykernel
ipython kernel install --user --name=tf		// add tf kernel to Jupyter

import tensorflow as tf 
len(tf.config.list_physical_devices('GPU'))
```

## Error while running train.py script
Could not load library libcudnn_cnn_infer.so.8. Error: libcuda.so: cannot open shared object file: No such file or di># https://discuss.pytorch.org/t/libcudnn-cnn-infer-so-8-library-can-not-found/164661/1
`export LD_LIBRARY_PATH=/usr/lib/wsl/lib:$LD_LIBRARY_PATH`