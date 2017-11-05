# Machine Learning: Setting up your environment
## Introduction
This tutorial walks you through the steps of setting up you development environment  so you can run machine learning computaitons with TensorFlow and Keras.

To do this we will be using Python3 Virualenv ([recommended](https://www.tensorflow.org/install/install_mac#determine_how_to_install_tensorflow)). If you wish to use Docker, you can find the instructions [here](https://www.tensorflow.org/install/install_mac#installing_with_docker). Just make sure the dependencies below are installed.

Time to Complete: 30 minutes

## Things to Install
Below is a list of things that will be installed in this tutorial. 
- Python ([Download Python | Python.org](https://www.python.org/downloads/))
- Tensorflow (https://www.tensorflow.org/install/)
- Keras (https://keras.io/#installation)
- Scipy (https://scipy.org/install.html)
- Pillow (https://pillow.readthedocs.io/en/4.2.x/installation.html)
- Homebrew ([Homebrew — The missing package manager for macOS](https://brew.sh/))

### Install Python3
You will need to have `python3` installed. Skip this section if its already installed. 
```
$ which python3
/Library/Frameworks/Python.framework/Versions/3.6/bin/python3
```

 You can download the installer directly from Python.org or install using [brew](https://brew.sh/). I would recommend using brew, it tends to set the pathing correctly. If you run intro problems with your brew installation you can always uninstall `brew uninstall python3` and try the [pkg installer](https://www.python.org/downloads/). 

1. Install/Update Xcode
2. Install Command Line Tools for Xcode.
```
$ xcode-select --install
```

3. Install Homebrew
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

4. Install Python3 with Homebrew
```
$ brew update
$ brew install python3
```

5. Verify your installation
```
$ which python3
/Library/Frameworks/Python.framework/Versions/3.6/bin/python3
```

6. Verify your python3 path was set correctly.
```
$ echo $PATH
/Library/Frameworks/Python.framework/Versions/2.7/bin:/Library/Frameworks/Python.framework/Versions/3.6/bin #a bunch of other stuff...
```

and
```
$ python3
Python 3.6.3 (v3.6.3:2c5fed86e0, Oct  3 2017, 00:32:08)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
# Use quit() or Ctrl-D (i.e. EOF) to exit
```

This will also install `pip3` , Python3’s package installer. 

### Install Virualenv
[Virtualenv](https://virtualenv.pypa.io/en/stable/)  is a sandboxed Python environment that has its own installation directories, that don’t share libraries with other `virtualenv` environments.

1. Install `virtualenv` with `pip3`
```
$ pip3 install --upgrade virtualenv
```

2. Make a target directory for your `virtualenv`. 
This is where we will install `tensorflow` later. You can put this anywhere, just make sure you update the target directory in the following commands.
```
$ mkdir -p ~/Documents/Python/texture-synthesis # env target directory
```

3. Create a `virtualenv` environment.
```
$ virtualenv --system-site-packages -p python3 ~/Documents/Python/texture-synthesis # env target directory
```

4. Activate the `virtualenv` environment
```
$ source ~/Documents/Python/texture-synthesis/bin/activate
```

You should now see:
```
(texture-synthesis)$
# Deactivate (texture-synthesis)$ deactivate
```

Use `(texture-synthesis)$ deactivate` to deactivate the environment. We want to keep using our `virtualenv` so don’t do this until we are all done. 

### Install TensorFlow
[Installing TensorFlow on macOS  |  TensorFlow](https://www.tensorflow.org/install/install_mac)

1. Install `tensorflow` with `pip3`
```
(texture-synthesis)$ pip3 install --upgrade tensorflow
```

2. Validate installation and run a short TensorFlow program.
```
(texture-synthesis)$ python3
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
b'Hello, TensorFlow!'
# Use quit() or Ctrl-D (i.e. EOF) to exit
```

### Install Keras
Keras is a high-level neural networks API, written in Python and capable of running on top of TensorFlow. [Keras Documentation](https://keras.io/#installation)
```
(texture-synthesis)$ pip install keras
```

### Install Scipy
SciPy is a Python-based ecosystem of open-source software for mathematics, science, and engineering. In particular, these are some of the core packages: [Installing packages — SciPy.org](https://scipy.org/install.html)
```
(texture-synthesis)$ pip3 install --user numpy scipy matplotlib ipython jupyter pandas sympy nose
```

### Install Pillow
Pillow is a Python Imaging Library [Installation — Pillow (PIL Fork) 4.2.1 documentation](https://pillow.readthedocs.io/en/4.2.x/installation.html)
```
(texture-synthesis)$ pip3 install Pillow
```

## Floyd  Hub
[FloydHub](https://www.floydhub.com/) allows us to run our computations "in the cloud" on their GPUs. You don't strictly need to use them, but if you don't have a good GPU this work will be *much* slower.

Signing up comes with 2 free hours of GPU time which should be sufficient for our purposes. To add more time: Profile (top right icon) -> Usage -> GPU -> Get more hours. ($7/10hrs., $33/50hrs., $59/100 hrs.)

1. [Sign up](https://www.floydhub.com/) for FloydHub. 
2. Install FloydHub cli
```
pip3 install -U floyd-cli
```

3. Login to FloydHub
```
$ floyd login
Please copy and paste the authentication token.
This is an invisible field. Paste token and press ENTER:
Login Successful as brendann.
```

Great now we can run our ml computations a lot faster!