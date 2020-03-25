# waymo_viewer
A rosbag recorder for Waymo Open Dataset

https://waymo.com/open/download/

https://docs.google.com/presentation/d/1gb0FWNSM3V5IXGwbaT-Iov2CoLlbsfCW6dLxDC-i0Ac/edit?usp=sharing

## Environment Setup
### Virtualenv
#### Check Version
Python 3.5-3.7
pip 19.0 及更高版本
```xml
$ python3 --version
$ pip3 --version
$ virtualenv --version
```

#### Create Virtual Environment
```xml
$ virtualenv --system-site-packages -p python3 ./WaymoVenv
$ source ./WaymoVenv/bin/activate
(WaymoVenv) $ deactivate
```

### Install Package
* Tensorflow
```xml
(WaymoVenv) $ pip install --upgrade tensorflow
(WaymoVenv) $ python -c "import tensorflow as tf;print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
```
* Other Package
```xml
(WaymoVenv) $ pip install matplotlib
(WaymoVenv) $ pip install pptk
(WaymoVenv) $ pip install pyyaml
(WaymoVenv) $ pip install rospkg
(WaymoVenv) $ pip install transformations
(WaymoVenv) $ pip install opencv-python
```

## Usage of Waymo_Viewer

* Git clone the whole package, including **waymo-od, waymo_viewer**
* waymo_viewer is the main package for rosbag recording

### Record the data from tfrecord to rosbag
* set parameter "lib_path", the path of the waymo-od
* set parameter "folderpath", the folerpath of tfrecord in launch file
* set parameter "bag_path", the path where the bag should be recorded
```xml
(WaymoVenv) $ roslaunch waymo_viewer recorder.launch
```

### View the camera annotation
* subscribe the topic *camera_image* and *camera_label*
* publish the camera image with annotation
* **CvBridge should be run in python2, so don't excute it in virtualenv**
```xml
$ rosrun waymo_viewer cameralabel_visualization.py
```
