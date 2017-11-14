# EE4C16 - Self Driving Car Lab

## Overview

This lab is based on Udacity's [self driving car
simulator](https://github.com/udacity/self-driving-car-sim), which is
a nice testbed for training autonomous car using Convolutional Neural
Networks.

![Simulated Self Driving Car Project Demo](/images/screenshot.jpg)

The simulator, written in Unity, allows you to drive a car around a
track and record a video of the front view of the ride as well as the
input commands.

You will upload this training data (the images + the input commands)
to the GCP clusters and train a CNN to predict the steering angle
command given the front view image. Thus the input of your CNN is an
image and the output is the steering angle.

You will then download back the trained model onto your lab machine so
that you can run the car simulation in autonomous mode.

## Preparing your lab machine

1. Download and extract the ZIP of this repo (download link
[here](https://github.com/frcs/EE4C16-self-driving-lab/archive/master.zip))

2. If you are on the Lab machines, start the anaconda prompt

![anaconda](/images/anaconda-start.jpg)

3. then in your conda prompt, go to the extracted directory (let's
call it `self-driving-lab`) and then type:

```bash
conda env create -f environments.yml
```

Then activate the environment. On windows you'll do:
```bash
activate 4c16
```

This will take a while, so in the meantime, go a play with the
simulator (see step 4).

If you want to install this on your machine, you will need
[anaconda](https://www.continuum.io/downloads) or
[miniconda](https://conda.io/miniconda.html) to use the
environment setting. 

4. Download our modified Udacity's self driving car simulator:

On the Lab machines, you will find a copy on `c:\4c16`. Otherwise you
can download a version for your system here:

*  [win64](https://drive.google.com/file/d/1vs_AbhXxPVL1fjCbRiKItR0U432ANRyh)
*  [linux64](https://drive.google.com/file/d/1ABdmMtDHMl_bRSTyDyH2zqdURkzzl93y)
*  [OSX](https://drive.google.com/open?id=1qqt_Q8pZqQFpvn9xHRMc002ABq-tQQDK)


### Collecting the training data

1. Start up the Udacity self-driving simulator, choose the **lake**
scene and press the Training Mode button.

2. Then press `R key` and select the **data** folder, where your
training images and CSV will be stored.

3. Press R again to start recording and R to stop recording. Let the
processing of video complete.

4. You should do around 1 to 5 laps of the lake track.

5. Zip both `driving_log.csv` file and `IMG` directory into a zip file
called `recordings.zip`. Upload `recordings.zip` to the 
`lab-06` directory of your cluster using the Jupyter notebook.

6. On the cluster, these commands in the notebook will unzip the file:
```python
!rm -rf IMG
!unzip -o -qq recordings.zip
driving_log = './driving_log.csv'
```

### Train the data

check the Jupyter notebook for instructions.

### Run in autonomous mode

1. Once you have trained your model and saved the weights in
`model.h5`. Download the weights back to your lab machine in the
`self-driving-lab` directory.

2. Start up the Udacity self-driving simulator, choose the **lake**
(left) scene and press the Autonomous Mode button.

3. In your conda prompt type 

```python
python drive.py model.h5
```

4. When the autonomous ride is over, drive.py will produce a file
called `car_positions.npz`. Upload that file to your cluster and add
it to your git for assessment.


## Links

NVIDIA's paper: [End to End Learning for Self-Driving Cars](http://images.nvidia.com/content/tegra/automotive/images/2016/solutions/pdf/end-to-end-dl-using-px.pdf) for the inspiration and model structure.

[Siraj Raval](https://github.com/llsourcell) & [naokishibuya](https://github.com/naokishibuya)



