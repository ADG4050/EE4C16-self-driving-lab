# EE4C16 - Self Driving Car Lab


## Overview

This lab is based on Udacity's [self driving car
simulator](https://github.com/udacity/self-driving-car-sim), which is a nice
testbed for training autonomous car using Convolutional Neural Networks.

![Simulated Self Driving Car Project Demo](/images/screenshot.jpg)

The simulator, written in Unity, allows you to drive a car around a track and
record a video of the front view of the ride as well as the input commands.

You will upload this training data (the images + the input commands) to the
clusters and train a CNN to predict the steering angle command from the front
view image alone. Thus, the input of your CNN is an image and the output is the
steering angle.

You will then download back the trained model onto your lab machine so that you
can run the car simulation in autonomous mode.

## Preparing your lab machine

1. Download and extract the ZIP of this repo (download link
[here](https://github.com/frcs/EE4C16-self-driving-lab/archive/master.zip)). Rename
this folder `self-driving-lab`.

2. If you are on the CadLab machines, start the anaconda prompt. We recommend to use `Miniconda3 (64 bit)`,

   1. Do not just search for 'Anaconda Prompt'!
   You must find specifically the 'Anaconda 3' (64 bit) version in 'All Programs'.
  
   1. If Miniconda3 (64bit) is not found under `Ananconda Prompt` section, use the `Anaconda 3' (64 bit)` version. 

      ![anaconda](/images/anaconda-start.jpg)

   1. You can also install Miniconda3 in the CAD Lab machines via [official website](https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links), choose `Miniconda3 Windows 64-bit`
   ![image](https://user-images.githubusercontent.com/10833993/202025335-4491d2d1-aaae-4d5d-944e-5c9d87416b9f.png)


3. then in your conda prompt, go to the extracted `self-driving-lab`
directory and then type:

```bash
conda env create -f environment.yml
```

Then activate the environment. On windows you'll do:
```bash
activate 4c16
```

This will take a while, so in the meantime, let's play with the
simulator (see step 4).

4. Download our modified Udacity's self driving car simulator.

On the Lab machines, you will find a copy on `c:\4c16 Car\`. Otherwise you
can download a version for your system here:

*  [win64](https://drive.google.com/file/d/1vs_AbhXxPVL1fjCbRiKItR0U432ANRyh)
*  [linux64](https://drive.google.com/file/d/1ABdmMtDHMl_bRSTyDyH2zqdURkzzl93y)
*  [OSX](https://drive.google.com/open?id=1qqt_Q8pZqQFpvn9xHRMc002ABq-tQQDK)

On OSX, you'll need to follow instructions for how to [open an app from an unidentified developer](https://support.apple.com/en-ie/guide/mac-help/mh40616/mac).


### Local Machine setup 
If you want to install this on your machine, you will need
[miniconda](https://conda.io/miniconda.html) or [anaconda](https://www.continuum.io/downloads) to use the
environment setting, or simply install the depencies with `pip`.
> *NOTE*: If you using Apple M* (M1/M2) PC, you will have to install `tensorflow-macos` and `tensorflow-metal` instead of `tensorflow`.


## Collecting the training data

1. Start up the Udacity self-driving simulator, choose the **lake**
scene (left) and press the Training Mode button.

2. Then press `R key` and select the **data** folder, where your
training images and CSV will be stored.

3. Press R again to start recording and R to stop recording and wait
for the processing of video to complete.

4. You should do around 1 to 5 laps of the lake track.

5. Zip both `driving_log.csv` file and `IMG` directory into a zip file
that you will name `recordings.zip` (do this by selecting these two
items inside the recordings folder and selecting 'create archive',
rather than by right-clicking and compressing the folder from the
parent).  Then upload `recordings.zip` inside the `4c16-labs/data` directory of
your Google Drive.
![image](https://user-images.githubusercontent.com/10833993/202027855-5f5adbee-30a8-47aa-b264-d146e41eca15.png)


6. On the Google Colab/cluster, the cell containing the following line will unzip the file to the runtime:
```python
!unzip -o -qq /content/gdrive/MyDrive/4c16-labs/data/recordings.zip -d /content/recordings
```

## Training your CNN

check the Jupyter notebook for instructions.

## Run in autonomous mode

1. Once you have trained your model and saved the weights in
`model.h5`. Download the weights back to your lab machine in the
`self-driving-lab` directory.

2. Start up the Udacity self-driving simulator, choose the **lake**
(left) scene and press the Autonomous Mode button.

3. In your conda prompt type

```python
python drive.py model.h5
```

and watch.

4. to stop the simulation: close the simulator window. Check in the
prompt window that the outout file `car_positions.npz` has been
saved. Type `ctrl-c`. It may take a while before `ctrl-c` has an
effect.

Check that the output file is in your directory and uplaod
`car_positions.npz` to your `lab-07` folder in the Google Drive and add it to your git for
assessment.

## Links

NVIDIA's paper: [End to End Learning for Self-Driving Cars](http://images.nvidia.com/content/tegra/automotive/images/2016/solutions/pdf/end-to-end-dl-using-px.pdf) for the inspiration and model structure.

[Siraj Raval](https://github.com/llsourcell) & [naokishibuya](https://github.com/naokishibuya)
