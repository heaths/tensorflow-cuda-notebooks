# Notebooks for TensorFlow using CUDA

The [NVIDIA CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit) can be used in [TensorFlow](https://tensorflow.org)
applications for GPU-accelerated machine learning. Getting it set up correctly can be a bit difficult, however.

The [install instructions](https://tensorflow.org/install/gpu) at the time of this writing specifically state that the
following software must be installed:

* [NVIDIA GPU Drivers](https://www.nvidia.com/drivers) - CUDA 10.1 requires *418.x or higher*.
* [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit-archive) - TensorFlow supports 10.1 (TensorFlow >= 2.1.0)
* [CUPTI](http://docs.nvidia.com/cuda/cupti/) ships with the CUDA Toolkit.
* [cuDNN SDK](https://developer.nvidia.com/cudnn) (>= 7.6)

Unlike a lot of software, unless stated explicitly above, "or newer" should not be assumed. With our NVIDIA 2060 RTX
on Windows 10 build 2004 with TensorFlow 2.2.0, I needed to install exactly:

* [CUDA Toolkit 10.1 update 2](https://developer.nvidia.com/cuda-10.1-download-archive-update2) (Aug 2019)
* [cuDNN v7.6.5 (November 5th, 2019), for CUDA 10.1](https://developer.nvidia.com/rdp/cudnn-download#a-collapse765-101)

After setting up the `PATH` environment variable per instructions, I was able to import TensorFlow without error:

```python
import tensorflow as tf
tf.test.is_gpu_available()
```

## Install

These [Jupyter notebooks](https://jupyter.org/) can be used with machine-wide site-packages, or in a virtual environment
to isolate package versions. Before you get started, be sure to have [Python 3.8 x86-64](https://python.org)
or newer installed, make sure pip is up-to-date, and install virtualenv machine-wide:

```powershell
python -m pip install --upgrade pip
pip install --upgrade virtualenv
```

### Run Jupyter from within a virtual environment

You can install and run Jupyter from within a virtual environment:

1. Create your virtual environment and activate it (PowerShell activation sample):
   ```powershell
   virtualenv .venv
   . .\.venv\Scripts\activate.ps1
   ```

2. Make sure python resolves to the virtual environment, and install required packages (PowerShell sample):
   ```powershell
   (get-command python).Source # should resolve to a directory under .venv
   pip install -r requirements.txt
   ```

3. After packages have finished installing, run Jupyter from within the virtual environment:
   ```powershell
   python -m jupyter notebook --notebook-dir .
   ```

4. When you have finished, you can click **Quit** from within Jupyter, or press `Ctrl+C` in the console you started above.

5. To deactivate the virtual environment and restore global operations, simply type:
   ```powershell
   deactivate
   ```
