---
title: "Install Keras with Tensorflow backend and GPU support in Anaconda"
excerpt: "Step-by-step manual"
tags:
  - Tensorflow
  - Keras
  - GPU
  - Anaconda
---
modified from Oleg Ovcharenko ovharenkoo.com

1. Install Nvidia driver
2. Install Cuda
3. ?Install cuDNN?
4. Install Anaconda
5. Open terminal and type one-by-one the following commands
```
conda create -n tfk python=3.6 pip spyder
conda install -n tfk tensorflow-gpu
conda install -n tfk -c conda-forge keras-gpu
```

Use it

```
source activate tfk
spyder . &
```

Done.
