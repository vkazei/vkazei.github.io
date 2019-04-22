# Install cuda and tensorflow-gpu 

tags:
  - Tensorflow
  - Keras
  - GPU
  - Anaconda


## Install Nvidia driver
find the latest driver for your gpu   
--no-x-check can sometimes help you to succeed  
## Install Cuda
don't let it install the driver  
don't install cuda 10.1 -- it is NOT supported by tensorflow  
## Install Anaconda

## Install tensorflow
```
conda create -n tfk python=3.6 pip spyder  
conda install -n tfk tensorflow-gpu  
```
python 3.7 is not supported  
check tensorflow  
```
python  
import tensorflow as tf  
```

## Install keras
```
conda install -n tfk -c conda-forge keras-gpu
```

Use it

```
source activate tfk
spyder . &
```

(c) Vladimir Kazei, Oleg Ovcharenko, KAUST 10-Apr-2019
